# Master Plan V1 — Field Employee CRM Sync App
## Solar-Bangalore Project

---

## 1. What We Are Building

A **mobile-first web app** for field employees of a solar company to:
1. See their assigned leads from Zoho CRM
2. Click a lead → open a dynamic form
3. Fill field data (text, numbers, dropdowns, checkboxes)
4. **Attach photos** (site photos, meter readings, installation shots)
5. Submit → data goes **directly to Zoho CRM** via API
6. Photos uploaded to **Google Drive** → link stored in CRM

**Target users:** Field installation engineers, site surveyors, sales support staff
**Device:** Mobile-first (phones, some tablets)
**Environment:** Works on 2G–4G weak connections

---

## 2. Current Architecture (As-Is)

```
Field Employee
     │
     ▼
[Web App] ──────► Zoho CRM API (text/number fields) ✓ works
     │
     │ (for photos)
     ▼
[Google Form] ← Record ID auto-filled
     │
     ▼
[Google Sheet] ← stores responses
     │
     ▼
[Zoho CRM] ← Sheet data mapped via n8n/Zoho Flow
     │
     ▼
[Google Drive] ← photos stored here, links extracted
```

**Problems with current architecture:**
- 3-step process for every photo (form → sheet → n8n → CRM)
- Google Forms dependency: employees need to switch between app and browser
- n8n/Zoho Flow adds latency and maintenance overhead
- No offline support — weak networks = lost submissions
- No versioning/audit trail on submitted data
- Hard to scale to multiple field types

---

## 3. Reference App Analysis

**Reference repo:** `zoho-crm-ui-blueprint` (abhishekmightcode/zoho-crm-ui-blueprint)

What it contains:
- Single HTML file (`index.html`, ~3100 lines)
- Full CRM-style UI: sidebar, module tabs, search, list views, detail panels
- CSS-heavy, no framework (vanilla JS)
- Hardcoded sample data (not API-driven)
- Static mockups of Leads, Deals, Accounts, Tasks modules

**What we can reuse:**
- UI component patterns (sidebar, module tabs, card layouts)
- Color scheme and design tokens
- Form field styling
- Mobile-responsive layout

**What needs to change:**
- Replace hardcoded data with live Zoho CRM API calls
- Strip out unnecessary modules (keep only Leads + one detail form)
- Add photo capture/upload capability
- Add offline queue and sync mechanism
- Replace mock detail view with dynamic field rendering

---

## 4. Preferred Architecture (To-Be)

```
┌─────────────────────────────────────────────────────────────┐
│                     FIELD EMPLOYEE                          │
│                  (Mobile Browser)                           │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                    WEB APP (SPA)                            │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌─────────────┐ │
│  │ Lead List│  │Form Render│  │Photo Capt│  │ Offline Queue│ │
│  │(from CRM)│  │ (dynamic) │  │(camera)  │  │(IndexedDB)  │ │
│  └──────────┘  └──────────┘  └──────────┘  └─────────────┘ │
│          │              │           │              │        │
│          └──────────────┴───────────┴──────────────┘        │
│                             │                                │
│                    ┌────────▼────────┐                       │
│                    │  Sync Manager  │                       │
│                    │ (queues,retry) │                       │
│                    └────────┬────────┘                       │
└─────────────────────────────┼───────────────────────────────┘
                              │
              ┌───────────────┴───────────────┐
              │                               │
              ▼                               ▼
   ┌─────────────────────┐         ┌─────────────────────┐
   │    ZOHO CRM API     │         │   GOOGLE DRIVE API  │
   │  (text field data)  │         │  (photo upload)     │
   └─────────────────────┘         └─────────────────────┘
```

**Flow for text/number fields:**
```
Web App → Zoho CRM API → CRM Record Updated ✓
```

**Flow for photo fields:**
```
Web App → Google Drive API → Photo stored
                             │
                             ▼
              Web App → Zoho CRM API → CRM field = Drive link ✓
```

---

## 5. Tech Stack Decision

| Layer | Choice | Reason |
|-------|--------|--------|
| Frontend | **Vite + Vanilla JS** (or Preact for small bundle) | No framework overhead, fast load on 2G, simple deployment |
| Styling | **Tailwind CSS** (CDN) | Mobile-first, small CSS bundle via CDN |
| Storage (offline) | **IndexedDB** (Dexie.js wrapper) | Queues submissions when offline, auto-syncs |
| Photo upload | **Google Drive API** (的直接上传) | User's own Drive = no extra storage costs |
| CRM sync | **Zoho CRM REST API v2** | Already proven working via curl/execute_code |
| Auth | **Zoho OAuth 2.0** (refresh token flow) | One login for all modules |
| Backend (optional) | **Netlify/Vercel edge functions** | Only if we need to proxy tokens |

