# VSS Field App — Master Implementation Plan
**Status:** ✅ PHASE 1 DEPLOYED
**Project:** VSS (V Sustain Solar Solutions)
**Last Updated:** 2026-05-09

---

## ✅ PHASE 1 COMPLETED — What's Built

The app is LIVE at: **https://abhishekmightcode.github.io/vss-ups-field-app/**

### Architecture
```
Browser → Firebase Firestore (read cache, instant load)
        ↕ (bidirectional sync)
     Zoho CRM (source of truth)

Web App (no Google Forms for text):
  ├── 📍 Send Location → GPS → Zoho CRM (direct API)
  ├── 📝 Submit Info   → In-app web form → Zoho CRM (direct API)
  └── 📷 Upload Photo → Google Form (photo only — setup pending)
```

### Firebase Doc IDs
- **Zoho records**: keyed by Zoho numeric ID (e.g. `1171062000002868005`)
- **Future csv_master dealers**: keyed by CSV dealer code (e.g. `1000036809`)
- **Fix applied 2026-05-09**: Previously both sources used the same numeric IDs causing duplicates. Now separated: Zoho records use their own Zoho IDs, csv_master dealers use their CSV codes.

### Fields Updated by "Submit Info"

---

## Overview

Mobile-first field app for VSS field employees (dealer visits):
- **Firebase** = read cache (dealer list from Zoho CRM)
- **Zoho CRM** = source of truth
- **Web App UI** = all textual data entry (no Google Form for text)
- **Google Form** = photo upload only

**3 Buttons per Dealer:**
1. 📍 **Send Location** — GPS coords → Zoho CRM directly via API
2. 📝 **Submit Info** — custom web app form → Zoho CRM API
3. 📷 **Upload Photo** — Google Form → Google Drive → Zoho CRM (Dealer Meets sub-form)

---

## Architecture

```
Field Employee (Mobile Browser)
         │
         ▼
┌─────────────────────────────────────────────────────────┐
│  VSS Field App (abhishekmightcode.github.io/vss-ups)   │
│                                                          │
│  Dealer List → tap dealer → dealer detail screen        │
│                  [📍 Send Location] [📝 Submit Info] [📷 Upload Photo] │
└──────────────────────────┬──────────────────────────────┘
                           │
         ┌─────────────────┼─────────────────┐
         │                 │                 │
         ▼                 ▼                 ▼
   GPS coords      Custom web form    Google Form
   Zoho API ───►   Zoho API ─────────► Google Drive
   (location       (text fields)      (photo stored)
   fields only)                       Apps Script reads
                                      Drive → URL → Zoho
                                      Dealer Meets sub-form
         │                 │                 │
         └─────────────────▼─────────────────┘
                           │
                    ZOHO CRM (source of truth)
                           │
                    Firebase Firestore
                    (sync: Zoho → Firebase,
                     every 15 min)
```

---

## Phase 1 Buttons

### Button 1: Send Location
```
Click → getCurrentPosition() → lat/lng
  → PUT https://crm.zoho.in/crm/v2/UPS/{id}
       Body: {
         "Address_of_the_dealer_Coordinates_Latitude": lat,
         "Address_of_the_dealer_Coordinates_Longitude": lng
       }
  → Update Firebase doc: location_synced = true, lat, lng
  → Show toast "Location synced ✓"
```

### Button 2: Submit Info (web app custom form)
Opens a built-in form in the app with these fields:

| Field | Type | Zoho API Name |
|---|---|---|
| Dealer Type | Dropdown | `Dealer_Type` |
| Existing Battery Stock | Text | `Existing_Battery_stock` |
| Existing UPS Stock | Text | `Existing_UPS_stock` |
| Existing High KV UPS Stock | Text | `Existing_High_KV_UPS_stock` |
| Approx Value in Outlet | Text | `Approx_value_in_outlet` |
| Credit Value with Dealer | Text | `Credit_value_with_dealer` |
| Follow-up Date & Time | Date + Time | `Follow_up_date_and_time` |
| Follow-up Notes | Textarea | `Follow_up_notes` |
| Visit Notes | Textarea | `Visit_Notes` (→ Dealer Meets sub-form) |
| Competition In Use | Text | `Competition_In_Use` (→ Dealer Meets sub-form) |
| Next Follow-up Type | Dropdown | `Follow_up_Type` (→ Dealer Meets sub-form) |

On Submit → PUT to Zoho UPS module + create Dealer Meets entry via POST

Also:
- Increment `Total_visits` in Zoho
- Set `last_visit_date` = today
- Increment `visit_count` in Firebase
- `last_visit_date` in Firebase = today

