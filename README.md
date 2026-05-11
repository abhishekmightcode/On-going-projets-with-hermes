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
├── PanaceaX-Knowledge-Base/         # AI-Native CRM / Zoho research
│   ├── README.md                    ← Project overview
│   ├── STUDY.md                     ← Initial research findings
│   ├── PLANS/
│   ├── IMPLEMENTATIONS/
│   └── docs/
│       ├── ZOHO/                   ← Zoho CRM API reference (8 parts)
│       │   ├── ZOHO-RESEARCH/
│       │   │   ├── PART-1 through PART-8
│       │   │   ├── ZOHO-CRM-COMPLETE-REFERENCE.md
│       │   │   └── Zoho-CRM-UI-Reference/
│       │   └── ZOHO-CRM-FEATURE-ATLAS.md
│       └── Zoho-CRM-Features/      ← 30 Zoho CRM feature docs
│
├── VSS-Knowledge-Base/              # V Sustain Solar Solutions (ACTIVE)
│   ├── README.md                    ← Company overview
│   ├── STATUS.md                    ← Current status
│   ├── CREDENTIALS.md               ← Credentials reference
│   ├── STRATEGY/                    ← Company strategy
│   ├── TOOLS/                       ← Tooling docs
│   ├── PLANS/                       ← All plans
│   ├── IMPLEMENTATIONS/             ← What was built
│   └── docs/
│       ├── COMPETITOR-RESEARCH/     ← Bangalore solar market intel
│       ├── FIELD-APP/               ← VSS Field App docs
│       └── ZOHO-CRM/                ← Zoho module studies
│
└── Solar-Bangalore/                 # Solar market research (PAUSED)
    └── README.md
```

---

## 🚦 Project Status At a Glance

| Project | Status | What to know |
|---------|--------|--------------|
| **VSS** | 🔴 ACTIVE | Field app at abhishekmightcode.github.io/vss-ups-field-app/ |
| **PanaceaX** | 🟡 EXPLORATION | Zoho CRM research, AI-native CRM build |
| **Solar-Bangalore** | ⚪ PAUSED | Market research, superseded by VSS |

---

## 🔑 Key Rules (For Hermes)

1. **Every new project** → create a knowledge base folder before doing anything else
2. **Every plan** → write as `.md` in project's `PLANS/` folder
3. **Every implementation** → document in `IMPLEMENTATIONS/`
4. **Every credential or secret** → store in `~/.hermes/` locally AND reference in `CREDENTIALS.md`
5. **Never push secrets to this repo** — `CREDENTIALS.md` contains only reference paths, not actual secrets
6. **Zoho DC:** `.in` (India) — `crm.zoho.in`, token URL `https://accounts.zoho.in/oauth/v2/token`
7. **Firebase doc ID** = Zoho record ID (PRIMARY KEY). `dealer_code` = secondary key stored as field inside doc.
8. **All text entry** via in-app web form → direct Zoho API. No Google Forms for text.

---

## 📍 VSS Field App (ACTIVE)

**Live:** https://abhishekmightcode.github.io/vss-ups-field-app/

**What it does:**
- Field employees view dealer list from Firebase (instant load)
- Tap a dealer → see: 📍 Send Location | 📝 Submit Info | 📷 Upload Photo
- **Send Location:** GPS → Zoho CRM via `PUT /crm/v2/UPS/{record_id}` (Zoho record ID as doc ID)
- **Submit Info:** In-app form → Zoho CRM via `PUT` + creates Dealer Meets entry via `POST`
- **Upload Photo:** Google Form (photo only)
- **Hourly sync:** Zoho → Firebase (cron job ID `e7474b1dd47e`)

**Data model:**
- Firebase doc ID = Zoho record ID (e.g. `1171062000002901006`)
- `dealer_code` stored as field inside each doc (e.g. `1000036809`)
- Zoho is source of truth; Firebase is read-cache

---

## 📍 PanaceaX (EXPLORATION)

**Purpose:** AI-native CRM build using Zoho CRM as platform. All Zoho research consolidated here.

**Key docs:**
- `docs/ZOHO/ZOHO-RESEARCH/` — Full Zoho CRM API v2 reference (8 parts)
- `docs/ZOHO/ZOHO-CRM-FEATURE-ATLAS.md` — Feature atlas
- `docs/Zoho-CRM-Features/` — 30 Zoho CRM feature deep-dives

---

*Last updated: 2026-05-11*