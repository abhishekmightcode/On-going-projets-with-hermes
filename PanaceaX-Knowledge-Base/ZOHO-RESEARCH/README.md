# ZOHO CRM — Complete Developer Reference
## 237 Pages Compiled from www.zoho.com/crm/developer/docs

**Compiled by:** Hermes Agent for Abhishek Sharma  
**Date:** May 2026  
**Purpose:** AI-Native CRM Build | Solar Solutions (Bangalore)

---

## FILES IN THIS COLLECTION

| File | Contents |
|------|----------|
| `PART-1-API-V8-OVERVIEW.md` | API overview, Composite API, Bulk APIs |
| `PART-2-RECORDS-CRUD.md` | Record CRUD, Search, Related Records |
| `PART-3-BULK-COMPOSITE-APIs.md` | COQL, Bulk Read/Write |
| `PART-4-METADATA-APIs.md` | Module, Field, Layout, Custom View APIs |
| `PART-5-USER-TERRITORY-APIs.md` | User, Profile, Role, Territory, Notification APIs |
| `PART-6-DEVELOPER-TOOLS.md` | Functions, Client Script, Widgets, SDKs, Mobile |
| `PART-7-ZIA-AI.md` | Zia AI, Forecasting, Agents |
| `PART-8-INTEGRATIONS-SECURITY.md` | Integrations, Security, Compliance |

---

## HOW TO SEARCH

Use `grep` or any text editor:
```bash
grep -r "workflow" .
grep -r "Deluge" .
grep -r "Client Script" .
```

---

## KEY API ENDPOINTS

### Authentication
- **OAuth 2.0** — `https://accounts.zoho.com/oauth/v2/auth`
- **Token Refresh** — `https://accounts.zoho.com/oauth/v2/token`

### Core
- **Get Records** — `GET /crm/v8/{module}`
- **Insert Records** — `POST /crm/v8/{module}`
- **Update Records** — `PUT /crm/v8/{module}/{id}`
- **Delete Records** — `DELETE /crm/v8/{module}/{id}`
- **Search** — `GET /crm/v8/{module}/search`

### Metadata
- **Get Modules** — `GET /crm/v8/settings/modules`
- **Get Fields** — `GET /crm/v8/settings/fields?module={module}`
- **Get Layouts** — `GET /crm/v8/settings/layouts?module={module}`

### Bulk Operations
- **Bulk Read** — `POST /crm/v8/bulk-read`
- **Bulk Write** — `POST /crm/v8/bulk-write`
- **COQL Query** — `POST /crm/v8/coql`

---

## ZOHO CRM MODULES

Standard Modules:
- Leads, Deals, Contacts, Accounts
- Campaigns, Tasks, Events, Calls
- Solutions, Products, Vendors, Quotes
- SalesOrders, PurchaseOrders, Invoices
- Custom Modules (unlimited)

---

## DELUGE SCRIPT REFERENCE

```deluge
// Fetch records
records = zoho.crm.getRecords("Leads", 1, 200, {"customfield": "value"});

// Insert record
resp = zoho.crm.insertRecord("Leads", {"Last_Name": "Test", "Email": "test@example.com"});

// Invoke URL
response = invokeURL([
	url: "https://api.example.com/endpoint",
	type: "POST",
	parameters: {"key": "value"},
	headers: {"Authorization": "Bearer token"}
]);
```

---

## CLIENT SCRIPT REFERENCE

```javascript
// On form load
ZCRM.ClientScript.onLoad(function(event) {
    console.log("Form loaded");
});

// On field change
ZCRM.ClientScript.onFieldChange(function(event) {
    var field = event.field;
    console.log("Field changed:", field);
});

// Get field value
var value = ZCRM.Form.getField("Field_Label").getValue();
```

---

*This is machine-compiled from Zoho's public documentation. 
Content belongs to Zoho Corporation. For official docs visit: www.zoho.com/crm/developer/docs*
