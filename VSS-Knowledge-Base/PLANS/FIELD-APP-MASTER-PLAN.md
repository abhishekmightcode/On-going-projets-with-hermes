# VSS Field App — Master Implementation Plan
**Status:** ✅ PHASE 1 DEPLOYED
**Project:** VSS (V Sustain Solar Solutions)
**Last Updated:** 2026-05-09

---

## Live App

**URL:** https://abhishekmightcode.github.io/vss-ups-field-app/
**GitHub Repo:** `abhishekmightcode/vss-ups-field-app`
**Latest Commit:** `ecb5edf` (fix: use Zoho record ID as Firebase doc ID everywhere)

---

## Architecture

```
Field Employee (Mobile Browser)
         │
         ▼
┌─────────────────────────────────────────────────────┐
│  VSS Field App (abhishekmightcode.github.io/vss-ups)│
│                                                      │
│  Dealer List → tap dealer → dealer detail screen    │
│              [📍 Send Location] [📝 Submit Info] [📷 Upload Photo] │
└──────────────────────┬───────────────────────────────┘
                      │
        ┌─────────────┼─────────────────┐
        ▼             ▼                 ▼
   GPS coords    In-app web form    Google Form
   Zoho API ─►   Zoho API ────────► Google Drive
   (location     (text fields)      (photo stored)
   fields only)                     Apps Script reads
                                     Drive → URL → Zoho
                                     Dealer Meets sub-form
        │             │                 │
        └─────────────▼─────────────────┘
                      │
               ZOHO CRM (source of truth)
                      │
              Firebase Firestore
              (sync: Zoho → Firebase,
               every 1 hour via cron)
```

---

## Data Model (CRITICAL — Read Before Touching Anything)

### Firebase
- **Collection:** `upsdealers`
- **Doc ID = Zoho Record ID (PRIMARY KEY)** — e.g. `1171062000002901006`
- **`dealer_code` = secondary key (10-digit string)** — stored as field INSIDE doc, e.g. `dealer_code: "1000036809"`
- ** NEVER use `dealer_code` as Firebase doc ID** — that was the old (broken) approach

### Zoho CRM
- **Module:** UPS
- **Record ID = PRIMARY KEY** — numeric ID returned by Zoho on insert (e.g. `1171062000002901006`)
- **`Dealer_code` field** — 10-digit string, secondary business identifier
- **`Phone` field** — must include `+91` prefix

### Rule (always):
```
Firebase doc ID = Zoho record ID (activeDealer.id)
dealer_code = field inside doc (activeDealer.dealer_code)
```

### Firebase Doc Shape
```json
{
  "id": "1171062000002901006",         // same as doc ID = Zoho record ID
  "dealer_code": "1000036809",          // secondary key as field
  "name": "Sri Bhyraveshwara Battery Point",
  "phone": "+919845367915",
  "dealer_type": "Retailer",
  "lat": 12.9716,
  "lng": 77.5946,
  "location_synced": true,
  "visit_count": 3,
  "last_visit_date": "2026-05-09T10:30:00.000Z",
  "last_synced": "<Firestore timestamp>",
  "dealer_meets": [
    {
      "Visit_Number": 3,
      "Visit_Date": "2026-05-09",
      "Visit_Notes": "Customer interested in 3kVA system",
      "submitted_at": "2026-05-09T10:30:00.000Z",
      "record_id": "1171062000002901006"
    }
  ]
}
```

---

## Button 1: Send Location ✅ IMPLEMENTED

**Flow:**
```
Employee taps "Send Location"
  → navigator.geolocation.getCurrentPosition() → lat/lng
  → GET Zoho token via getZohoToken()
  → PUT https://crm.zoho.in/crm/v2/UPS/{activeDealer.id}
      Body: {
        "Address_of_the_dealer_Coordinates_Latitude": "12.9716",
        "Address_of_the_dealer_Coordinates_Longitude": "77.5946"
      }
  → Firebase: UPDATE doc {activeDealer.id} with { lat, lng, location_synced: true }
  → Show toast "📍 Location synced to Zoho CRM ✓"
```

