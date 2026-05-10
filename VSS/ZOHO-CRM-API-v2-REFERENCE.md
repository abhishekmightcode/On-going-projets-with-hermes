# Zoho CRM API v2 — Complete Reference

> Source: https://www.zoho.com/crm/developer/docs/api/v2/
> Base URL: `https://www.zohoapis.com/crm/v2`
> Auth: `Authorization: Zoho-oauthtoken {access_token}`
> Body format: `{"data": [...]}` — bare arrays will fail

---

## Entity API — Records

### 1. Get Records (List)
```
GET https://www.zohoapis.com/crm/v2/{module_api_name}
```
**Query params:**
- `page` — page number (default 1)
- `per_page` — records per page (max 200)
- `fields` — comma-separated field list (e.g. `id,Name,Dealer_Code`)
- `sort_by` — field to sort by
- `sort_order` — `asc` or `desc`
- `cvid` — custom view ID
- `ids` — filter by record IDs
- `territory_id` — territory filter
- `approved` — `true`/`false` for approval-filtered records
- `converted` — `true`/`false` for converted leads

**curl:**
```bash
curl "https://www.zohoapis.com/crm/v2/UPS?per_page=200&fields=id,Name,Dealer_Code,Phone,Dealer_Type" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

**Response:**
```json
{
  "data": [
    { "id": "1171062000002903016", "Name": "Harshita Tiwari", "Dealer_Code": null, ... }
  ],
  "info": { "page": 1, "per_page": 200, "total_count": 80, "more_records": false }
}
```

---

### 2. Get Record by ID
```
GET https://www.zohoapis.com/crm/v2/{module_api_name}/{record_id}
```
**Query params:** `fields` (optional, defaults to ALL)

**curl:**
```bash
curl "https://www.zohoapis.com/crm/v2/UPS/1171062000002903016?fields=ALL" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

**Response:**
```json
{
  "data": [{
    "id": "1171062000002903016",
    "Name": "Harshita Tiwari",
    "Phone": null,
    "Dealer_Code": null,
    "Dealer_Type": null,
    ...
  }]
}
```

**Note:** Single-record fetch returns ALL fields. List API returns only `id` for some tokens with limited scopes.

---

### 3. Insert Records (Create)
```
POST https://www.zohoapis.com/crm/v2/{module_api_name}
```
**Body:** `{"data": [ {...}, ... ]}` — max 100 records per call (Zoho recommends ≤10 for reliability)

**curl:**
```bash
curl -X POST "https://www.zohoapis.com/crm/v2/UPS" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -d '{"data": [{"Name": "Test Dealer", "Dealer_Code": "1000036999", "Phone": "9448043392"}]}'
```

**Response:**
```json
{
  "data": [{
    "code": "SUCCESS",
    "details": { "id": "1171062000002903016" },
    "message": "record added",
    "status": "success"
  }]
}
```

---

### 4. Update Records
```
PUT https://www.zohoapis.com/crm/v2/{module_api_name}          # bulk update
PUT https://www.zohoapis.com/crm/v2/{module_api_name}/{record_id}  # single record
```
**Body:** `{"data": [{"id": "record_id", "field": "value", ...}]}`

**curl:**
```bash
curl -X PUT "https://www.zohoapis.com/crm/v2/UPS/1171062000002903016" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -d '{"data": [{"Address_of_the_dealer_Coordinates_Latitude": "12.9716"}]}'
```

**Response:**
```json
{
  "data": [{
    "code": "SUCCESS",
    "details": { "id": "1171062000002903016" },
    "message": "record updated",
    "status": "success"
  }]
}
```

---

### 5. Delete Records
```
DELETE https://www.zohoapis.com/crm/v2/{module_api_name}?ids={record_id}      # single
DELETE https://www.zohoapis.com/crm/v2/{module_api_name}?ids={id1},{id2}       # multiple (NOT comma-separated single param — separate ?ids= for each)
DELETE https://www.zohoapis.com/crm/v2/{module_api_name}/{record_id}           # single by path
```
**Note:** Zoho DELETE accepts one ID per call in path format, or multiple `ids=` repeated params.

