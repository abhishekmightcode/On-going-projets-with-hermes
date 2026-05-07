# Master Plan V2 — UPS Field App with Google Forms + n8n + Sheets
## VSS — V Sustain Solar Solutions

---

## 1. Architecture Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                     FIELD EMPLOYEE (Mobile)                        │
└────────────────────────────┬─────────────────────────────────────┘
                             │
                             ▼
┌──────────────────────────────────────────────────────────────────┐
│                FIELD APP (GitHub Pages, public)                   │
│                                                                  │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────────┐  │
│  │ Dealer List  │───►│ Dealer Detail │───►│  "Open Form" btn │  │
│  │ (from Sheet) │    │   Modal       │    │  (pre-filled)    │  │
│  └──────────────┘    └──────────────┘    └────────┬─────────┘  │
└─────────────────────────────────────────────────────┼────────────┘
                                                      │
                              ┌──────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────────┐
│                    GOOGLE FORM (pre-filled)                       │
│   Fields: Dealer Name | Record ID | Phone | Stage | Notes | Photos
│   URL: https://docs.google.com/forms/d/e/...                      │
└────────────────────────────┬─────────────────────────────────────┘
                             │
                             ▼
┌──────────────────────────────────────────────────────────────────┐
│                    GOOGLE SHEET (responses)                       │
│   Columns: Timestamp | Dealer Name | Record ID | Phone |        │
│            Stage | Notes | Photo URLs | Submitted By             │
└────────────────────────────┬─────────────────────────────────────┘
                             │
              ┌──────────────┴──────────────┐
              │                             │
              ▼                             ▼
┌─────────────────────────┐     ┌─────────────────────────┐
│  n8n Workflow           │     │  Google Apps Script     │
│  Trigger: Sheet Row     │     │  (Zoho → Sheet sync)    │
│  New                    │     │  Pulls dealer list       │
│  ─────────────────────  │     │  from Zoho CRM           │
│  1. Parse row data      │     │  Runs on edit/update    │
│  2. Build Zoho payload  │     │  Every 5 mins (time-dr) │
│  3. PATCH Zoho CRM      │     └─────────────────────────┘
└─────────────────────────┘

         ┌─────────────────┐
         │    ZOHO CRM      │
         │  (UPS Module)    │
         │  Updated!        │
         └─────────────────┘
```

---

## 2. Component Breakdown

### 2.1 Field App (GitHub Pages)
**Public URL:** `https://abhishekmightcode.github.io/vss-ups-field-app/`

**What it does:**
1. Fetches dealer list from Google Sheet (Apps Script published URL)
2. Shows cards: Dealer Name, Phone, Dealer Code, Last Visit
3. Filter chips: All / City / Dealer Type / Date range
4. Search bar
5. Tap card → bottom sheet modal with dealer details
6. "Update Dealer" button → opens Google Form pre-filled with:
   - Dealer Name
   - Record ID (hidden field)
   - Phone
   - Current Stage (Dealer_meets subform entry)
   - Notes
   - Photo upload

**No auth.** App is fully public. Anyone with the link can see the dealer list.

**Stack:** Vanilla JS + CSS (same dark theme as Executionflow), hosted on GitHub Pages

---

### 2.2 Google Form

**URL:** `https://docs.google.com/forms/d/e/1FAIpQLSe.../viewform`

**Fields:**

| Field Label | Entry ID | Type | Notes |
|------------|----------|------|-------|
| Dealer Name | `entry.XXXXX` | text (pre-filled, read-only) | from URL param |
| Record ID | `entry.XXXXX` | short text (hidden) | Zoho CRM record ID |
| Phone | `entry.XXXXX` | text (pre-filled) | |
| Visit Stage | `entry.XXXXX` | dropdown | New Visit / Follow-up / Site Survey / Order Taken / Installation / AMC |
| Notes | `entry.XXXXX` | paragraph | |
| Photos | `entry.XXXXX` | file upload | stored in submitter's Google Drive |
| Submitted By | `entry.XXXXX` | text | employee name/ID |