**Key implementation (app.js):**
```javascript
// IMPORTANT: doc ID = Zoho record ID (activeDealer.id), NOT dealer_code
await window.FB.db.collection(CONFIG.FIRESTORE_COLLECTION).doc(activeDealer.id).update({
  lat: pos.lat,
  lng: pos.lng,
  location_synced: true
});
```

**Zoho API call:**
```bash
PUT https://crm.zoho.in/crm/v2/UPS/1171062000002901006
Authorization: Zoho-oauthtoken {token}
Content-Type: application/json
Body: {"data":[{"Address_of_the_dealer_Coordinates_Latitude":"12.9716","Address_of_the_dealer_Coordinates_Longitude":"77.5946"}]}
```

---

## Button 2: Submit Info ✅ IMPLEMENTED (partial — Dealer Meets history not fetched)

**Flow:**
```
Employee taps "Submit Info" → opens in-app form
  → Fills: Dealer Type, Battery Stock, UPS Stock, High KVA UPS Stock,
           Approx Value, Credit Value, Follow-up Date/Time, Follow-up Notes,
           Visit Notes, Competition In Use, Next Follow-up Type
  → Taps "Submit to Zoho CRM"
  → PUT https://crm.zoho.in/crm/v2/UPS/{activeDealer.id} (text fields)
  → POST https://crm.zoho.in/crm/v2/UPS/{activeDealer.id}/Dealer_meets (visit entry)
  → Firebase: UPDATE doc {activeDealer.id} with field updates + dealer_meets array
  → Show toast "✅ Visit #{N} submitted successfully!"
```

**Zoho fields updated (PUT):**
| Form Field | Zoho API Name |
|------------|---------------|
| Dealer Type | `Dealer_Type` |
| Battery Stock | `Existing_Battery_stock` |
| UPS Stock | `Existing_UPS_stock` |
| High KVA UPS Stock | `Existing_High_KV_UPS_stock` |
| Approx Value | `Approx_value_in_outlet` |
| Credit Value | `Credit_value_with_dealer` |
| Follow-up Date/Time | `Follow_up_date_and_time` (ISO string) |
| Follow-up Notes | `Follow_up_notes` |

**Dealer Meets entry (POST to sub-form):**
```json
{
  "Visit_Date": "2026-05-09",
  "Visit_Notes": "Customer interested in 3kVA system",
  "Competition_In_Use": "Luminous",
  "Follow_up_Type": "Visit"
}
```

**Known gap:** The app does NOT yet fetch Dealer Meets history from Zoho on modal open. The "Recent Visits" section shows only locally-submitted visits stored in Firebase `dealer_meets` array.

---

## Button 3: Upload Photo ⚠️ PENDING (Google Form not created)

**User must:**
1. Create Google Form with fields: Record ID (hidden), Dealer Code (hidden), Photo (file upload)
2. Share Form ID and entry IDs with Hermes
3. Hermes will update `config.js` with `GOOGLE_FORM` config and set `enabled: true`

**Flow (planned):**
```
Employee taps "Upload Photo"
  → Opens pre-filled Google Form URL:
    https://docs.google.com/forms/d/{FORM_ID}/viewform?entry.XXXX={record_id}&entry.YYYY={dealer_code}
  → Employee uploads photo and submits
  → Apps Script trigger: form submit → Drive upload → get public URL
  → Apps Script: POST to Zoho Dealer Meets sub-form with Image_URL
  → Firebase: UPDATE doc {record_id} with latest_photo_url
```

---

## Zoho CRM API Reference

**Base:** `https://crm.zoho.in/crm/v2`
**DC:** `.in` (India)
**Module:** UPS

### Update UPS Record (location or text)
```
PUT /crm/v2/UPS/{record_id}
Headers: Authorization: Zoho-oauthtoken {token}, Content-Type: application/json
Body: { "data": [{ "Address_of_the_dealer_Coordinates_Latitude": "12.9716", ... }] }
```

### Create Dealer Meets Entry
```
POST /crm/v2/UPS/{record_id}/Dealer_meets
Body: { "data": [{ "Visit_Date": "2026-05-09", "Visit_Notes": "...", "Image_URL": "https://..." }] }
```