### Button 3: Upload Photo (Google Form)
- Open Google Form with Record ID + Dealer Code as pre-filled hidden params
- Employee uploads photo (phone camera or file)
- On submit → Apps Script trigger → upload photo to Google Drive → get public URL
- Apps Script: POST to Zoho CRM Dealer Meets sub-form with Image_URL
- Apps Script: update Firebase doc with photo URL
- Photo appears in app dealer detail view

---

## Google Form: Photo Upload

**Form Name:** VSS — Dealer Visit Photo

**Fields:**
| # | Field | Type |
|---|---|---|
| 1 | Record ID | Short answer (hidden, pre-filled) |
| 2 | Dealer Code | Short answer (hidden, pre-filled) |
| 3 | Photo | File upload |

**Pre-filled URL format:**
```
https://docs.google.com/forms/d/{FORM_ID}/viewform?
  entry.XXXX={record_id}&       ← Record ID
  entry.YYYY={dealer_code}      ← Dealer Code
```

**Apps Script on submit:**
1. Get file upload from form response
2. Upload to Google Drive (specific folder)
3. Get public/shareable URL
4. PUT to Zoho CRM → Dealer Meets sub-form:
   ```
   POST /crm/v2/UPS/{record_id}/Dealer_meets
   {
     "data": [{
       "Visit_Number": <auto-increment>,
       "Visit_Date": "<today>",
       "Image_URL": "<google_drive_url>",
       "Dealer_Code": "<dealer_code>"
     }]
   }
   ```
5. Update Firebase doc with image URL

---

## Zoho CRM API Reference

**Base:** `https://crm.zoho.in/crm/v2`

### Update UPS Record (text fields)
```
PUT /crm/v2/UPS/{record_id}
Headers: Authorization: Zoho-oauthtoken {token}
Body: { "data": [{ "Dealer_Type": "Retailer", "Existing_Battery_stock": "10 units", ... }] }
```

### Update Location (separate call)
```
PUT /crm/v2/UPS/{record_id}
Body: { "data": [{ "Address_of_the_dealer_Coordinates_Latitude": "12.9716", "Address_of_the_dealer_Coordinates_Longitude": "77.5946" }] }
```

### Increment Total Visits
```
PUT /crm/v2/UPS/{record_id}
Body: { "data": [{ "Total_visits": <current + 1> }] }
```

### Create Dealer Meets Entry (sub-form)
```
POST /crm/v2/UPS/{record_id}/Dealer_meets
Body: { "data": [{
  "Visit_Number": 1,
  "Visit_Date": "2026-05-08",
  "Visit_Notes": "Customer interested in 3kVA system",
  "Competition_In_Use": "Luminous",
  "Follow_up_Type": "Call",
  "Image_URL": "https://drive.google.com/..."
}] }
```

### Get All UPS Records (for Firebase sync)
```
GET /crm/v2/UPS?fields=ALL&per_page=200&page=1
Headers: Authorization: Zoho-oauthtoken {token}
```

---

## Firebase Firestore: ups_dealers

Doc ID = `Dealer_Code` (e.g. "UP32-001")

```json
{
  "id": "1171062000002812045",
  "dealer_code": "UP32-001",
  "name": "Sri Bhyraveshwara Battery Point",
  "phone": "919845367915",
  "phone2": "",
  "dealer_type": "Retailer",
  "address": "Shop No. 12, MG Road",
  "city": "Bangalore",
  "state": "Karnataka",
  "lat": 12.9716,
  "lng": 77.5946,
  "location_synced": false,
  "last_visit_date": null,
  "visit_count": 0,
  "last_order_date": null,
  "last_order_value": null,
  "total_lifetime_value": null,
  "follow_up_date_time": null,
  "follow_up_notes": "",
  "existing_battery_stock": "",
  "existing_ups_stock": "",
  "existing_high_kv_ups_stock": "",
  "approx_value_in_outlet": "",
  "credit_value_with_dealer": "",
  "status": "Active",
  "latest_photo_url": "",
  "synced_at": null,
  "zoho_last_modified": null
}
```

---

## Zoho CRM Field Map (Confirmed)

| Firebase Field | Zoho API Name |
|---|---|
| id | id (record ID — use for API calls) |
| dealer_code | Dealer_code (Firebase doc ID) |
| name | Name |
| phone | Phone |
| dealer_type | Dealer_Type |
| location_lat | Address_of_the_dealer_Coordinates_Latitude |
| location_lng | Address_of_the_dealer_Coordinates_Longitude |
| last_order_date | Last_Order_Date |
| last_order_value | Last_Order_Value |
| total_lifetime_value | Total_Lifetime_Value |
| follow_up_date_time | Follow_up_date_and_time |
| follow_up_notes | Follow_up_notes |
| existing_battery_stock | Existing_Battery_stock |
| existing_ups_stock | Existing_UPS_stock |
| existing_high_kv_ups_stock | Existing_High_KV_UPS_stock |
| approx_value_in_outlet | Approx_value_in_outlet |
| credit_value_with_dealer | Credit_value_with_dealer |
| total_visits | Total_visits |
| address | Address_of_the_dealer |
| city | Address_of_the_dealer_City |