**curl:**
```bash
# Single record by path
curl -X DELETE "https://www.zohoapis.com/crm/v2/UPS/1171062000002903016" \
  -H "Authorization: Zoho-oauthtoken $AT"

# Multiple records
curl -X DELETE "https://www.zohoapis.com/crm/v2/UPS?ids=1171062000002903016,1171062000002903015" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

**Response:**
```json
{ "data": [{ "code": "SUCCESS", "message": "record deleted", "status": "success" }] }
```

---

### 6. Upsert Records (Insert or Update by External Field)
```
POST https://www.zohoapis.com/crm/v2/{module_api_name}/upsert
```
**Header:** `X-EXTERNAL-FIELD: {field_api_name}` — the field to match on

**curl:**
```bash
curl -X POST "https://www.zohoapis.com/crm/v2/UPS/upsert" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -H "X-EXTERNAL-FIELD: Dealer_Code" \
  -d '{"data": [{"Dealer_Code": "1000036809", "Name": "Updated Name", "Phone": "9448043392"}]}'
```

**Response:**
```json
{
  "data": [{
    "code": "SUCCESS",
    "details": { "id": "1171062000002903016", "updated": true },
    "message": "record updated",
    "status": "success"
  }]
}
```

---

### 7. Search Records
```
GET https://www.zohoapis.com/crm/v2/{module_api_name}/search?criteria={field}:{operator}:{value}
GET https://www.zohoapis.com/crm/v2/{module_api_name}/search?word={keyword}
GET https://www.zohoapis.com/crm/v2/{module_api_name}/search?phone={phone_number}
GET https://www.zohoapis.com/crm/v2/{module_api_name}/search?email={email}
```
**Operators:** `equals`, `not_equals`, `contains`, `starts_with`, `ends_with`, `greater_than`, `less_than`, `between`

**criteria example:** `(Dealer_Code:equals:1000036809)`
**Logical operators:** combine with `and`, `or` — `(Last_Name:equals:Doe and First_Name:equals:John)`

**Scope required:** `ZohoSearch.securesearch.READ`

**curl:**
```bash
curl "https://www.zohoapis.com/crm/v2/UPS/search?criteria=(Dealer_Code:equals:1000036809)" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

---

### 8. Get Related Records
```
GET https://www.zohoapis.com/crm/v2/{module_api_name}/{record_id}/{related_module_api_name}
```
**Query params:** `page`, `per_page`

**curl:**
```bash
# Get Dealer_Meets sub-form entries for a UPS record
curl "https://www.zohoapis.com/crm/v2/UPS/1171062000002903016/Dealer_Meets?per_page=200" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

---

### 9. Get Notes
```
GET https://www.zohoapis.com/crm/v2/{module_api_name}/{record_id}/notes?page=1&per_page=200
```

---

### 10. Insert Sub-form / Related Records
```
POST https://www.zohoapis.com/crm/v2/{module_api_name}/{record_id}/{related_module_api_name}
```
**Body:** `{"data": [{...subform_fields...}]}`

**curl — Insert Dealer Meets entry:**
```bash
curl -X POST "https://www.zohoapis.com/crm/v2/UPS/1171062000002903016/Dealer_Meets" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -d '{"data": [{
    "Visit_Number": 1,
    "Visit_Date": "2026-05-10",
    "Visit_Purpose": "Sales Visit",
    "Visit_Notes": "Discussed new 3kVA system",
    "Outcome": "Positive - Order Likely",
    "Next_Follow_Up_Type": "Demo",
    "Next_Follow_Up_Date": "2026-05-15",
    "Order_Value_Expected": "45000"
  }]}'
```

---

## Bulk Write API

> Documentation: `https://www.zoho.com/crm/developer/docs/api/v2/bulk-write/`
> Upload → Create Job → Poll → Download Results

### Step 1 — Upload CSV File
```
POST https://upload.zoho.com/crm/v8/upload
```
**Headers:**
- `Authorization: Zoho-oauthtoken {token}`
- `feature: bulk-write`
- `X-CRM-ORG: {zgid}` — your Zoho Group ID (ORGID)

**Body:** `multipart/form-data` with `file` field (ZIP containing CSV)

**curl:**
```bash
curl -X POST "https://upload.zoho.com/crm/v8/upload" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "feature: bulk-write" \
  -H "X-CRM-ORG: 11710620000000001" \
  -F "file=@dealers.zip"
```