### Get All UPS Records
```
GET /crm/v2/UPS?fields=ALL&per_page=200&page=1
Headers: Authorization: Zoho-oauthtoken {token}
```

### Increment Total Visits
```
PUT /crm/v2/UPS/{record_id}
Body: { "data": [{ "Total_visits": 5 }] }
```

---

## Hourly Sync (Zoho → Firebase)

**Script:** `/home/azureuser/.hermes/scripts/vss_zoho_firebase_sync.py`
**Cron Job ID:** `e7474b1dd47e`
**Schedule:** `0 * * * *` (every hour at minute 0)
**Logic:**
1. Fetch all Zoho UPS records (GET with per_page=200, page=200 max)
2. For each record: `docId = str(record.id)` (Zoho record ID)
3. `batch.set(db.collection('upsdealers').doc(docId), data, {merge: true})`
4. Commit batch

**Note:** Does NOT fetch Dealer Meets sub-form data. Gap to fix.

---

## Bugs Fixed (2026-05-09)

| # | Bug | Symptom | Fix | Commit |
|---|-----|---------|-----|--------|
| 1 | `docRef` undefined | `syncFromZoho()` crashed with `docRef is not defined` | Added `const docRef = window.FB.db.collection(...).doc(docId)` | `ecb5edf` |
| 2 | Wrong doc ID in `sendLocation()` | Firebase update targeted wrong doc (used `dealer_code`) | Changed to `doc(activeDealer.id)` | `ecb5edf` |
| 3 | Wrong doc ID in `submitInfoForm()` | Firebase update targeted wrong doc (used `dealer_code`) | Changed to `doc(activeDealer.id)` | `ecb5edf` |
| 4 | `data.dealer_code = String(code)` | Overwrote mapped `dealer_code` with empty string on every sync | Removed the errant line | `8f266e2` |
| 5 | Firebase collection name | Was `ups_dealers` (underscore) — 404 on REST calls | Changed to `upsdealers` | `8755ea9` |
| 6 | Record ID not shown in modal | Employee couldn't see Zoho record ID to verify | Added `modalRecordId` field with 🔑 icon | `8755ea9` |

---

## Implementation Phases

### ✅ Phase 1 — Core UI + Location + Info Submit (DONE)
- [x] Dealer list with 3 buttons
- [x] Location button: GPS → Zoho API PUT
- [x] Submit Info button: in-app web form → Zoho API PUT + Dealer Meets POST
- [x] On Submit Info: increment `visit_count`, set `last_visit_date`, add to `dealer_meets` array
- [x] Location permission prompt on first load
- [x] Firebase sync (all top-level fields, not sub-forms)

### ⚠️ Phase 2 — Photo Upload (PENDING — needs user action)
- [ ] User creates Google Form (photo upload only)
- [ ] User shares Form ID + entry IDs
- [ ] Hermes updates `config.js` with `GOOGLE_FORM` config
- [ ] Apps Script: form submit → Drive → Zoho Dealer Meets `Image_URL`
- [ ] Upload Photo button opens pre-filled form URL

### 🔜 Phase 3 — Dealer Meets History in App (PENDING)
- [ ] On `openModal()`: fetch Dealer Meets sub-form records from Zoho for that record ID
- [ ] Display visit history in "Recent Visits" section of modal
- [ ] Add photo badge on dealer card when photo exists

### 🔜 Phase 4 — Improved Sync
- [ ] Sync script should also fetch and store Dealer Meets sub-form data
- [ ] Add `last_sync` timestamp to each dealer in Firebase
- [ ] Show "syncing ↻" indicator during background sync

---

## Credentials

| Service | Where Stored |
|---------|-------------|
| Zoho OAuth (client_id, client_secret, refresh_token) | `~/.hermes/zoho_credentials.json` |
| Firebase config | In `index.html` (public, not a secret) |
| Google OAuth token | `~/.hermes/google_token.json` |
| Google client secret | `~/.hermes/google_client_secret.json` |

**Full credentials reference:** `VSS/CREDENTIALS.md`

---

*Last updated: 2026-05-09*