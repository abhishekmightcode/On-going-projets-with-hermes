# Master Plan V1.5 — Field Employee CRM Sync App
## Solar-Bangalore × Executionflow Reference Analysis

---

## 1. Executionflow App — Full Analysis

**Repo:** `vsustainsolar/Executionflow`
**What it does:** Mobile-first SPA that fetches solar projects from a Google Sheet (via Apps Script), shows them in a list, and lets field employees update execution/onsite stages.

**Architecture:**
```
Field App → Google Apps Script Web App → Google Sheet ← Zoho Flow/n8n ← Zoho CRM
                ↑
                └── Execution stage update → n8n webhook
                                              ↓
On-site tab: Open Google Form (pre-filled) → Google Sheet → n8n → Zoho CRM
```

**What works well:**
- Dark theme, mobile-first UI with bottom-sheet modal
- Filter chips (status + lead), search
- Stage tracker with done/current/remaining states
- GPS capture on every submit
- Config-driven (stages, columns, form entry IDs all in config.js)
- Offline-capable thinking via n8n retries

**Limitations:**
- Data always goes through Google Sheets (extra hop)
- Photo upload requires Google Form + sheet processing
- No direct CRM update for text fields (all routed through n8n)
- No offline queue in the app itself
- Single-tenant (hardcoded n8n webhook + form URL)

---

## 2. New Architecture (Based on Executionflow + Your Requirements)

```
┌─────────────────────────────────────────────────────────────┐
│                    FIELD EMPLOYEE (Mobile)                   │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                  FIELD APP (Vanilla JS SPA)                  │
│                                                              │
│  Lead List ──► Lead Detail Modal ──► Form ──► Submit        │
│       │                                     │               │
│       │                              ┌──────┴──────┐        │
│       │                              │             │        │
│       │                    Text/Number fields   Photo       │
│       │                              │             │        │
│       │                              │      ┌──────▼─────┐  │
│       │                              │      │ Compress   │  │
│       │                              │      │ to ≤1MB    │  │
│       │                              │      └──────┬─────┘  │
│       │                              │             │        │
└───────┼──────────────────────────────┼─────────────┼────────┘
        │                              │             │
        │                         ┌────▼────┐   ┌─────▼──────┐
        │                         │ Zoho CRM │   │Google Drive│
        │                         │   API    │   │  Upload   │
        │                         │(direct)  │   │ (Drive API)│
        │                         └────┬────┘   └─────┬──────┘
        │                              │             │
        │                              │    Drive link saved
        │                              │    to CRM field
        │                              ▼             │
        │                         ┌─────────────┐    │
        │                         │ Zoho CRM    │◄───┘
        │                         │ Record      │
        │                         └─────────────┘
        │
        ▼ (optional fallback)
   ┌─────────┐
   │   n8n   │ ← only if Zoho Flow triggers needed post-submit
   └─────────┘
```

---

## 3. Key Differences From Executionflow

| Aspect | Executionflow | New App |
|--------|--------------|---------|
| Data source | Google Sheet ( Apps Script) | **Zoho CRM API directly** |
| Text field updates | n8n → Zoho Flow | **Direct Zoho CRM API** |
| Photo upload | Google Form → Sheet → n8n | **Direct Google Drive API** |
| Offline queue | None | **IndexedDB queue** |
| Auth | None (app is public) | **Zoho OAuth2 PKCE** |
| n8n usage | All updates | **Only for post-submit triggers** |

---

## 4. Tech Stack — Confirmed

| Layer | Choice | Why |
|-------|--------|-----|
| Frontend | **Vanilla JS** (no framework) | Proven in Executionflow, fast, no build |
| Styling | **Vanilla CSS** (dark theme like Executionflow) | Keep consistency with existing brand |
| Data source | **Zoho CRM REST API v2** | Direct, no sheet hop |
| Photo storage | **Google Drive API** | Employees have Google accounts; Drive API is simple REST |
| Offline | **IndexedDB** (raw API, no library) | Lightweight, proven pattern |
| Backend | **None for core flow** | App is fully client-side |
| Proxy | **Tiny Netlify Edge/Vercel function** | Only for secure token refresh (httpOnly cookie) |

---

## 5. Field Mapping — Project_Execution Module

Based on what we pulled from the VSS CRM earlier. Fields available:

