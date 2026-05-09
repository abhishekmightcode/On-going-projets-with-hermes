# On Going Projets with Hermes

> **Purpose:** Complete visibility of all projects, plans, implementations, and next steps — for Abhishek's reference and memory. If Hermes loses context, this repo must be enough to understand everything.

**Managed by:** Hermes Agent (Abhishek Sharma)
**GitHub:** https://github.com/abhishekmightcode/On-going-projets-with-hermes

---

## 📁 Repository Structure

```
On-going-projets-with-hermes/
│
├── README.md                        ← You are here
│
├── VSS/                             # V Sustain Solar Solutions (ACTIVE)
│   ├── README.md                    ← Company overview, contacts, quick facts
│   ├── STATUS.md                    ← Current status, what's working, what's next
│   ├── CREDENTIALS.md               ← All credentials (API keys, tokens, endpoints)
│   ├── STRATEGY/                    ← Company strategy docs
│   │   ├── MASTER-STRATEGY.md
│   │   ├── HUMAN-CAPITAL.md
│   │   ├── COMPLIANCE.md
│   │   └── CASE-STUDIES.md
│   ├── PLANS/                       ← All plans (field app, strategy, etc.)
│   │   └── FIELD-APP-MASTER-PLAN.md
│   ├── IMPLEMENTATIONS/             ← What was built
│   │   ├── FIELD-APP/               ← VSS Field App (live at GitHub Pages)
│   │   ├── ZOHO-CRM/                ← Zoho module studies, field maps
│   │   └── FIREBASE/                ← Firebase config, sync scripts
│   ├── TOOLS.md                     ← Tooling (quotegen, Executionflow, etc.)
│   └── COMPETITOR-RESEARCH/        ← Bangalore solar market intelligence
│
├── PanaceaX/                        # PanaceaX (EXPLORATION)
│   ├── README.md
│   ├── PLANS/
│   ├── IMPLEMENTATIONS/
│   ├── STUDY.md                     ← Initial research findings
│   └── ZOHO-RESEARCH/              ← PanaceaX-specific Zoho research
│
├── Solar-Bangalore/                 # Solar-Bangalore market research (PAUSED)
│   ├── README.md
│   ├── PLANS/
│   ├── IMPLEMENTATIONS/
│   └── field-app/                   ← Old field app drafts (superseded by VSS)
│
└── SHARED/                          # Cross-project resources
    └── ZOHO-RESEARCH/               ← Full Zoho CRM API reference (8 parts)
```

---

## 🚦 Project Status At a Glance

| Project | Status | What to know |
|---------|--------|--------------|
| **VSS** | 🔴 ACTIVE | Field app running at abhishekmightcode.github.io/vss-ups-field-app/ |
| **PanaceaX** | 🟡 EXPLORATION | Research phase, no implementation yet |
| **Solar-Bangalore** | ⚪ PAUSED | Field app work superseded by VSS |

---

## 🔑 Key Rules (For Hermes)

1. **Every new project** → create a folder in this repo before doing anything else
2. **Every plan** → write it as a `.md` file in the project's `PLANS/` folder
3. **Every implementation** → document what was built in `IMPLEMENTATIONS/`
4. **Every credential or secret** → store in `~/.hermes/` locally AND reference in `CREDENTIALS.md`
5. **Never push secrets to this repo** — CREDENTIALS.md contains only REFERENCE FILES, not actual secrets
6. **Zoho DC:** `.in` (India) — `crm.zoho.in`, token URL `https://accounts.zoho.in/oauth/v2/token`
7. **Firebase doc ID** = Zoho record ID (PRIMARY KEY). `dealer_code` = secondary key stored as field inside doc.
8. **All text entry** via in-app web form → direct Zoho API. No Google Forms for text.

---

## 📍 VSS Field App (ACTIVE)

**Live:** https://abhishekmightcode.github.io/vss-ups-field-app/

**What it does:**
- Field employees view dealer list from Firebase (instant load)
- Tap a dealer → see details: 📍 Send Location | 📝 Submit Info | 📷 Upload Photo
- **Send Location:** GPS → Zoho CRM via `PUT /crm/v2/UPS/{record_id}` (uses Zoho record ID)
- **Submit Info:** In-app form → Zoho CRM via `PUT` + creates Dealer Meets entry via `POST`
- **Upload Photo:** Opens Google Form (photo only — Google Form setup pending)
- **Hourly sync:** Zoho → Firebase (cron job ID `e7474b1dd47e`)

**Data model:**
- Firebase doc ID = Zoho record ID (e.g. `1171062000002901006`)
- `dealer_code` stored as field inside each doc (e.g. `1000036809`)
- Zoho is source of truth; Firebase is read-cache

**Known issues (resolved):**
- ❌ Bug: `docRef` undefined in `syncFromZoho()` → ✅ Fixed commit `ecb5edf`
- ❌ Bug: Firebase doc ID used `dealer_code` instead of record ID in `sendLocation()` and `submitInfoForm()` → ✅ Fixed commit `ecb5edf`

---

*Last updated: 2026-05-09*