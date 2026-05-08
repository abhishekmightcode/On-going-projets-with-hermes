# VSS Field App — Master Implementation Plan
**Status:** PLANNED — awaiting execution
**Project:** VSS (V Sustain Solar Solutions)
**Last Updated:** 2026-05-08

---

## Overview

Build a **mobile-first field app** for VSS field employees (dealer visits) that:
1. Shows dealer/lead list from Firebase (synced from Zoho CRM)
2. Lets employee tap a dealer → pre-filled Google Form opens
3. Submits location (GPS → Zoho CRM directly via API)
4. Submits visit info (Google Form → Zoho CRM via API → Firebase for app display)
5. Syncs all data back from Zoho to Firebase for real-time app updates

**Stack:** React web app (existing) + Firebase Firestore + Google Sheets/Forms + Zoho CRM API + Google Apps Script (bridge)

---

## Architecture

```
┌─────────────────┐
│  Field Employee │
│  (Mobile Broser)│
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  VSS Field App  │◄─── Firebase (read dealer list)
│  (abhishekmight │     Dealer_Code → lat/lng/status/sync flag
│   code.github.io│
│   /vss-ups...)  │
└────────┬────────┘
         │
         │ 1. Tap dealer
         │ 2. "Send Location" → GPS → Zoho API
         │ 3. "Submit Info" → Google Form (pre-filled)
         │
         ▼
┌──────────────────────────────────────────────┐
│  ZOHO CRM  (Source of Truth)                 │
│  Modules: UPS (Dealers), Project_Execution   │
│  Sub-forms: Dealer Meets (visits)            │
└──────────────────────────────────────────────┘
         │
         │  Sync: Zoho → Firebase (periodic)
         ▼
┌─────────────────┐
│  Firebase       │
│  Firestore      │
│  Collection:    │
│  ups_dealers    │
└─────────────────┘

┌──────────────────────────────────────────────┐
│  GOOGLE FORMS (Data Entry Interface)          │
│  Pre-filled via URL params:                  │
│  dealer_code, phone, record_id               │
│  Employee fills remaining fields → submit    │
└──────────────────────────────────────────────┘
         │
         ▼
┌──────────────────────────────────────────────┐
│  GOOGLE APPS SCRIPT (Webhook Bridge)          │
│  Form Submit trigger → parse → Zoho API      │
│  Zoho API → update CRM record fields         │
│  Also: Dealer Meets sub-form entry creation   │
└──────────────────────────────────────────────┘
```

---

## Data Model

### Firebase Firestore: `ups_dealers`

```
Document ID = Dealer_Code (e.g. "UP32-001")

Fields:
  - id                  (Zoho Record ID, e.g. "UP32234230001234")
  - dealer_code         (e.g. "UP32-001")
  - code                (phone/contact code)
  - name                (dealer/shop name)
  - phone               (primary phone)
  - phone2              (secondary phone)
  - address             (text address)
  - city                (text)
  - lat                 (float — GPS latitude from field)
  - lng                 (float — GPS longitude from field)
  - location_synced     (bool — has Zoho been updated with lat/lng?)
  - last_visit_date     (ISO date string — most recent visit)
  - visit_count         (int — total visits, incremented per submission)
  - dealer_type         (text — from CRM)
  - last_order_date     (date — from CRM)
  - last_order_value    (number — from CRM)
  - total_lifetime_value (number — from CRM)
  - follow_up_date_time (datetime — from CRM)
  - follow_up_notes     (text — from CRM)
  - existing_battery_stock (text — from CRM)
  - existing_ups_stock    (text — from CRM)
  - existing_high_kva_ups_stock (text — from CRM)
  - approach_value      (text — from CRM)
  - credit_value        (text — from CRM)
  - status              (text — from CRM)
  - synced_at           (timestamp — last Zoho→Firebase sync)
  - zoho_last_modified  (timestamp — from Zoho for delta sync)
```

### Zoho CRM: UPS Module Fields (to update)

| Zoho Field Name       | Type     | Notes |
|-----------------------|----------|-------|
| Dealer_Code           | string   | Match key — do not update |
| id                    | string   | Record ID — used for API calls |
| Location_Latitude      | string   | GPS lat (filled by "Send Location") |
| Location_Longitude     | string   | GPS lng (filled by "Send Location") |
| Dealer_Type            | picklist | Set by employee via form |
| Last_Order_Date        | date     | From CRM, updated on new order |
| Last_Order_Value       | number   | From CRM, updated on new order |
| Total_Lifetime_Value   | number   | From CRM |
| Follow_up_Date_Time    | datetime | Updated on each visit |
| Follow_up_Notes        | text     | Updated on each visit |
| Existing_Battery_Stock | text     | Employee enters via form |
| Existing_UPS_Stock     | text     | Employee enters via form |
| Existing_High_KVA_UPS_Stock | text | Employee enters via form |
| Approach_Value         | text     | Employee enters via form |
| Credit_Value           | text     | Employee enters via form |