| CRM Field | Form Field Type | Notes |
|-----------|----------------|-------|
| Customer_Name | display (read-only) | From CRM |
| Phone | display (read-only) | From CRM |
| Address | display (read-only) | From CRM |
| Project_type | display (read-only) | On grid / Hybrid / Off grid |
| Sanctioned_load | number input | in kW |
| Execution_stage | dropdown | 8 stages (see Executionflow) |
| Day_1, Day_2, Day_3 | date pickers | |
| Project_lead | display (read-only) | |
| Project_assistance_team | text (multi-select) | |
| ACDB_DCDB_setup | checkbox | |
| Structure_setup | checkbox | |
| Panel_mounting | checkbox | |
| Electrical_wiring | checkbox | |
| Inverter_UPS_Battery | checkbox | |
| Lightning_arrester | checkbox | |
| Earthing | checkbox | |
| Advance_amount_received | currency | |
| Second_installment_amount | currency | |
| Second_installment_received | date | |
| Total_deal_amount | currency (read-only) | |
| Full_payment_cleared | checkbox | |
| Pending_payment_amount | currency | |

**On-site stages (checklist items) → would be stored in CRM or Drive as a checklist JSON**

---

## 6. What I Still Need From You

Before I can write **Master Plan V2 (Implementation Version)**:

### Critical (must have):

**A. Zoho CRM — Which module does the form write to?**
- Option 1: `Project_Execution` (the custom module we already studied — 13 records)
- Option 2: `Leads` (standard Zoho module)
- Option 3: Something else?

**B. Which specific fields from the module should appear on the form?**
I'll need a list like: `Field_Display_Name | API_Field_Name | Field_Type`
You can give me this as a text list or screenshot of the CRM layout.

**C. Google Cloud OAuth credentials:**
1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Create a project (or use existing)
3. Enable **Google Drive API**
4. Create **OAuth Client ID** (Web application type)
5. Add redirect URI: `http://localhost:8080` (dev) + your production URL later
6. Give me the **Client ID**

**D. Photo fields in CRM:**
Which CRM text field should store the Google Drive photo link? (I saw `"Photo URLs"` field type but need the exact API name)

### Important (should have):

**E. Reference web app URL**
If your Executionflow app is deployed somewhere live, give me the URL so I can see it in action.

**F. n8n usage scope**
In the new architecture, n8n is only for post-submit triggers. Does your current n8n workflow do anything beyond updating CRM? (e.g., send WhatsApp messages, update accounting software) — this tells me what to preserve.

---

## 7. What's Clear From Executionflow

✅ Mobile-first dark SPA pattern works great — we'll use it as UI template
✅ Config-driven stages/form definitions — we'll replicate this pattern
✅ GPS capture on every submit — we'll keep it
✅ Pre-filled Google Form pattern — **replaced by direct Drive upload**
✅ n8n webhook for stage updates — **replaced by direct CRM API call**
✅ Filter chips for leads — **adapted for Zoho CRM owner filter**

---

## 8. Phased Implementation Plan

### Phase 1: Foundation (2–3 hours)
- [ ] New project repo setup
- [ ] HTML structure (bottom-sheet modal, lead list, form)
- [ ] CSS theme (dark, mobile-first — based on Executionflow)
- [ ] Zoho OAuth2 PKCE login flow
- [ ] Lead list from CRM (GET /Project_Execution)
- [ ] Lead detail modal with read-only fields

### Phase 2: Form & Direct CRM Updates (2 hours)
- [ ] Dynamic form renderer (config-driven like Executionflow)
- [ ] Checkbox, date, number, dropdown field types
- [ ] Direct Zoho CRM PATCH for execution stage updates
- [ ] Submission success/error UX

### Phase 3: Photo Upload (2 hours)
- [ ] Camera capture component (input[capture])
- [ ] Client-side image compression (canvas resize to 1920px, quality 0.7)
- [ ] Google Drive upload via Drive API v3
- [ ] Drive link → CRM field update

### Phase 4: Offline Support (1 hour)
- [ ] IndexedDB queue for submissions
- [ ] Sync manager with retry logic
- [ ] "Pending uploads" indicator
- [ ] Auto-sync on reconnect

### Phase 5: Polish & Deploy (1 hour)
- [ ] Loading skeletons
- [ ] Error handling (rate limits, token expiry)
- [ ] Deploy to Netlify
- [ ] PWA manifest

---

*Status: Awaiting items A–F from user before Master Plan V2*
*Executionflow reference: fully analyzed and incorporated*