**Response:**
```json
{ "file_id": "{file_id_from_upload}" }
```

---

### Step 2 — Create Bulk Write Job
```
POST https://www.zohoapis.com/crm/bulk/v2/write
```
**Scope:** `ZohoCRM.bulk.CREATE` or `ZohoCRM.bulk.ALL`

**Body:**
```json
{
  "operation": "insert | update | upsert",
  "ignore_empty": true,
  "callback": {
    "url": "https://your-server.com/callback",
    "method": "post"
  },
  "resource": [{
    "type": "data",
    "module": "UPS",
    "file_id": "{file_id}",
    "find_by": "Dealer_Code",
    "field_mappings": [
      { "api_name": "Name", "index": 0 },
      { "api_name": "Dealer_Code", "index": 1, "find_by": "Dealer_Code" },
      { "api_name": "Phone", "index": 2 }
    ]
  }]
}
```

**curl:**
```bash
curl -X POST "https://www.zohoapis.com/crm/bulk/v2/write" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -d '{"operation":"insert","ignore_empty":true,"resource":[{"type":"data","module":"UPS","file_id":"{file_id}","field_mappings":[{"api_name":"Name","index":0},{"api_name":"Dealer_Code","index":1}]}]}'
```

**Response:**
```json
{
  "status": "success",
  "details": { "id": "{job_id}", "state": "ADDED" }
}
```

---

### Step 3 — Poll Job Status
```
GET https://www.zohoapis.com/crm/bulk/v2/write/{job_id}
```
**Job states:** `ADDED` → `IN PROGRESS` → `COMPLETED` | `FAILED` | `SKIPPED`

**curl:**
```bash
curl "https://www.zohoapis.com/crm/bulk/v2/write/{job_id}" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

**Response (when complete):**
```json
{
  "status": "success",
  "details": {
    "id": "{job_id}",
    "state": "COMPLETED",
    "result": {
      "download_url": "https://download.zoho.com/..."
    }
  }
}
```

---

### Step 4 — Download Results
Use `download_url` from completed job response. Returns a ZIP containing CSV with columns: mapped fields + `ID`, `Status`, `Errors`.

---

## Bulk Read API

> Export data from Zoho CRM using async jobs.

### Step 1 — Create Bulk Read Job
```
POST https://www.zohoapis.com/crm/bulk/v2/read
```
**Body:**
```json
{
  "callback": { "url": "https://your-server.com/callback" },
  "query": {
    "module": "UPS",
    "fields": ["id", "Name", "Dealer_Code", "Phone"],
    "criteria": {
      "group": [
        { "group": [{ "field": "Dealer_Type", "comparator": "equal", "value": "Retailer" }] }
      ]
    },
    "page": 1
  }
}
```

**curl:**
```bash
curl -X POST "https://www.zohoapis.com/crm/bulk/v2/read" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -d '{"query":{"module":"UPS","fields":["id","Name","Dealer_Code"],"page":1}}'
```

**Response:** `{ "status": "success", "details": { "id": "{job_id}", "state": "ADDED" } }`

---

### Step 2 — Poll Job Status
```
GET https://www.zohoapis.com/crm/bulk/v2/read/{job_id}
```
Poll until `state` = `COMPLETED`, then use `result.download_url`.

---

## Query API (COQL — SQL-like SELECT)

> Cross-Object Query Language. Use instead of JOINs.
> `POST https://www.zohoapis.com/crm/v2/coql`

**Scope:** `ZohoCRM.coql.READ` + `ZohoCRM.modules.{operation_type}`

**Request body:**
```json
{
  "select_query": "select id, Name, Dealer_Code, Phone from UPS where Dealer_Type = 'Retailer' limit 20 offset 0"
}
```

**Operators in WHERE:** `=`, `!=`, `<`, `>`, `<=`, `>=`, `in`, `not in`, `between`, `like`, `starts with`, `ends with`
**Clauses:** `where`, `order by`, `limit`, `offset`

**curl:**
```bash
curl -X POST "https://www.zohoapis.com/crm/v2/coql" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -d '{"select_query":"select id, Name, Dealer_Code from UPS limit 5"}'
```

**Response:**
```json
{
  "data": [
    { "id": "1171062000002903016", "Name": "Harshita Tiwari", "Dealer_Code": null }
  ],
  "info": { "count": 1, "more_records": false }
}
```

