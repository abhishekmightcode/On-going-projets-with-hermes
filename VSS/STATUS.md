# VSS — Status

**Last updated:** 2026-05-09

## Current Architecture

```
Field Employee (mobile browser)
  ├─── "📍 Send Location"  ──→ n8n webhook ──→ Zoho CRM
  ├─── "📝 Submit Info"    ──→ n8n webhook ──→ Zoho CRM
  └─── "📋 Record Meeting" ──→ n8n webhook ──→ Zoho CRM

Firebase ← Zoho sync (server-side, every 15 min) — Firebase is READ-ONLY for field app
```

**Web app:** `https://abhishekmightcode.github.io/vss-ups-field-app/`
**Webhook:** `https://vsustainsolar.app.n8n.cloud/webhook/ed515a09-7182-4541-9f7d-5b356d2e5770`

## Data Flow Rules (May 2026)

- **Zoho is the single source of truth**
- **Firebase is a read-cache only** — seeded from Zoho, never written by field app
- **Field app reads from Firebase** — loads dealer list for display
- **Field app writes to n8n webhook only** — never touches Zoho or Firebase directly
- **n8n workflow** receives all payloads and writes to Zoho CRM
- **Server-side Zoho→Firebase sync** runs every 15 min to refresh the read-cache

## Three Webhook Payloads

### 1. Send Location (`action: "send_location"`)
```json
{
  "action": "send_location",
  "timestamp": "2026-05-09T...",
  "dealer": { "zoho_id": "...", "dealer_code": "...", "name": "..." },
  "location": { "latitude": 12.9716, "longitude": 77.5946, "accuracy": 10 }
}
```

### 2. Submit Info (`action: "submit_info"`)
```json
{
  "action": "submit_info",
  "timestamp": "2026-05-09T...",
  "dealer": { "zoho_id": "...", "dealer_code": "...", "name": "...", "phone": "..." },
  "fields": {
    "Dealer_Type": "Retailer", "Existing_Battery_stock": "20",
    "Existing_UPS_stock": "5", "Existing_High_KV_UPS_stock": "2",
    "Approx_value_in_outlet": "50000", "Credit_value_with_dealer": "20000",
    "Follow_up_date_and_time": "2026-05-12T...", "Follow_up_notes": "..."
  }
}
```

### 3. Record Meeting (`action: "record_meeting"`)
```json
{
  "action": "record_meeting",
  "timestamp": "2026-05-09T...",
  "dealer": { "zoho_id": "...", "dealer_code": "...", "name": "...", "phone": "..." },
  "meeting": {
    "visit_number": 1,
    "visit_date": "2026-05-09",
    "visit_purpose": "Sales Visit",
    "visit_notes": "Discussed Exide battery stock...",
    "competition": "Luminous, Exide",
    "outcome": "Positive - Order Likely",
    "next_follow_type": "Visit",
    "next_follow_date": "2026-05-15",
    "order_value_expected": "45000"
  }
}
```

## What's Working

- ✅ Dealer list loads from Firebase (read-only)
- ✅ Send Location → n8n webhook
- ✅ Submit Info → n8n webhook
- ✅ Record Meeting → n8n webhook
- ✅ Firebase is updated ONLY by server-side Zoho sync (never by field app)

## What's Pending (n8n side)

- n8n workflow needs to handle all 3 action types and write to Zoho CRM
- Need: PUT to UPS record for Send Location (lat/lng fields)
- Need: PUT to UPS record for Submit Info (stock + follow-up fields)
- Need: POST to Dealer_Meets sub-form for Record Meeting

## Firebase Document Model

Firebase doc ID = Zoho record ID (stable primary key)

```json
{
  "id": "1171062000002901006",
  "dealer_code": "1000036809",
  "name": "Ae Battery Point",
  "phone": "+919448043392",
  "dealer_type": "Retailer",
  "city": "Bangalore",
  "visit_count": 3,
  "last_visit_date": "2026-05-09",
  "lat": 12.9716,
  "lng": 77.5946,
  "location_synced": true,
  "dealer_meets": [ /* array of visit records from Zoho sync */ ]
}
```

## What n8n Workflow Must Do

1. **Receive webhook** — JSON with `action` field
2. **Route by action:**
   - `send_location` → `PUT /crm/v2/UPS/{zoho_id}` with lat/lng fields
   - `submit_info` → `PUT /crm/v2/UPS/{zoho_id}` with stock + follow-up fields
   - `record_meeting` → `POST /crm/v2/UPS/{zoho_id}/Dealer_Meets` with meeting details
3. **Verify write to Zoho** — confirm 200 response before marking done

## Removed (May 2026)

- Cloudflare tunnel / Zoho proxy (no longer needed — webhook has no CORS)
- Firebase writes from field app (now read-only from app side)
- `getZohoToken()`, `zohoUpdateRecord()`, `zohoCreateDealerMeets()` (all removed)