**Pre-fill logic (built in app.js):**
```
form URL + ?usp=pp_url
  &entry.DEALER_NAME=John Doe
  &entry.RECORD_ID=1171062000000994001
  &entry.PHONE=+919448043392
```

---

### 2.3 Google Sheet

**Sheet name:** `UPS Dealer Visits`

**Columns:**

| Column | Source | Updated By |
|--------|--------|------------|
| Timestamp | Google Form | Auto |
| Dealer Name | Form | Employee |
| Record ID | Form (hidden) | Employee |
| Phone | Form | Employee |
| Visit Stage | Form | Employee |
| Notes | Form | Employee |
| Photo URLs | Form | Google (Drive link) |
| Submitted By | Form | Employee |
| Sync Status | n8n | n8n |
| Zoho CRM Status | n8n | n8n |

---

### 2.4 Google Apps Script (Zoho → Sheet Sync)

**Purpose:** Keep the dealer list in Google Sheet in sync with Zoho CRM UPS module.

**Trigger:** Time-based, every 5 minutes

**What it does:**
1. Refresh Zoho OAuth token
2. GET all UPS records from Zoho CRM
3. Map to sheet columns
4. Clear old data, write fresh (or use SET values to update in place)

**Data pulled from Zoho:**

| Zoho Field | Sheet Column |
|-----------|--------------|
| Name | Dealer_Name |
| Phone | Phone |
| Dealer_Code | Dealer_Code |
| Dealer_Type | Dealer_Type |
| City | City |
| State | State |
| Total_Lifetime_Value | Lifetime_Value |
| Last_Order_Date | Last_Order |
| Total_visits | Total_Visits |
| Next_Follow_up | Next_Followup |
| Owner_email | Assigned_To |
| id | Record_ID (hidden key) |

---

### 2.5 n8n Workflow

**Trigger:** Google Sheets — "When row is added/updated"

**Steps:**

```
[Sheet Trigger: new row]
       │
       ▼
[Code Node: Parse row]
  - Extract Record ID, Stage, Notes, Photo URLs
  - Validate Record ID format
       │
       ▼
[Code Node: Build Zoho payload]
  - Map stage to Zoho subform field structure
  - Build Dealer_Meets subform entry:
    {
      "Visit_Date": "{{$now}}",
      "Stage": "Follow-up",
      "Notes": "...",
      "Photo_URLs": ["https://drive.google.com/..."],
      "Submitted_By": "field_employee_name"
    }
       │
       ▼
[HTTP Request: PATCH Zoho CRM UPS]
  - Method: PATCH
  - URL: https://www.zohoapis.in/crm/v2/UPS/{record_id}
  - Body: { "data": [{ "Dealer_Meets": [new entry] }] }
       │
       ▼
[Code Node: Update Sync Status]
  - Write "Synced ✓" or "Failed: error" to Sheet
```

---

## 3. Data Flow — Step by Step

### Step 1: Dealer List Sync (Zoho → Sheet → App)
```
Zoho CRM (UPS module)
    │ (Apps Script, every 5 mins)
    ▼
Google Sheet (UPS Dealer Visits)
    │ (Apps Script publishes as web app)
    ▼
Field App (page load / pull-to-refresh)
```

### Step 2: Field Employee Submits Visit
```
Employee opens app → sees dealer list
    │
    │ taps dealer card
    ▼
Bottom sheet opens with dealer details
    │
    │ taps "Update Dealer" button
    ▼
Google Form opens (pre-filled with name, phone, record ID)
    │
    │ employee fills stage, notes, photos
    │ submits form
    ▼
Google Form → Google Sheet (new row)
    │
    │ (automatic trigger)
    ▼
n8n workflow fires
    │
    │ parses row, builds subform entry
    ▼
n8n → Zoho CRM PATCH (upsert Dealer_Meets entry)
    │
    │ n8n updates Sheet sync status column
    ▼
Done ✓
```

