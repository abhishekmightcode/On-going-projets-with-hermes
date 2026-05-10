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

## VSS Module Field Maps (Confirmed May 2026)

### UPS — 43 Fields (GET /crm/v2/settings/fields?module=UPS)

**List API visibility:** `id` only with current token. Use COQL or single-record fetch for full data.

**Identity:** `id`, `Name`, `Dealer_Code`, `Phone`, `Email`, `Owner`, `Owner_email`
**Location:** `Address_of_the_dealer`, `Address_of_the_dealer_Street_Address`, `Address_of_the_dealer_Flat_House_No_Building_Apart`, `Address_of_the_dealer_City`, `Address_of_the_dealer_State_Province`, `Address_of_the_dealer_Country_Region`, `Address_of_the_dealer_Zip_Postal_Code`, `Address_of_the_dealer_Coordinates`, `Address_of_the_dealer_Coordinates_Latitude` (double), `Address_of_the_dealer_Coordinates_Longitude` (double), `Address_map_URL`
**Classification:** `Dealer_Type` (picklist), `Tag`
**Visits:** `Dealer_meets` (subform), `Total_visits` (formula), `Follow_up_date_and_time`, `Follow_up_notes`, `Next_Follow_up_date_and_time`, `Last_Activity_Time`
**Stock:** `Existing_Battery_stock` (integer), `Existing_UPS_stock` (integer), `Existing_High_KV_UPS_stock` (integer), `Approx_value_in_outlet` (integer), `Credit_value_with_dealer` (integer)
**Financial:** `Last_Order_Date` (date), `Last_Order_Value` (integer), `Total_Lifetime_Value` (integer)
**Email:** `Email_Opt_Out` (boolean), `Unsubscribed_Mode` (picklist), `Unsubscribed_Time`
**System:** `Created_Time`, `Modified_Time`, `Created_By`, `Modified_By`, `Record_Image`, `Locked__s`

---

### Leads — 62 Fields (GET /crm/v2/settings/fields?module=Leads)

**List API visibility:** FULL — all fields visible with current token.

**Identity:** `id`, `Salutation` (picklist), `First_Name`, `Last_Name`, `Full_Name`, `Name1`, `Company`, `Designation`
**Contact:** `Phone` (phone), `Mobile` (phone), `Email` (email), `Secondary_Email`, `Skype_ID`, `Twitter`, `Fax`
**Address:** `Address` (textarea), `Street`, `Flat_House_No_Building_Apartment_Name`, `City`, `State` (picklist), `Country` (picklist), `Zip_Code`, `Latitude` (double), `Longitude` (double), `Coordinates` (textarea)
**Status/Source:** `Lead_Source` (picklist), `Lead_Status` (picklist: Attempted to Contact, Contacted, Hot, In Progress, Junk Lead, Lost Lead, New Lead, Not Qualified, Open), `Rating` (picklist: Hot, Warm, Cold)
**Business:** `Industry` (picklist), `Annual_Revenue` (currency), `No_of_Employees` (integer), `Website` (website)
**Sales:** `Closing_date` (datetime), `Amount_closed` (integer)
**Follow-up:** `Follow_up_date_and_time`, `Follow_up_notes` (textarea), `Follow_up_subject`, `Next_Follow_up_date_and_time`, `Copy_follow_up_notes`, `Copy_follow_up_subject`
**Enrichment:** `Enrich_Status__s` (picklist), `Last_Enriched_Time__s` (datetime)
**Ads:** `ad_campaign` (text), `ad_set` (text), `leadchain0__Social_Lead_ID` (text)
**System:** `Created_Time`, `Modified_Time`, `Created_By`, `Modified_By`, `Owner`, `Last_Activity_Time`, `Record_Image`, `Tag`, `Locked__s`, `Description` (textarea), `Reason_for_junk` (textarea), `Reason_for_marking_not_qualified` (textarea), `Email_Opt_Out` (boolean), `Unsubscribed_Mode`, `Unsubscribed_Time`, `Change_Log_Time__s` (datetime)