### Zoho CRM: Dealer Meets Sub-form (Phase 2)

| Zoho Sub-form Field    | Type     | Notes |
|-----------------------|----------|-------|
| Visit_Number           | int      | Auto-increment per dealer |
| Visit_Date             | date     | Auto-today |
| Visit_Notes            | text     | Employee enters |
| Competition_In_Use     | text     | Employee enters |
| Next_Follow_Up_Type    | picklist | call / visit / whatsapp |
| Image_URL              | url      | Added in Phase 3 (image form) |

---

## Google Form Structure

**Form Name:** VSS — Dealer Visit Report

**Pre-filled Fields (via URL params):**
- Entry ID (internal — hidden)
- Dealer Code (hidden, pre-filled)
- Phone (hidden, pre-filled)

**Employee-Filled Fields:**
1. **Dealer Type** — Dropdown: Retailer / Distributor / Institution / Service Partner
2. **Existing Battery Stock** — Text (e.g. "10 units Exide 150Ah")
3. **Existing UPS Stock** — Text
4. **Existing High KVA UPS Stock** — Text
5. **Approach Value** — Text (how to approach: main road, lane, landmark)
6. **Credit Value** — Text (current credit limit/outstanding)
7. **Follow-up Date & Time** — Date + Time picker
8. **Follow-up Notes** — Text area
9. **Visit Notes** — Text area (for Dealer Meets sub-form)
10. **Competition In Use** — Text
11. **Next Follow-up Type** — Dropdown: Call / Visit / WhatsApp / None

---

## Implementation Phases

### Phase 1 — App UI: Location & Visit (CRUD + Sync)

**Step 1.1 — Firebase Sync Script**
- Build Node.js script: Zoho CRM → Firebase Firestore
- Runs on-demand or cron (every 15 min)
- Uses Zoho CRM REST API (OAuth token)
- Delta sync: only records where `Last_Modified_Time` changed since last sync
- Updates all textual fields from CRM into Firebase

**Step 1.2 — Update VSS Field App UI**
- Home screen: list of dealers from Firebase
- Each card shows: name, dealer_code, phone, city, last_visit_date, visit_count
- "Send Location" button → GPS → Zoho API (updates lat/lng in CRM)
- "Submit Info" button → Opens Google Form (pre-filled via URL)
- Badge/indicator if location already synced

**Step 1.3 — Location Button Logic**
```
on click "Send Location":
  1. getCurrentPosition() — browser Geolocation API
  2. Store lat/lng in Firebase document
  3. Call Zoho CRM API: update record by ID
     PUT /crm/v2/UPS/{record_id}
     body: { "Location_Latitude": lat, "Location_Longitude": lng }
  4. Set location_synced = true in Firebase
  5. Show toast: "Location synced ✓"
```

**Step 1.4 — Submit Info Button Logic**
```
on click "Submit Info":
  1. Build Google Form URL with pre-filled params:
     https://docs.google.com/forms/d/{FORM_ID}/viewform?entry.ID={record_id}&entry.dealer_code={dealer_code}&entry.phone={phone}
  2. Open form in new tab (or in-app iframe)
  3. Employee fills form and submits
```

**Step 1.5 — Apps Script Webhook (Form → Zoho)**
```
Form Submit Trigger:
  1. Get form response (all fields)
  2. Extract record_id, dealer_code, phone from hidden pre-filled fields
  3. Map form fields to Zoho CRM field names
  4. PUT to Zoho CRM UPS module:
     PUT https://crm.zoho.in/crm/v2/UPS/{record_id}
     JSON: { "data": [{ all mapped fields }] }
  5. Also increment visit_count in Firebase (via REST)
  6. Set last_visit_date = today in Firebase
  7. Send confirmation email / show success
```

### Phase 2 — Dealer Meets Sub-form (Zoho Sub-form)

**Step 2.1 — Update Apps Script**
- After updating main UPS record, create Dealer Meets sub-form entry via:
  `POST /crm/v2/UPS/{record_id}/Dealer_Meets`
- Body: { Visit_Number, Visit_Date, Visit_Notes, Competition_In_Use, Next_Follow_Up_Type }

**Step 2.2 — App UI for Dealer Meets view**
- In app: tap dealer → see list of past visits
- Each visit card: date, visit_number, notes, competition

### Phase 3 — Image Submission (Future)