**Dealer Meets Sub-form (Photo + Visit notes):**
| Firebase Field | Zoho Sub-form API Name |
|---|---|
| visit_number | Visit_Number |
| visit_date | Visit_Date |
| visit_notes | Visit_Notes |
| competition_in_use | Competition_In_Use |
| next_follow_up_type | Follow_up_Type |
| image_url | Image_URL |

---

## Implementation Phases

### Phase 1 — Core UI (Text + Location)
- [ ] Update VSS app: dealer list with 3 buttons
- [ ] Location button: GPS → Zoho API
- [ ] Submit Info button: custom web form → Zoho API
- [ ] Zoho → Firebase sync script (periodic, 15 min)
- [ ] Location permission on first app open

### Phase 2 — Photo Upload (Google Form)
- [ ] User creates Google Form (photo upload only)
- [ ] User gives Form ID + entry IDs for Record ID + Dealer Code
- [ ] Apps Script: form submit → Drive upload → get URL → Zoho Dealer Meets
- [ ] Upload Photo button opens pre-filled form URL

### Phase 3 — Dealer Meets Sub-form in App
- [ ] App shows visit history per dealer
- [ ] Each visit card shows photo, visit notes, date
- [ ] Visit count badge on dealer card

---

## Google Form Format (for Photo Upload)

**Form Name:** VSS — Dealer Visit Photo

**Pre-filled hidden fields:**
```
entry.XXXX = Record ID (Zoho CRM record ID)
entry.YYYY = Dealer Code
```

**User-visible field:**
```
Photo — File upload (accept: image/*)
```

**Pre-filled URL:**
```
https://docs.google.com/forms/d/{FORM_ID}/viewform?entry.XXXX={record_id}&entry.YYYY={dealer_code}
```

**Apps Script trigger on form submit:**
1. Get `entry.XXXX` (Record ID) from form response
2. Get `entry.YYYY` (Dealer Code) from form response
3. Get uploaded file from Drive
4. Move to specific Drive folder
5. Make file public → get sharing URL
6. POST to Zoho CRM Dealer Meets sub-form:
   - Visit_Number: auto (query existing entries + 1)
   - Visit_Date: today
   - Image_URL: Drive sharing URL
   - Dealer_Code: from form
7. Update Firebase doc with latest_photo_url

---

## Credentials Stored

| File | Contents |
|---|---|
| `~/.hermes/zoho_credentials.json` | Active: client ID, secret, refresh token, access token |
| `~/.hermes/zoho_credentials_old.json` | Reference: old credentials |
| `~/.hermes/zoho_field_map.json` | Confirmed field API names |
| `~/.hermes/google_token.json` | Google OAuth (Sheets/Forms/Drive) |
| `~/.hermes/google_client_secret.json` | Google OAuth client |

---

## Repo Structure

```
On-going-projets-with-hermes/
  VSS/
    MASTER-PLAN-FIELD-APP.md   ← this file
    FIELD-APP/
      app.js                   ← current field app (needs update)
      index.html
    SCRIPTS/
      zoho-to-firebase-sync.js ← Zoho → Firebase sync
      firebase-to-zoho.js      ← Location update + info submit
    GOOGLE-FORMS/
      photo-upload-form.md    ← Form structure + entry IDs
      apps-script.js          ← Photo → Drive → Zoho bridge

  PanaceaX/
    (folder ready for future projects)

  Solar-Bangalore/
    (folder ready for future projects)
```

---

## Todo

### Phase 1 (start here)
- [ ] 1.1 Update app.js — add 3 buttons per dealer card
- [ ] 1.2 Location button: getCurrentPosition() → Zoho API PUT
- [ ] 1.3 Submit Info button: open built-in form modal → Zoho API PUT
- [ ] 1.4 On Submit Info: also increment Total_visits, set last_visit_date
- [ ] 1.5 Create Dealer Meets entry via POST after main record update
- [ ] 1.6 Location permission prompt on first app load
- [ ] 1.7 Build Zoho → Firebase sync (all fields)

### Phase 2
- [ ] 2.1 User creates Google Form (photo only)
- [ ] 2.2 User provides Form ID + entry IDs
- [ ] 2.3 Apps Script: form submit → Drive → Zoho Dealer Meets
- [ ] 2.4 Upload Photo button opens pre-filled Google Form

### Phase 3
- [ ] 3.1 App: show visit history with photos per dealer
- [ ] 3.2 Photo badge/indicator on dealer cards
- [ ] 3.3 Firebase: update latest_photo_url on each new photo

---

*Last updated: 2026-05-08*