---

### Project_Execution — 56 Fields (GET /crm/v2/settings/fields?module=Project_Execution)

**List API visibility:** FULL — all fields visible with current token.

**Identity:** `id`, `Name`, `Customer_name`, `Email`, `Phone` (phone), `Owner`, `Owner1` (email)
**Address:** `Address` (textarea), `Address_Street_Address`, `Address_Flat_House_No_Building_Apartment_Name`, `Address_City`, `Address_State_Province` (picklist), `Address_Country_Region` (picklist), `Address_Zip_Postal_Code`, `Address_Coordinates` (textarea), `Address_Coordinates_Latitude` (double), `Address_Coordinates_Longitude` (double)
**Project:** `Project_type` (picklist), `Execution_stage` (picklist), `Current_on_site_execution` (picklist), `On_site_execution_stage` (multiselectpicklist)
**Schedule:** `Date_and_time_of_execution` (datetime), `Day_1` (date), `Day_2` (date), `Day_3` (date)
**Team:** `Project_lead` (picklist), `Project_assistance_team` (multiselectpicklist), `Project_assistance_team_Day2` (multiselectpicklist), `Project_assistance_team_Day3` (multiselectpicklist)
**Installation:** `Structure_setup` (textarea), `ACDB_DCDB_setup` (textarea), `Panel_mounting` (textarea), `Inverter_UPS_Battery_installation` (textarea), `Electrical_wiring` (textarea), `Lightning_arrester` (textarea), `Unloading_on_roof` (textarea), `Material_Delivered_on_Location` (textarea), `Commissioning` (textarea), `test_muoliti_line` (textarea)
**Financials:** `Total_deal_amount` (integer), `Sanctioned_load` (double), `Advance_amount_received` (integer), `Second_installment_amount` (integer), `Second_installment_received` (picklist), `Full_payment_cleared` (picklist), `Pending_payment_amount` (integer)
**System:** `Created_Time`, `Modified_Time`, `Created_By`, `Modified_By`, `Last_Activity_Time`, `Record_Image`, `Tag`, `Locked__s`, `Unsubscribed_Mode`, `Unsubscribed_Time`

---

### Tasks — 19 Fields (GET /crm/v2/settings/fields?module=Tasks)

**List API visibility:** FULL — all fields visible with current token.

**Core:** `id`, `Subject` (text), `Status` (picklist: Not Started, In Progress, Completed, Waiting for Input, Deferred), `Priority` (picklist: High, Medium, Low, None), `Due_Date` (date)
**Details:** `Description` (textarea)
**Timing:** `Closed_Time` (datetime), `Remind_At` (ALARM), `Send_Notification_Email` (boolean), `Recurring_Activity` (RRULE)
**Relations:** `Who_Id` (lookup — Contact), `What_Id` (lookup — any CRM record e.g. Project_Execution, UPS, Deals)
**System:** `Created_Time`, `Modified_Time`, `Created_By`, `Modified_By`, `Owner`, `Last_Activity_Time`, `Tag`, `Locked__s`

---

## Critical Rules

1. **Always wrap body as `{"data": [...]}`** — bare arrays fail with `INVALID_DATA`
2. **Use `terminal` + `curl` for all Zoho CRM API calls** — `requests` library has 204/200 inconsistencies
3. **Use fresh access token per batch of 10 records** — token refresh rate-limits after 20+ rapid calls
4. **Token endpoint for .in DC is `accounts.zoho.in`** — NOT `accounts.zoho.com`
5. **No `redirect_uri` in refresh_token grant** — causes `invalid_client`
6. **Bulk operations are ASYNC** — submit job → poll → download results (can take minutes)
7. **Search requires `ZohoSearch.securesearch.READ` scope** — not included in `ZohoCRM.modules.ALL`