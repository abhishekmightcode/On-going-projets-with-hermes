# VSS Field App — Master Implementation Plan
**Status:** PHASE 1 IN PROGRESS
**Project:** VSS (V Sustain Solar Solutions)
**Last Updated:** 2026-05-08

---

## Overview

Mobile-first field app for VSS employees (dealer visits):
- Shows dealer list from Firebase (synced from Zoho CRM)
- Tap dealer → "Send Location" (GPS → Zoho via API)
- Tap dealer → "Submit Info" (Google Form pre-filled → Zoho via API)
- Zoho is source of truth; Firebase is read-cache for app display

**Stack:** React web app + Firebase Firestore + Google Forms + Zoho CRM API + Google Apps Script

---

## Architecture

    Field Employee (Mobile Browser)
              │
              ▼
    ┌─────────────────────────┐
    │  VSS Field App           │◄── Firebase (dealer list cache)
    │  abhishekmightcode.github│     doc ID = Dealer_Code
    │  .io/vss-ups-field-app   │
    └────────┬────────────────┘
              │
    ┌─────────▼────────────────┐     ┌─────────────────────┐
    │  Firebase Firestore      │     │  Google Forms       │
    │  ups_dealers collection  │     │  Dealer Visit Report│
    │  (doc ID = Dealer_Code)  │     │  (pre-filled via    │
    └─────────┬────────────────┘     │   URL params)       │
              │                     └──────────┬──────────┘
              │  Zoho ←→ Hermes sync                │
    ┌─────────▼────────────────┐                  ▼
    │  ZOHO CRM               │    ┌────────────────────────┐
    │  UPS Module             │    │  Google Apps Script    │
    │  Sub-form: Dealer Meets │    │  Form Submit Trigger   │
    └─────────────────────────┘    │  → Zoho CRM API update │
                                   └────────────────────────┘

---

## Zoho CRM Field Map (Confirmed)

| App Field         | Zoho API Name                        |
|--------------------|--------------------------------------|
| id                 | id                                   |
| name               | Name                                 |
| dealer_code        | Dealer_code                          |
| phone              | Phone                                |
| dealer_type       | Dealer_Type                          |
| location_lat       | Address_of_the_dealer_Coordinates_Latitude |
| location_lng       | Address_of_the_dealer_Coordinates_Longitude |
| last_order_date    | Last_Order_Date                      |
| last_order_value   | Last_Order_Value                     |
| total_lifetime_value | Total_Lifetime_Value                |
| follow_up_date_time| Follow_up_date_and_time              |
| follow_up_notes   | Follow_up_notes                      |
| existing_battery_stock | Existing_Battery_stock           |
| existing_ups_stock | Existing_UPS_stock                  |
| existing_high_kv_ups_stock | Existing_High_KV_UPS_stock    |
| approx_value_in_outlet | Approx_value_in_outlet          |
| credit_value_with_dealer | Credit_value_with_dealer      |
| total_visits       | Total_visits                        |
| address            | Address_of_the_dealer               |
| city               | Address_of_the_dealer_City          |

**Zoho sub-form:** `Dealer_meets` — per-visit entries

---

## Firebase Firestore: ups_dealers

Doc ID = `Dealer_Code` (e.g. "UP32-001")

```
{
  id: "1171062000002812045"       ← Zoho record ID
  dealer_code: "UP32-001"         ← Firebase doc ID
  name: "Sri Bhyraveshwara..."
  phone: "919845367915"
  dealer_type: "Retailer"
  address: "Shop No. 12, MG Road"
  city: "Bangalore"
  lat: 12.9716
  lng: 77.5946
  location_synced: false          ← has GPS been sent to Zoho?
  last_visit_date: null
  visit_count: 0
  last_order_date: null
  last_order_value: null
  total_lifetime_value: null
  follow_up_date_time: null
  follow_up_notes: ""
  existing_battery_stock: ""
  existing_ups_stock: ""
  existing_high_kv_ups_stock: ""
  approx_value_in_outlet: ""
  credit_value_with_dealer: ""
  status: ""
  synced_at: timestamp
}
```

