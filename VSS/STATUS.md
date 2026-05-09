# VSS — Current Status

**Last updated:** 2026-05-09

---

## ✅ What Is Working

### Field App (Production)
- **URL:** https://abhishekmightcode.github.io/vss-ups-field-app/
- **GitHub repo:** `abhishekmightcode/vss-ups-field-app`
- Dealer list loads from Firebase instantly
- Dealer detail modal shows: name, phone, dealer code, record ID, type, LTV, address, GPS status, visit count
- **Send Location button** — GPS → Zoho CRM via `PUT /crm/v2/UPS/{record_id}` with lat/lng ✅
- **Submit Info button** — In-app form → Zoho CRM PUT + Dealer Meets POST ✅
- **Upload Photo button** — Shows Google Form (disabled until form is created by user)
- Firebase syncs from Zoho on app load + every hour via cron
- Toast notifications for success/error ✅
- Filter chips (All / Distributor / Retailer / Service Partner / Institution) ✅
- Search (dealer name, city, code) ✅

### Zoho CRM
- 80 dealer records in UPS module, all with 10-digit `Dealer_code` + `+91` phones
- Zoho record IDs captured and used as Firebase doc IDs
- Server-based OAuth (client ID + client secret + refresh token)

### Firebase
- Collection `upsdealers` — 80 docs, doc ID = Zoho record ID (PRIMARY KEY)
- `dealer_code` stored as field inside each doc (secondary key)
- Hourly sync via `vss_zoho_firebase_sync.py` (cron job ID: `e7474b1dd47e`, schedule: `0 * * * *`)

---

## ❌ What Is NOT Working / Pending

### Google Form Photo Upload
- **Status:** Not set up yet
- User needs to create a Google Form with: Record ID (hidden), Dealer Code (hidden), Photo (file upload)
- Once created, update `config.js` with `GOOGLE_FORM` values (`enabled: true`, `base_url`, `entry_record_id`, `entry_dealer_code`)
- Apps Script needed to: form submit → upload to Drive → get URL → POST to Zoho Dealer Meets sub-form

### Dealer Meets Sub-form (Visit History)
- Currently when `submitInfoForm()` runs, it creates a Dealer Meets entry in Zoho via POST
- The app does NOT yet fetch and display Dealer Meets history from Zoho in the "Recent Visits" section of the modal
- Firebase does NOT store Dealer Meets array consistently after sync
- **Fix needed:** Fetch Dealer Meets sub-form records via GET and display in app

### Visit History in App
- "Recent Visits" section in modal shows `d.dealer_meets` from Firebase (set locally on submit)
- On app reload, `dealer_meets` comes from Firebase — but Firebase sync doesn't fetch sub-form data
- **Fix needed:** `syncFromZoho()` should also fetch Dealer Meets sub-form per record

### First Sync on App Load
- `syncFromZoho()` runs after `loadFromFirebase()` but shows stale data briefly
- Not a functional bug, but UX could be improved (show loading indicator during sync)

---

## 🔧 Known Bugs Fixed (2026-05-09)

| Bug | Fix | Commit |
|-----|-----|--------|
| `docRef` undefined in `syncFromZoho()` | Added missing `docRef` declaration | `ecb5edf` |
| Firebase doc ID used `dealer_code` in `sendLocation()` | Changed to `activeDealer.id` (Zoho record ID) | `ecb5edf` |
| Firebase doc ID used `dealer_code` in `submitInfoForm()` | Changed to `activeDealer.id` (Zoho record ID) | `ecb5edf` |
| `data.dealer_code = String(code)` overwrote mapped value | Removed the errant line | `8f266e2` |
| Firebase collection name was `ups_dealers` (underscore) | Changed to `upsdealers` | `8755ea9` |
| `modalRecordId` not shown in dealer modal | Added field with 🔑 icon | `8755ea9` |

---

## 📋 Next Steps (Priority Order)

1. **Create Google Form** for photo upload — user action needed
2. **Display Dealer Meets history in app** — fetch sub-form data from Zoho on modal open
3. **Fix `syncFromZoho()`** to also fetch Dealer Meets sub-form per record
4. **Add photo badge** on dealer cards when photo has been uploaded
5. **PanaceaX implementation** — once Abhishek clarifies scope
6. **n8n workflow** for automated daily sync report

---

## 📊 Data Model Summary

```
Firebase Collection: upsdealers
Doc ID = Zoho Record ID (PRIMARY KEY)    e.g. "1171062000002901006"
                                             
Field: dealer_code = "1000036809"         (secondary key, human-readable)
Field: id = "1171062000002901006"         (same as doc ID, for reference)
Field: name = "Sri Bhyraveshwara Battery Point"
Field: phone = "+919845367915"
Field: lat, lng = GPS coordinates (set when employee sends location)
Field: location_synced = boolean
Field: visit_count = number
Field: last_visit_date = ISO date string
Field: dealer_meets = array (set locally on submit)
Field: last_synced = Firestore timestamp
```

---

## 🔑 Key Zoho API Facts

- **DC:** `.in` (India) — `crm.zoho.in`
- **Module:** UPS (API name)
- **Update record:** `PUT /crm/v2/UPS/{record_id}` — body: `{ "data": [{ ...fields }] }`
- **Create Dealer Meets:** `POST /crm/v2/UPS/{record_id}/Dealer_meets` — body: `{ "data": [{ ...subform_fields }] }`
- **Get all records:** `GET /crm/v2/UPS?fields=ALL&per_page=200&page=1`
- **Latitude field:** `Address_of_the_dealer_Coordinates_Latitude`
- **Longitude field:** `Address_of_the_dealer_Coordinates_Longitude`
- **Dealer_code field:** `Dealer_code` (string, 255 chars — stores 10-digit codes)
- **Phone field:** `Phone` — must include `+91` prefix

---

*Last updated: 2026-05-09*