**Stack NOT chosen and why:**
- Firebase Storage: extra account, no native Drive integration
- AWS S3: complex permissions for field employees
- Cloudinary: extra dependency, Drive is free and familiar
- Zoho WorkDrive: photo upload API more complex than Drive
- n8n: adds a middle layer we want to eliminate

---

## 6. Photo Upload Architecture (Key Decision)

### Why Google Drive over direct Zoho upload:
1. **Zoho's file upload** requires `multipart/form-data` with session-based authentication — extremely difficult from a browser SPA
2. **Google Drive API** supports direct REST upload with just an API key + OAuth
3. Field employees likely already have a Google account
4. Drive links are public by default → perfect for CRM field storage

### Photo upload flow:
1. Employee takes photo in web app (using `<input type="file" capture="environment">`)
2. Photo compressed client-side (max 1MB, 1920px wide)
3. Uploaded directly to **specific Google Drive folder** via Drive API
4. Drive returns **webContentLink** (public shareable link)
5. WebContentLink saved into a CRM text field

### Drive folder structure:
```
/SolarFieldApp/
  /2026-05-07/
    LEAD-1171062000000994001_photo1.jpg
    LEAD-1171062000000994001_photo2.jpg
```

---

## 7. Offline Strategy

**Problem:** Field employees work in basements, rural sites, weak coverage areas.

**Solution: IndexedDB Queue**

```
Submit button clicked
        │
        ▼
Is online? ──No──► Save to IndexedDB
        │                   │
       Yes                  ▼
        │           "Pending Sync" badge
        ▼                  appears in UI
  Zoho API call
        │
   Success? ──No──► Save to IndexedDB
        │               (with retry count)
       Yes
        │
        ▼
  CRM updated ✓
  Remove from queue
```

- Queue processes every 30 seconds when online
- Visual indicator shows pending uploads
- Manual "Sync Now" button available
- Max 3 retries before flagging as failed

---

## 8. Security Architecture

**API Token Handling:**
- Access tokens stored in **memory only** (never localStorage)
- Refresh tokens stored in **httpOnly cookie** (set by a tiny backend proxy)
- Token refresh happens automatically on 401

**Employee Authentication:**
- Each field employee logs in with their **Zoho account**
- OAuth2 PKCE flow (no client secret in browser)
- Role-based: employees can only see their assigned leads

**Drive Access:**
- App requests Drive API scope: `https://www.googleapis.com/auth/drive.file`
- Each photo uploaded to a folder owned by the employee
- App does NOT request full Drive access

**CRM Data:**
- Employees see only their assigned leads (Zoho filter by Owner)
- No write access to other employees' records

---

## 9. Key Modules & File Structure

```
field-app/
├── index.html              # Main entry
├── css/
│   └── styles.css          # All styles
├── js/
│   ├── app.js              # Main app logic, router
│   ├── api/
│   │   ├── zoho.js         # Zoho CRM API wrapper
│   │   ├── drive.js        # Google Drive API wrapper
│   │   └── auth.js         # OAuth2 PKCE flow
│   ├── db/
│   │   └── offline.js      # IndexedDB via Dexie.js
│   ├── sync/
│   │   └── sync-manager.js # Queue processor, retry logic
│   ├── ui/
│   │   ├── lead-list.js    # Lead list component
│   │   ├── lead-form.js    # Dynamic form renderer
│   │   └── photo-capture.js # Camera/gallery handler
│   └── utils/
│       ├── image.js        # Compression, resize
│       └── config.js       # API keys, endpoints
├── manifest.json           # PWA manifest
└── sw.js                   # Service worker (optional)
```

---

## 10. API Flow Diagrams

### Lead Fetch Flow:
```
1. Employee opens app
2. Check: is token valid?
   No → redirect to Zoho OAuth login
   Yes → continue
3. GET /crm/v2/Leads?owner={employee_id}&per_page=50
4. Render lead cards (name, phone, stage, last visit)
5. Show "Last synced: X mins ago"
```

### Form Submit Flow:
```
1. Employee taps lead → form opens
2. Form fields loaded from CRM layout (or hardcoded config)
3. Employee fills fields + attaches photos
4. Submit clicked
5. For each photo:
   a. Compress to ≤1MB
   b. Upload to Drive → get webContentLink
   c. Store link in form data
6. POST /crm/v2/Leads/{id} with all field data
7. Show success/error
8. If offline → queue and show "Saved offline"
```

---

## 11. Zoho CRM Fields to Capture (Per Lead)