**Step 3.1 — Second Google Form**
- Form: "VSS — Dealer Visit Photo"
- Fields: Photo upload, Caption, Record ID (pre-filled)
- Apps Script: on submit, upload photo to Google Drive, get public URL
- Update Dealer Meets sub-form entry with Image_URL

---

## Credentials & Access Required

| Service | Credential | Status |
|---------|-----------|--------|
| Zoho CRM | OAuth token (refresh) | 🔒 Stored in Firebase/gate |
| Google Forms | Form ID + Apps Script | 🔒 To be created |
| Google Sheets | Backup sheet ID | 🔒 To be created |
| Firebase | API key + project | ✅ Already configured |

---

## Google Form URL Structure (Pre-filled Params)

```
https://docs.google.com/forms/d/{FORM_ID}/viewform?
  entry.XXXXX={record_id}&       # hidden: Zoho record ID
  entry.XXXXX={dealer_code}&     # hidden: dealer code
  entry.XXXXX={phone}            # hidden: phone number
```

**Note:** Entry field IDs (XXXXX) are assigned by Google Forms and must be extracted from the form's edit URL after creation.

---

## Zoho CRM API Reference

**Base URL:** `https://crm.zoho.in/crm/v2`

**Auth:** `Zoho-oauthtoken` header with refresh token

**UPS Module — Update Record:**
```
PUT /crm/v2/UPS/{record_id}
Headers: Authorization: Zoho-oauthtoken {token}
Body: { "data": [{ "field_api_name": value, ... }] }
```

**UPS Module — Get Record:**
```
GET /crm/v2/UPS/{record_id}
Headers: Authorization: Zoho-oauthtoken {token}
```

**UPS Module — Get All Records (with delta sync):**
```
GET /crm/v2/UPS?fields=id,Dealer_Code,name,phone,Location_Latitude,...
    &sort_by=Modified_Time&sort_order=desc&page=1&per_page=200
Headers: Authorization: Zoho-oauthtoken {token}
```

**Dealer Meets Sub-form — Create Entry:**
```
POST /crm/v2/UPS/{record_id}/Dealer_Meets
Body: { "data": [{ "Visit_Number": 1, "Visit_Date": "2026-05-08", ... }] }
```

---

## Files & Repo Structure

```
On-going-projets-with-hermes/
  VSS/
    MASTER-PLAN-FIELD-APP.md    ← this file
    FIELD-APP/
      app.js                    ← updated field app
      index.html                ← main UI
    SCRIPTS/
      zoho-to-firebase-sync.js  ← Phase 1.1: Zoho → Firebase sync
      apps-script.js            ← Google Apps Script (Form → Zoho bridge)
      firebase-sync.js          ← Firebase helpers
    GOOGLE-FORMS/
      dealer-visit-form.md      ← Form field map + entry IDs
      form-url-builder.md       ← How to build pre-filled URLs
    CREDENTIALS.md              ← All API keys / tokens (gitignored)
```

---

## Todo Checklist

### Phase 1
- [ ] 1.1 Create Zoho OAuth refresh token flow (user provides once)
- [ ] 1.2 Write Zoho → Firebase sync script (Node.js)
- [ ] 1.3 Test sync: pull all UPS records into Firebase
- [ ] 1.4 Update field app: show dealer list from Firebase
- [ ] 1.5 Add "Send Location" button + GPS → Zoho API logic
- [ ] 1.6 Create Google Form: Dealer Visit Report
- [ ] 1.7 Get form entry field IDs
- [ ] 1.8 Build pre-filled form URL logic in app
- [ ] 1.9 Create Apps Script: Form Submit → Zoho API
- [ ] 1.10 Test full flow: form submit → Zoho update → Firebase update
- [ ] 1.11 Deploy Apps Script as web app / form trigger
- [ ] 1.12 Test "Submit Info" button in app

### Phase 2
- [ ] 2.1 Extend Apps Script: also create Dealer Meets sub-form entry
- [ ] 2.2 Update app: show visit history per dealer
- [ ] 2.3 Increment visit_count in Firebase on each submission

### Phase 3
- [ ] 3.1 Create image upload form
- [ ] 3.2 Apps Script: upload to Drive → get public URL
- [ ] 3.3 Update Dealer Meets entry with Image_URL

---

## Notes

- **Zoho Refresh Token:** User must provide once. I will store it securely.
- **Google Form Entry IDs:** Unique per form — must extract after form creation.
- **Location Permission:** Browser Geolocation API. Employee grants once, reused.
- **No Zoho write from Firebase directly** — always goes through Apps Script bridge for security.
- **Firebase is read-cache** for app display. Zoho is source of truth.
- **Periodic sync:** Zoho → Firebase every 15 min to catch changes made outside the app.

---

*Last updated: 2026-05-08*
