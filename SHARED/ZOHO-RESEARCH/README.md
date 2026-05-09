# SHARED — Zoho CRM Research

> Cross-project Zoho CRM API reference. All parts researched and documented from official Zoho CRM v2 API.

**Source:** https://www.zoho.com/crm/developer/docs/api/v2/

---

## Contents

| Part | File | What's Inside |
|------|------|--------------|
| 1 | `PART-1-API-V8-OVERVIEW.md` | API basics, authentication, base URL, request/response format |
| 2 | `PART-2-RECORDS-CRUD.md` | GET, POST, PUT, DELETE records; field types, pagination |
| 3 | `PART-3-BULK-COMPOSITE-APIs.md` | Bulk operations, layout IDs, sub-forms, multi-lookup |
| 4 | `PART-4-METADATA-APIs.md` | Modules, fields, layouts, custom views |
| 5 | `PART-5-USER-TERRITORY-APIs.md` | Users, roles, territories, groups |
| 6 | `PART-6-DEVELOPER-TOOLS.md` | Client app, server-based app, JS SDK, webhooks, BluePrint |
| 7 | `PART-7-ZIA-AI.md` | Zia AI, predict, anomaly detection, sentiment analysis |
| 8 | `PART-8-INTEGRATIONS-SECURITY.md` | Extensions, market, info, security, best practices |
| Ref | `ZOHO-CRM-COMPLETE-REFERENCE.md` | Full consolidated reference (very large) |

---

## Key Facts for VSS / PanaceaX Projects

### Authentication (Server-based App)
```
POST https://accounts.zoho.in/oauth/v2/token
Body: grant_type=refresh_token&client_id=XXX&client_secret=XXX&refresh_token=XXX
Response: { "access_token": "..." }
```

### Update a Record
```
PUT https://crm.zoho.in/crm/v2/{module}/{record_id}
Headers: Authorization: Zoho-oauthtoken {token}, Content-Type: application/json
Body: { "data": [{ "field_api_name": "value" }] }
```

### Create Sub-form Entry
```
POST https://crm.zoho.in/crm/v2/{module}/{record_id}/{subform_api_name}
Headers: Authorization: Zoho-oauthtoken {token}, Content-Type: application/json
Body: { "data": [{ "subform_field_api_name": "value" }] }
```

### Get All Records
```
GET https://crm.zoho.in/crm/v2/{module}?fields=ALL&per_page=200&page=1
Headers: Authorization: Zoho-oauthtoken {token}
```

---

## Known Zoho DC-Specific URLs

| DC | Token URL | API Base |
|----|-----------|----------|
| `.in` (India) | `https://accounts.zoho.in/oauth/v2/token` | `https://crm.zoho.in/crm/v2` |
| `.com` (US) | `https://accounts.zoho.com/oauth/v2/token` | `https://crm.zoho.com/crm/v2` |
| `.eu` (Europe) | `https://accounts.zoho.eu/oauth/v2/token` | `https://crm.zoho.eu/crm/v2` |

---

*Last updated: 2026-05-09*