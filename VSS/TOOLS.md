# VSS — Tools

> **Date:** May 2026

---

## Overview

VSS operates two production web tools that form the operational backbone of the business. Both are hosted on GitHub Pages and connect to external services (Google Sheets, n8n, Zoho CRM).

---

## 1. quotegen — Quotation Generator

**Live URL:** `https://vsustainsolar.github.io/quotegen/`  
**Repo:** `https://github.com/vsustainsolar/quotegen`

### Purpose

Generates professional, GST-compliant price quotations for solar and UPS systems. Used by sales team to create client-facing proposals.

### Variants

| Variant | Purpose | Path |
|---------|---------|------|
| **On-Grid** | Grid-tied rooftop with net-metering | `on-grid/index.html` |
| **Off-Grid** | Standalone solar with battery storage | `off-grid/index.html` |
| **UPS B2B** | Luminous UPS systems for commercial | `ups-b2b/index.html` |

### Tech Stack

- Pure HTML + CSS + Vanilla JavaScript
- No backend — all computation client-side
- GST calculation logic built-in (5% / 18%)
- Print-optimized CSS

### Key Features

- Dynamic system sizing based on load inputs
- Component breakdown: panels, inverters, ACDB/DCDB, cabling, BOS
- ROI calculation
- GST-compliant PDF-ready output
- Mobile-responsive

### Brand Integration

- V Sustain logo + brand colors (blue #0a2a5e, yellow #f5c518)
- Luminous authorized partner messaging
- Contact details auto-populated

---

## 2. Executionflow — Field Execution Tracker

**Live URL:** `https://vsustainsolar.github.io/Executionflow/`  
**Repo:** `https://github.com/vsustainsolar/Executionflow`

### Purpose

Field app used by installation workers to update project progress in real-time. Updates flow into Zoho CRM via n8n webhook + Google Sheets as backend.

### Architecture

```
Field Worker (Mobile Browser)
    │
    ├─► Google Sheets (Google Apps Script) — Read/write project data
    │
    └─► n8n Webhook ──► Zoho CRM — Updates EXECUTION_STAGE + ONSITE_STAGE
```

### Tech Stack

- HTML + CSS + Vanilla JavaScript
- Google Apps Script Web App (Google Sheets backend)
- n8n cloud webhook (workflow automation)
- Google Form (photo upload via mobile)
- Zoho CRM (final record update)

### Config (config.js)

```javascript
SHEET_API_URL: "https://script.google.com/macros/s/.../exec"
N8N_WEBHOOK_URL: "https://vsustainsolar.app.n8n.cloud/webhook/..."
GOOGLE_FORM_BASE: "https://docs.google.com/forms/d/e/.../viewform"
LOGO_URL: "https://raw.githubusercontent.com/vsustainsolar/Images/..."
```

### Execution Stages (in order)

1. Advance received
2. Procurement done and Team assigned
3. Execution day 1
4. Execution day 2
5. Execution day 3
6. Feedback Taken
7. Subsidy amount received
8. Commissioning

### On-Site Stages (independent checklist)

- Material Delivered
- Payment 2 done
- Structure setup
- Panel mounting
- Electrical wiring
- ACDB DCDB setup
- Inverter-UPS-Battery installation
- Earthing
- Lightning arrester
- Commissioning

### Project Leads

Shivakant | Nikhil | Atul | Shailesh

---

## Connection to Zoho CRM

Executionflow is the **field-facing layer** that feeds data into Zoho CRM:

- Workers update stages via mobile browser
- Data writes to Google Sheets (real-time backup)
- n8n webhook fires on each update
- Zoho CRM record updated with current stage
- Manager sees real-time progress in CRM dashboard

This creates a **closed loop**: Field → Sheet → n8n → CRM

---

## Future Tool Roadmap

| Tool | Priority | Description |
|------|----------|-------------|
| Customer Portal | High | Self-service for clients to track project status |
| AMC Manager | High | Manage renewal lifecycle for maintenance contracts |
| Lead Tracker | Medium | Lite CRM for incoming leads + follow-up reminders |
| Survey Tool | Medium | Post-installation feedback collection |
| Inventory Manager | Low | Track spare parts, stock alerts |

---

*Source: VSS GitHub repos + config.js*