---

## Notification API (Webhooks)

> Subscribe to record change events.
> `POST https://www.zohoapis.com/crm/v2/actions/watch`

### Enable Notifications (Subscribe)
```
POST https://www.zohoapis.com/crm/v2/actions/watch
```
**Scope:** `ZohoCRM.notifications.CREATE`

**Body:**
```json
{
  "token": "your_verify_token",
  "url": "https://your-server.com/webhook",
  "channel_id": "1000000068001",
  "events": ["UPS.create", "UPS.edit", "UPS.delete", "UPS.name.id"]
}
```

**Event format:** `{Module}.{operation}` or `{Module}.{operation}.{field}` or `{Module}.{operation}.*.{field}`

**curl:**
```bash
curl -X POST "https://www.zohoapis.com/crm/v2/actions/watch" \
  -H "Authorization: Zoho-oauthtoken $AT" \
  -H "Content-Type: application/json" \
  -d '{"token":"abc123","url":"https://your-server.com/webhook","channel_id":"1000000068001","events":["UPS.create","UPS.edit"]}'
```

**Verify token:** Zoho sends `X-ABC` header with the token. Verify HMAC-SHA256.

---

### List Notifications
```
GET https://www.zohoapis.com/crm/v2/actions/watch?page=1&per_page=200
```
**Scope:** `ZohoCRM.notifications.READ`

**curl:**
```bash
curl "https://www.zohoapis.com/crm/v2/actions/watch?page=1&per_page=200" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

---

### Disable Notifications (Unsubscribe)
```
DELETE https://www.zohoapis.com/crm/v2/actions/watch?channel_ids={channel_id1},{channel_id2}
```
**Scope:** `ZohoCRM.notifications.DELETE`

**curl:**
```bash
curl -X DELETE "https://www.zohoapis.com/crm/v2/actions/watch?channel_ids=1000000068001" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

---

## Common Patterns

### Get Modules (List all available modules)
```
GET https://www.zohoapis.com/crm/v2/settings/modules
```
**Scope:** `ZohoCRM.settings.modules.READ`

**curl:**
```bash
curl "https://www.zohoapis.com/crm/v2/settings/modules" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

---

### Get Fields (List all fields for a module)
```
GET https://www.zohoapis.com/crm/v2/settings/fields?module={module_api_name}
```
**Scope:** `ZohoCRM.settings.fields.READ`

**curl:**
```bash
curl "https://www.zohoapis.com/crm/v2/settings/fields?module=UPS" \
  -H "Authorization: Zoho-oauthtoken $AT"
```

---

### Get Layouts
```
GET https://www.zohoapis.com/crm/v2/settings/layouts?module={module_api_name}
```

---

### Get Tags
```
GET https://www.zohoapis.com/crm/v2/tags?module={module_api_name}
POST https://www.zohoapis.com/crm/v2/{module_api_name}/{record_id}/actions/add_tags?tag_names={tag1,tag2}
```

---

## Response Codes

| code | meaning |
|---|---|
| `SUCCESS` | Operation succeeded |
| `INVALID_DATA` | Request body malformed (often missing `{"data":[...]}` wrapper) |
| `INVALID_TOKEN` | Access token expired or invalid |
| `OAUTH_SCOPE_MISMATCH` | Token lacks required scope |
| `NO_PERMISSION` | User lacks permission for this operation |
| `RECORD_NOT_FOUND` | Record ID doesn't exist |
| `DUPLICATE_ENTRY` | Duplicate record (upsert without match) |

---

## Critical Rules

1. **Always wrap body as `{"data": [...]}`** — bare arrays fail with `INVALID_DATA`
2. **Use `terminal` + `curl` for all Zoho CRM API calls** — `requests` library has 204/200 inconsistencies
3. **Use fresh access token per batch of 10 records** — token refresh rate-limits after 20+ rapid calls
4. **Token endpoint for .in DC is `accounts.zoho.in`** — NOT `accounts.zoho.com`
5. **No `redirect_uri` in refresh_token grant** — causes `invalid_client`
6. **Bulk operations are ASYNC** — submit job → poll → download results (can take minutes)
7. **Search requires `ZohoSearch.securesearch.READ` scope** — not included in `ZohoCRM.modules.ALL`