**To be confirmed by user. Based on UPS + Project_Execution modules, likely candidates:**
- Site address
- Current meter reading (number)
- Panel count (number)
- Battery status (picklist: Good/Fair/Poor/Replace)
- Installation photo URLs (multi-line text)
- Site condition notes (textarea)
- Next follow-up date
- Visit timestamp
- GPS coordinates (from browser)

---

## 12. Failure Points & Mitigations

| Failure | Likelihood | Impact | Mitigation |
|---------|-----------|--------|------------|
| Token expires mid-session | Medium | High | Auto-refresh on 401, retry original request |
| Photo upload to Drive fails | Medium | Medium | Queue photo, submit text first, retry photo later |
| CRM API 429 rate limit | Medium | Low | Exponential backoff (1s, 2s, 4s, 8s...) |
| Offline for hours | High | High | IndexedDB queue, visual badge, sync on reconnect |
| Wrong lead selected | Low | High | Confirmation screen before submit |
| Duplicate submission | Low | Medium | Idempotency key per form (lead_id + timestamp) |
| Photo too large | Medium | Low | Client-side compression before upload |

---

## 13. Scalability Considerations

- **Multi-employee:** Each employee has own OAuth token + Drive folder
- **Multi-tenant:** If another company uses this app → separate Zoho org + Drive scopes
- **Form builder:** Forms can be driven by a JSON config, not hardcoded fields
- **Analytics:** Submission success rate, avg time per lead, offline ratio → stored in IndexedDB, shown in admin view

---

## 14. What's Needed From You (User)

Before Master Plan V2, I need:

**A. Access & Credentials**
- [ ] Google Cloud Console project (or use existing) with Drive API enabled
- [ ] Google OAuth client ID (web application type)
- [ ] Redirect URIs configured (localhost for dev, production URL)
- [ ] Zoho CRM OAuth client ID (already have from earlier)
- [ ] Which Zoho modules/fields should appear on the form? (field list)

**B. Reference Materials**
- [ ] Link to your existing working web app (repo or demo URL)
- [ ] Screenshot/sample of the Google Form used for photos
- [ ] Google Sheet structure (column names) used currently
- [ ] n8n workflow file (if using n8n) — to understand current mapping

**C. Business Logic**
- [ ] How many field employees will use this?
- [ ] Do employees need to see ALL leads or only their assigned ones?
- [ ] What happens after form submission? Does CRM trigger any workflow?
- [ ] Are there different form types? (site survey, installation, follow-up)
- [ ] Is there a stage/status field that changes after submission?

---

## 15. Open Questions

1. **Google account ownership:** Do field employees have company Google accounts, or personal ones? (Affects Drive scope)
2. **Zoho role setup:** Are employees set up as "Salesperson" or "Admin" in Zoho? (Determines API permission scope)
3. **Existing data:** Do you want historical leads migrated into the app, or only new ones going forward?
4. **PWA vs hosted:** Should this be a PWA (installable) or a hosted web app?
5. **Maintenance:** Who maintains the app after launch? Do you have hosting?

---

## 16. Phased Implementation Plan

### Phase 1: Foundation (1–2 days)
- Project scaffolding (Vite + Tailwind)
- Zoho OAuth2 PKCE login flow
- Lead list view (live from CRM)
- Basic form (hardcoded fields)
- Single-field CRM update test

### Phase 2: Photos & Drive (1–2 days)
- Photo capture component
- Client-side compression
- Google Drive upload
- Drive link → CRM field mapping

### Phase 3: Offline Support (1 day)
- IndexedDB queue
- Sync manager
- Visual pending indicators
- Retry logic

### Phase 4: Polish & Deploy (1 day)
- PWA manifest + icons
- Error handling UI
- Loading states
- Deploy to Netlify/Vercel

### Phase 5: Iterations (ongoing)
- Dynamic form fields from CRM layout
- Admin dashboard
- Analytics

---

## 17. My Assessment

**What I can do autonomously:**
- Build the entire frontend (HTML/CSS/JS)
- Write Zoho CRM API integration
- Implement Google Drive upload flow
- Build offline queue with IndexedDB
- Deploy to Netlify (CLI)
- Write all code, configs, deployment scripts

**What I need from you:**
- Google Cloud OAuth client ID + configured redirect URI
- Form field definitions (which CRM fields to capture)
- Zoho module name + field names for the form
- Reference app link (if private repo, clone it and give me access)

**Time estimate:** 4–6 hours of work split across phases. I can deliver Phase 1–3 in one session once I have the credentials.

---

*Last updated: 2026-05-07*
*Status: Awaiting user input (credentials + field definitions)*