---

## 4. File Structure

```
vss-ups-field-app/
├── index.html           # Main app shell
├── css/
│   └── style.css        # Dark theme (from Executionflow)
├── js/
│   ├── config.js        # Sheet URL, form URL, form entry IDs
│   ├── app.js           # Main logic: load, search, filter, modal
│   └── form-builder.js  # Pre-fill form URL builder
├── manifest.json        # PWA manifest (optional)
└── README.md
    │
    ├── SHEET_SETUP.md   # Sheet creation + column guide
    ├── FORM_SETUP.md    # Google Form creation + entry IDs guide
    ├── APPS_SCRIPT.md   # Apps Script code (Zoho → Sheet sync)
    └── N8N_WORKFLOW.md  # n8n workflow JSON + setup guide
```

---

## 5. Implementation Sequence

### Step 1: Create the Web App (1 hour)
- [ ] Create GitHub repo `vss-ups-field-app`
- [ ] Copy Executionflow HTML/CSS/JS structure
- [ ] Adapt config.js for UPS fields (dealer list columns)
- [ ] Build dealer list → modal → form open flow
- [ ] Test with static/mock data first
- [ ] Deploy to GitHub Pages

### Step 2: Create Google Sheet + Apps Script (30 mins)
- [ ] Create sheet with columns as defined above
- [ ] Create Apps Script project
- [ ] Write script: Zoho auth → fetch UPS → write to Sheet
- [ ] Deploy Apps Script as web app (public)
- [ ] Update config.js with sheet API URL
- [ ] Test data flow: Zoho → Sheet

### Step 3: Create Google Form (20 mins)
- [ ] Create form with fields as defined above
- [ ] Publish form, get public URL
- [ ] Get all entry IDs (from form URL or inspect)
- [ ] Update config.js with form URL + entry IDs
- [ ] Test pre-fill: open form with params

### Step 4: Create n8n Workflow (30 mins)
- [ ] Create new n8n workflow
- [ ] Add Google Sheets trigger node
- [ ] Add Code node (parse row)
- [ ] Add Code node (build Zoho payload)
- [ ] Add HTTP Request node (PATCH Zoho CRM)
- [ ] Add Code node (update sync status)
- [ ] Activate + test with a real form submission

### Step 5: End-to-End Test (30 mins)
- [ ] Submit real form entry
- [ ] Check Sheet receives data
- [ ] Check n8n fires
- [ ] Check Zoho CRM updated with subform entry
- [ ] Fix any issues

---

## 6. What I Need From You (Before Implementation)

**Must have:**

1. **Google Sheet URL** — create a blank Google Sheet and give me the URL
   - Sheet should be in your Google Drive / owned by you
   - I'll give you the Apps Script to paste in

2. **Google Form URL** — create a Google Form with these fields:
   - Dealer Name (text)
   - Record ID (short text — will be hidden)
   - Phone (text)
   - Visit Stage (dropdown — options: New Visit, Follow-up, Site Survey, Order Taken, Installation, AMC)
   - Notes (paragraph)
   - Photos (file upload)
   - Submitted By (text)
   - Give me the form's public URL

3. **Form Entry IDs** — after creating the form, go to:
   - Open form → three dots menu → Get pre-filled link
   - Or: fill the form once yourself, then check the submitted sheet
   - I need the `entry.XXXXX` IDs for each field

4. **n8n credentials:**
   - Do you have n8n cloud access? (your `vsustainsolar.app.n8n.cloud`?)
   - Or is it self-hosted?
   - Either way I need the webhook URL to put in the sheet

**Nice to have:**

5. **Employee names list** — how many field employees? I'll add a dropdown or they can type their name

---

## 7. Zoho CRM Subform: Dealer_Meets

Based on the UPS module structure we pulled earlier, the `Dealer_Meets` subform stores visit records per dealer. Each submission from Google Form creates ONE subform row in Zoho.

**Subform field mapping (from Sheet row → Zoho subform entry):**

