# VSS — Status

**Last updated:** 2026-05-09

## Current Architecture

```
Field Employee (mobile browser)
  └─── "📍 Send Location" ──→ n8n webhook ──→ Zoho CRM (handled in n8n workflow)
  └─── "📝 Submit Info"    ──→ n8n webhook ──→ Zoho CRM (handled in n8n workflow)
  └─── Firebase (read-cache, seeded by server-side Zoho sync)
```

**Web app:** `https://abhishekmightcode.github.io/vss-ups-field-app/`
**Webhook:** `https://vsustainsolar.app.n8n.cloud/webhook/ed515a09-7182-4541-9f7d-5b356d2e5770`

## Two Payloads

### Send Location (`action: "send_location"`)
```json
{
  "action": "send_location",
  "timestamp": "2026-05-09T...",
  "dealer": {
    "zoho_id": "1171062000002901006",
    "dealer_code": "1000036809",
    "name": "Ae Battery Point"
  },
  "location": {
    "latitude": 12.9716,
    "longitude": 77.5946,
    "accuracy": 10
  }
}
```

### Submit Info (`action: "submit_info"`)
```json
{
  "action": "submit_info",
  "timestamp": "2026-05-09T...",
  "dealer": {
    "zoho_id": "1171062000002901006",
    "dealer_code": "1000036809",
    "name": "Ae Battery Point",
    "phone": "+919448043392"
  },
  "visit": {
    "visit_number": 1,
    "visit_date": "2026-05-09",
    "visit_notes": "Checked stock, suggested Exide upgrade",
    "competition_in_use": "Exide, Luminous",
    "follow_up_type": "Call"
  },
  "fields": {
    "Dealer_Type": "Retailer",
    "Existing_Battery_stock": "20",
    "Existing_UPS_stock": "5",
    "Existing_High_KV_UPS_stock": "2",
    "Approx_value_in_outlet": "50000",
    "Credit_value_with_dealer": "20000",
    "Follow_up_date_and_time": "2026-05-12T10:00:00.000Z",
    "Follow_up_notes": "Follow up on Exide stock"
  }
}
```

## What's Working

- ✅ Dealer list loads from Firebase
- ✅ Firebase seeded from Zoho via server-side sync (Node.js script)
- ✅ Send Location sends GPS + dealer info to n8n webhook
- ✅ Submit Info sends full form + visit data to n8n webhook
- ✅ Firebase updates locally after each action

## What's Pending (n8n side)

- n8n workflow needs to receive webhook payloads and write to Zoho CRM
- Dealer Meets sub-form entries in Zoho (for visit history)
- Photo upload via Google Form (button exists, not wired)

## Known Issues

- n8n workflow not yet configured to consume these payloads
- Cloudflare tunnel / Zoho proxy **no longer needed** — kept as fallback reference

## Removed (2026-05-09)

- Cloudflare tunnel dependency
- Local Node.js Zoho proxy (port 3000)
- `getZohoToken()`, `zohoUpdateRecord()`, `zohoCreateDealerMeets()`
- Browser CORS issues → gone, webhook POST has no CORS restrictions