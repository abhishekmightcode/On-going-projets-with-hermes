# Zoho CRM UI Reference Catalog
**Project:** PanaceaX — Zoho CRM Feature Documentation
**Purpose:** UI component mapping for Zoho CRM replication
**Source:** 1,036 scraped KB articles, 7,118 UI screenshots
**Last Updated:** May 2026

---

## Summary

| Metric | Count |
|--------|-------|
| Total KB Articles Scraped | 1,036 |
| Articles with UI Images | 735 |
| Unique UI Screenshots | 7,118 |
| Feature Areas Documented | 30 |

---

## Image Distribution by Feature Area

| Feature Area | Articles | UI Images | Top Articles |
|---|---|---|---|
| Extensions (Integrations) | 263 | 2,174 | Amazon Connect, Marketo, SalesIQ, Ytel |
| Zia AI | 87 | 991 | Custom AI Studio, Zia Vision, Anomaly Detection |
| Customization & Canvas | 51 | 523 | Working with Page Layouts, Canvas Studio |
| Mobile CRM | 43 | 408 | Android App Analytics, iOS Features |
| Analytics & Reports | 29 | 407 | Understanding Reports, Building Reports |
| Workflow Automation | 40 | 352 | Workflow Rules, Assignment Rules |
| Integrations | 29 | 304 | Meeting Integration, telephony |
| Data Management | 23 | 302 | Data Migration FAQs, Import/Export |
| Settings | 12 | 230 | Configuration, Portal Setup |
| Contacts & Accounts | 21 | 182 | Contact Management, Organization Details |
| Blueprint | 23 | 180 | Process Management, Stage Automation |
| Activities | 19 | 167 | Tasks, Events, Meetings |
| Modules | 14 | 151 | Data Model, Custom Modules |
| **Total** | **735** | **7,118** | |

---

## How to Use This Catalog

### Finding UI Images for a Feature
1. Each feature area has its own subfolder
2. Images are referenced by `article_title` → `image_url`
3. To find the exact UI element, navigate to the article URL and scroll to the relevant section

### Image URL Pattern
```
https://help.zoho.com/portal/en/kb/crm/{article-permalink}
  → Images embedded in article body:
    https://help.zoho.com/galleryDocuments/{gallery_id}?inline=true
    https://desk.zoho.in/galleryDocuments/{gallery_id}?inline=true
    https://www.zohowebstatic.com/sites/default/files/{filename}.png
```

### Image Filtering Applied
- ✅ Included: Screenshot images (100px+) from KB articles
- ✅ Included: UI diagrams, workflow screenshots, form layouts
- ❌ Excluded: Icons (< 40px), logos, avatars, arrows, bullets
- ❌ Excluded: Tracking pixels, spacers, gradients

---

## Key UI Elements Found

### Common Button Labels (from 735 articles)
- Save, Cancel, Edit, Delete, Add, Remove, Clone, Export
- Submit, Approve, Reject, Escalate, Close
- Send Email, Schedule, Create, Update, Refresh
- Next, Previous, Back, Done, Finish
- Search, Filter, Sort, Group, View
- Setup, Configure, Manage, Customize

### Common Navigation Elements
- Tab names: Home, Leads, Contacts, Deals, Activities, Analytics, Reports
- Module names: All, My Team, Shared, Archive
- Action menus: More Actions (⋮), Quick Create (+)

### Common Form Elements
- Text fields, dropdowns, radio buttons, checkboxes
- Date pickers, time pickers, user pickers
- File upload zones, signature pads
- Lookup fields, related list tables

---

## JSON Data File

For programmatic access, see:
```
ZOHO-CRM-IMAGE-CATALOG.json
```

Contains:
- `all_articles[]` — every article with image URLs, dimensions, article URL
- `by_feature_area{}` — articles grouped by Zoho CRM feature
- `summary{}` — total counts and metadata

---

*Part of PanaceaX Zoho CRM Documentation — maintained for AI-native CRM development*
