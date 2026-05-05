# Zoho CRM UI Components — Buttons, Navigation & Form Elements
**Source:** 735 Zoho CRM KB articles with UI screenshots
**Purpose:** UI/UX replication reference — maps UI patterns to feature areas

---

## Button Taxonomy

### Primary Actions (Top Bar)
| Button | Found In | Feature Area |
|--------|----------|--------------|
| **Save** | All record pages | All |
| **Edit** | Detail views | All |
| **Delete** | Detail views | All |
| **Clone / Duplicate** | Detail views | All |
| **Add / Create** | List views | All |
| **Export** | List views, Reports | Data, Reports |
| **Import** | List views, Setup | Data |
| **Close** | Detail views, Modals | All |

### Record Actions (Record Level)
| Button | Found In | Feature Area |
|--------|----------|--------------|
| **Submit for Approval** | Approval-enabled modules | Workflow |
| **Approve / Reject** | Approval notifications | Workflow |
| **Convert Lead** | Leads module | Leads |
| **Send Email** | Contact, Deal, Lead | Email |
| **Log Activity** | Record detail pages | Activities |
| **Add Note / Comment** | Feed/Activity tabs | Tagging |
| **Share** | Records, Reports | Sharing |
| **Mass Update** | List view | Data |

### Module-Specific Actions
| Button | Module | Feature |
|--------|--------|---------|
| **Launch Campaign** | Campaigns | Marketing |
| **Send Survey** | Surveys | Webforms |
| **Create Quote** | Deals | CPQ |
| **Generate Document** | Deals, Contacts | Documents |
| **Sync** | Integrations | Integrations |
| **Refresh** | Dashboards, Lists | All |
| **Schedule Report** | Reports | Analytics |

### Navigation & Layout Buttons
| Element | Location | Notes |
|---------|----------|-------|
| **Tab Bar** | Top of module | Home, Leads, Contacts, Deals, etc. |
| **+ (Quick Create)** | Global floating button | Creates record in any module |
| **⋮ (More Actions)** | Record header, row | Dropdown with context actions |
| **← → (Pagination)** | List views | Page navigation |
| **⚙ (Settings)** | Module header | Module-specific settings |
| **Filter / Sort** | List view header | Column filtering |
| **Group By** | List view | Group records by field |
| **Collapse / Expand** | Sections, Sidebars | Toggle visibility |
| **Full Screen** | Canvas, Reports | Maximize view |

---

## Form Field Types

### Standard Fields
| Field Type | UI Pattern | Feature |
|------------|------------|---------|
| **Single-line Text** | `<input type="text">` | All |
| **Multi-line Text** | `<textarea>` | All |
| **Rich Text Editor** | WYSIWYG toolbar | Email, Notes |
| **Number** | `<input type="number">` | All |
| **Currency** | Number + currency symbol | Deals, Inventory |
| **Date** | Calendar picker | All |
| **DateTime** | Date + Time picker | Activities |
| **Time** | Time selector | Activities, Business Hours |
| **Phone** | Dial icon + input | Contacts, Leads |
| **Email** | Mail icon + input | Contacts, Leads |
| **URL** | Link icon + input | Accounts |
| **Checkbox** | ☐ / ☑ toggle | All |
| **Radio Button** | ○ / ● selection | Forms |
| **Dropdown** | Select with chevron | All |
| **Multi-select** | Dropdown + chips | All |
| **User Lookup** | User picker | Assignment, Workflow |
| **Module Lookup** | Record picker | Related records |
| **File Upload** | Drag & drop zone | Attachments |
| **Signature** | Canvas signer | Quotes, Contracts |
| **Rating** | ★ stars | Reviews, Scoring |
| **Slider** | Range input | Scoring |
| **Formula** | Auto-calculated | Computed fields |

---

## Layout & Structure Components

### Page Layout Regions
```
┌─────────────────────────────────────────────────────┐
│ MODULE HEADER: [Tab] [Tab] [Tab]     [+Add] [⚙]   │
├─────────────────────────────────────────────────────┤
│ SUBHEADER: Breadcrumb / Filters / View Selector     │
├──────────┬──────────────────────────────────────────┤
│          │                                          │
│ SIDEBAR  │  MAIN CONTENT AREA                      │
│ (List/   │  ┌────────────────────────────────────┐ │
│  Filter) │  │ RECORD HEADER                      │ │
│          │  │ [Avatar] Name  [Actions] [♥] [⋮]  │ │
│          │  ├────────────────────────────────────┤ │
│          │  │ DETAIL TABS: [Details][Activity]   │ │
│          │  │             [Related][Feed] ...     │ │
│          │  ├────────────────────────────────────┤ │
│          │  │ TAB CONTENT AREA                   │ │
│          │  │                                    │ │
│          │  └────────────────────────────────────┘ │
│          │                                          │
└──────────┴──────────────────────────────────────────┘
```

### Component Hierarchy
```
Application
├── GlobalHeader
│   ├── Logo
│   ├── ModuleTabs (Leads, Contacts, Deals...)
│   ├── QuickCreateButton (+)
│   ├── GlobalSearch
│   └── UserMenu
├── ModuleView
│   ├── ListView
│   │   ├── FilterBar
│   │   ├── ColumnHeaders (sortable)
│   │   ├── RecordRows
│   │   └── Pagination
│   ├── DetailView
│   │   ├── RecordHeader
│   │   ├── TabPanel
│   │   │   ├── DetailsTab
│   │   │   ├── ActivityTab
│   │   │   ├── RelatedListTab
│   │   │   └── FeedTab
│   │   └── SidePanel (timeline, checklist)
│   └── CanvasEditor (custom layouts)
├── GlobalModals
│   ├── QuickCreateModal
│   ├── SearchModal
│   ├── ImportWizard
│   └── BulkEditModal
└── NotificationCenter
```

---

## Component-to-Feature Mapping

| Component | Primary Feature Areas |
|-----------|----------------------|
| **Page Layouts** | Customization, Canvas |
| **Tab Panels** | All modules |
| **Related Lists** | All modules |
| **Activity Feeds** | Activities, Tagging |
| **Timeline** | Deals, Activities |
| **Kanban Board** | Deals, Projects |
| **Calendar View** | Activities, Meetings |
| **Chart Views** | Analytics, Reports |
| **Formula Builder** | Customization, CPQ |
| **Workflow Designer** | Workflow |
| **Blueprint Designer** | Blueprint |
| **Canvas Editor** | Canvas |
| **Report Builder** | Analytics |
| **Import Wizard** | Data |
| **Approval Panel** | Workflow |

---

## Interaction Patterns

### Hover States
- Buttons: slight brightness increase, cursor pointer
- Row items: background color highlight
- Tooltips: appear after 500ms hover

### Click Actions
- Single click: select / open
- Double click: edit (in list views)
- Right click: context menu

### Drag & Drop
- Reorder list items
- Move between Kanban stages
- Attach files to records

### Keyboard Shortcuts
- `N` — New record
- `E` — Edit record
- `/` — Global search
- `Esc` — Close modal/cancel
- `Ctrl+S` — Save
- `Ctrl+C/V` — Copy/Paste
- `Tab` — Next field

---

*Part of PanaceaX Zoho CRM Documentation*