---

## Phase 1 Steps

### 1.1 — Zoho OAuth Setup
- [x] Client ID + Secret obtained
- [x] Authorization code flow completed
- [x] Refresh token + Access token stored at `~/.hermes/zoho_credentials.json`
- [x] Field API names confirmed via `GET /crm/v2/settings/fields?module=UPS`
- [x] All 43 fields identified (43 in UPS module)

### 1.2 — Firebase ↔ Zoho Mapping
- [x] Firebase doc ID = Dealer_Code
- [x] Zoho Record ID = `id` field from CRM
- [ ] Need: mapping from Dealer_Code → Zoho Record ID
  - Strategy: search Zoho by Dealer_code when syncing
  - OR: maintain a Firebase field `zoho_id` per document

### 1.3 — Build Zoho → Firebase Sync Script
- Reads all UPS records from Zoho (paginated)
- For each record: finds matching Firebase doc by Dealer_code
- Updates Firebase doc with all fields
- Sets `zoho_last_modified` timestamp

### 1.4 — Build Firebase → Zoho Sync Script (for location update)
- App sends: `PUT /crm/v2/UPS/{id}` with lat/lng
- Uses Zoho access token

### 1.5 — Google Form: Dealer Visit Report
- Create form (user action needed)
- Hidden pre-filled fields: Record ID, Dealer Code, Phone
- Employee fills: Dealer Type, battery stock, UPS stock, approach value, credit value, follow-up date/time, follow-up notes

### 1.6 — Apps Script Webhook
- On form submit: parse response → Zoho API update
- Also increment visit_count in Firebase
- Set last_visit_date = today

### 1.7 — Update Field App UI
- "Send Location" button per dealer card
- "Submit Info" button → pre-filled Google Form URL

### 1.8 — App Location Permission Flow
- On first load: request geolocation permission
- Store coords; reuse for all "Send Location" calls

---

## Google Form Structure

**Form Name:** VSS — Dealer Visit Report

**Hidden pre-filled fields (via URL params):**
- `entry.ID` = Zoho Record ID
- `entry.dealer_code` = Dealer code
- `entry.phone` = Phone number

**Employee fills:**
| Question | Zoho Field to Update |
|---|---|
| Dealer Type | Dealer_Type |
| Existing Battery Stock | Existing_Battery_stock |
| Existing UPS Stock | Existing_UPS_stock |
| Existing High KV UPS Stock | Existing_High_KV_UPS_stock |
| Approx Value in Outlet | Approx_value_in_outlet |
| Credit Value with Dealer | Credit_value_with_dealer |
| Follow-up Date & Time | Follow_up_date_and_time |
| Follow-up Notes | Follow_up_notes |
| Visit Notes | → Dealer_meets sub-form (Phase 2) |
| Competition In Use | → Dealer_meets sub-form (Phase 2) |
| Next Follow-up Type | → Dealer_meets sub-form (Phase 2) |

---

## Implementation Status

| Step | Status |
|------|--------|
| Zoho credentials stored | ✅ |
| Field names confirmed | ✅ |
| Google OAuth (Sheets/Forms/Drive) | ✅ |
| Firebase (read) | ✅ |
| Google Form created | ⏳ User to create |
| Apps Script webhook | ⏳ Pending |
| Field app UI update | ⏳ Pending |
| Location button | ⏳ Pending |
| Submit Info button | ⏳ Pending |
| Full sync Zoho ↔ Firebase | ⏳ Pending |

---

## Credentials

| Service | File |
|---|---|
| Zoho CRM (active) | `~/.hermes/zoho_credentials.json` |
| Zoho CRM (reference) | `~/.hermes/zoho_credentials_old.json` |
| Zoho field map | `~/.hermes/zoho_field_map.json` |
| Google OAuth | `~/.hermes/google_token.json` |
| Google client secret | `~/.hermes/google_client_secret.json` |
| Firebase | `~/.hermes/vss-firebase-config.json` |

---

*Last updated: 2026-05-08*