| Sheet Column | Zoho Subform Field | Type |
|-------------|-------------------|------|
| Timestamp | Visit_Date | DateTime |
| Visit Stage | Stage | Picklist |
| Notes | Notes | Text |
| Photo URLs | Photo_URL | URL |
| Submitted By | Field_Employee | Text |

**Note:** The exact subform field names (API names) need to be confirmed from the Zoho CRM layout. I can extract these once the rate limit clears.

---

## 8. Apps Script: Zoho → Sheet Sync (Pseudocode)

```javascript
// Zoho CRM config
const ZOHO_CONFIG = {
  client_id: '1000.3JWYP8QJM6S3CIGPPOQ5R8VOUFCQ9Z',
  refresh_token: '1000.2034b714368b7f024a7d98a0746442cd.63b5dfcedc97dd27d3bebaf7c71b734e',
  token_url: 'https://accounts.zoho.in/oauth/v2/token',
  api_base: 'https://www.zohoapis.in/crm/v2'
};

// Sheet config
const SHEET_NAME = 'UPS Dealer Visits';
const SHEET_HEADERS = ['Timestamp','Dealer Name','Record ID','Phone',
                        'Dealer Type','City','State','Lifetime Value',
                        'Last Order','Total Visits','Next Follow-up',
                        'Assigned To'];

// Main sync function (runs every 5 mins via time trigger)
function syncZohoToSheet() {
  const token = getAccessToken();
  const records = fetchAllUPSRecords(token);
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(SHEET_NAME);
  
  // Clear data rows (keep headers)
  sheet.getRange(2, 1, sheet.getLastRow(), SHEET_HEADERS.length).clearContent();
  
  // Write new data
  records.forEach((record, i) => {
    const row = mapRecordToRow(record);
    sheet.getRange(i + 2, 1, 1, SHEET_HEADERS.length).setValues([row]);
  });
}
```

---

## 9. n8n Workflow Overview

```
Node 1: Google Sheets Trigger
  - Watch for: "Row added"
  - Sheet: UPS Dealer Visits

Node 2: Code — Parse Row
  - const stage = $json["Visit Stage"];
  - const recordId = $json["Record ID"];
  - const notes = $json["Notes"];
  - const photos = $json["Photo URLs"];
  - const employee = $json["Submitted By"];
  - return { recordId, stage, notes, photos, employee };

Node 3: HTTP Request — PATCH Zoho UPS
  - Method: PATCH
  - URL: https://www.zohoapis.in/crm/v2/UPS/{recordId}
  - Auth: OAuth2 (refresh token flow)
  - Body:
    {
      "data": [{
        "Dealer_Meets": [{
          "Visit_Date": "{{ $json.visit_date }}",
          "Stage": "{{ $json.stage }}",
          "Notes": "{{ $json.notes }}",
          "Photo_URL": "{{ $json.photos }}",
          "Field_Employee": "{{ $json.employee }}"
        }]
      }]
    }

Node 4: Code — Update Sync Status
  - sheet.updateCell(row, 'Sync Status', 'Synced ✓')

Node 5 (error path): Code — Update Sync Status (Error)
  - sheet.updateCell(row, 'Sync Status', 'Failed: ' + error.message)
```

---

## 10. Timeline

| Step | Who Does It | Time |
|------|------------|------|
| 1. Create GitHub repo + web app | Me | 1 hour |
| 2. Create Google Sheet | You | 5 mins |
| 3. Create Google Form | You | 10 mins |
| 4. Get entry IDs | You | 5 mins |
| 5. Apps Script (Zoho→Sheet) | Me (give you code) | 10 mins setup |
| 6. n8n workflow | Me (give you JSON) | 10 mins setup |
| 7. End-to-end test | You + Me | 30 mins |

**Total: ~2 hours active work, mostly on your side (Sheet + Form creation)**

---

*Status: Ready to implement. Awaiting Sheet URL, Form URL, and Entry IDs from user.*
