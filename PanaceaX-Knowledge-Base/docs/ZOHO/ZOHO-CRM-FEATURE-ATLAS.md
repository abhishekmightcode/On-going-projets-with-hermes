# Zoho CRM — Complete Feature Atlas & Industry Use Case Mapping

> Compiled for AI-Native CRM Build | Solar Solutions (Bangalore) | Abhishek Sharma

---

## 📌 HOW TO READ THIS DOCUMENT

Each Zoho CRM feature is listed with:
- **What it does** — Core capability
- **How it solves problems** — Business value
- **Industry touchpoints** — Which verticals benefit most
- **Config/API notes** — How to set it up

---

# PART 1: ZOHO CRM FEATURE ATLAS

---

## 🔷 MODULE & CUSTOMIZATION ENGINE

### 1.1 Standard Modules
- **Leads** — Inbound prospect capture, scoring, lifecycle tracking
- **Contacts** — Customer/company relationships (post-conversion)
- **Accounts** — Company records with hierarchical structures
- **Deals** — Revenue opportunities with pipeline stages, amounts, probabilities
- **Activities** — Tasks, Events, Calls — all customer touchpoints
- **Solutions** — Knowledge base / FAQ management for support
- **Products** — Product catalog with pricing, stock, images
- **PriceBooks** — Multiple pricing tiers per product
- **Quotes** — Auto-generated from deals, send to prospects
- **SalesOrders, PurchaseOrders, Invoices** — Full revenue cycle
- **Cases** — Customer support tickets
- **Vendors** — Supplier management
- **Custom Modules** — Build ANYTHING (Projects, Properties, Students, Vehicles, etc.)

### 1.2 Layout Designer
- Drag-and-drop page layouts per module
- Sections, columns, fields placement
- **Multi-layout support** — Assign different layouts to different roles/profiles
- **Mobile layouts** — Optimized for CRM mobile app
- **Related Lists** — Show child records (e.g., all deals under an Account)
- Conditional fields — show/hide based on other field values

### 1.3 Field Types (50+)
| Type | Use For |
|------|---------|
| Single Line / Multi Line | Names, descriptions |
| Email / Phone | Contact details with click-to-call |
| Number / Currency | Deal amounts, quantities |
| Date / DateTime | Deadlines, appointments |
| Dropdown / Multi-select | Status, category, tags |
| Lookup | Connect to other modules (Contact→Account) |
| Formula | Auto-calculate (Deal value × probability) |
| Cross Module | Pull data from related records |
| Image / File Upload | Documents, photos, ID proofs |
| Radio / Checkbox | Yes/No, binary choices |
| Percent | Margins, completion rates |
| Phone (with territory routing) | Smart call routing |

### 1.4 Module Relationships
- **1:1** — One Contact → One License
- **1:N** — One Account → Many Contacts, Many Deals
- **N:N** — Many Contacts ↔ Many Deals (via Deal Contact Role)
- **Parent-Child** — Sub-accounts under holding company
- **Customer Portal** — External stakeholders see limited view

---

## 🔷 SALES FORCE AUTOMATION (SFA)

### 2.1 Pipeline Management
- **Multiple Pipelines** — Separate pipelines for different products/channels
- **Custom Stages** — Per pipeline stage with probability %
- **Stage Actions** — On entering stage: auto-create task, send email, update field
- **Kanban View** — Drag-and-drop deal management
- **List View** — Sortable, filterable, mass-update
- **Timeline View** — Activity-based chronological view
- **Deal splitting** — Split credit across multiple owners
- **Loss reasons** — Mandatory/optional on deal loss
- **Reactivation** — Reopen lost deals

### 2.2 Lead Management
- **Lead capture sources** — Web forms, email parsing, API, import, social
- **Lead scoring** — Demographic (industry, company size, title) + Behavioral (email opens, page visits)
- **Assignment Rules** — Round-robin, territory, load-balanced, criteria-based
- **Lead conversion** — One-click: Contact + Account + Deal (with field mapping)
- **Lead nurturing** — Drip sequences via workflows
- **Auto-response** — Instant acknowledgment on lead creation
- **Duplicate detection** — Block or warn on duplicate emails/phones

### 2.3 Goal Metrics & Quotas
- Revenue targets per rep/team/org
- Activity targets (calls, meetings, demos per day/week)
- Quantity targets (deals closed, MQLs generated)
- Goal hierarchies — team = sum of individual reps
- Gamification — leaderboards, badges, achievements
- Quota tracking vs actual in real-time

### 2.4 Forecasting
- **Commit / Best Case / Pipeline** — Three-slice forecasting
- **Forecast by owner, territory, product, team**
- **Rolling forecasts** — Moving averages
- **Multi-scenario** — Optimistic, realistic, conservative
- **Manager overrides** — Adjust with justification notes
- **Period comparison** — Q1 vs Q2, this year vs last year

---

## 🔷 COMMUNICATION CHANNELS

### 3.1 Email
- **Multi-account** — sales@, support@, info@ linked to CRM
- **Shared inboxes** — Team manages generic addresses
- **Email-to-lead** — Auto-create leads from new inbound senders
- **Email threading** — All emails linked to CRM records
- **Templates with merge fields** — `{{Lead.First_Name}}`, `{{Deal.Amount}}`
- **HTML + Plain text** — Rich formatting support
- **Send later / Schedule** — Send at optimal times
- **Follow-up reminders** — If no reply in X days → alert
- **Mass email campaigns** — Bulk send with open/click tracking
- **Email workflows** — Trigger on record events
- **Shared email templates** — Organization-wide consistency

### 3.2 SMS Gateway
- **Providers supported** — Zoho SMS, Twilio, MSG91, Plivo, Sinch
- **Two-way SMS** — Receive and reply within CRM
- **SMS templates** — With merge fields
- **Bulk SMS campaigns** — Filter CRM records → send
- **SMS automation** — Triggered by record events
- **Scheduling** — Send at specific date/time
- **Delivery tracking** — Sent, delivered, failed statuses
- **Opt-out management** — Auto-unsubscribe handling

### 3.3 WhatsApp Business API
- **Official WhatsApp Business API** — Not unofficial third-party apps
- **Setup requirements:**
  1. Meta Business Account
  2. WhatsApp Business Profile
  3. Dedicated phone number (not personal WhatsApp)
  4. Approved message templates (by Meta)
- **Template categories:**
  - Marketing (promotional, offers)
  - Utility (order updates, appointments)
  - Authentication (OTP, verification)
  - Appointment reminders
- **Features in CRM:**
  - Send templated WhatsApp from CRM record
  - Two-way conversation within CRM
  - Media (images, docs, videos)
  - Read receipts / delivery status
  - Multi-agent support
  - Chat assigned to specific rep
- **Use cases:**
  - Appointment confirmations with PDF
  - Abandoned cart recovery
  - Order status updates with tracking
  - Lead nurture with video content
  - Payment link sharing
  - Urgency messaging (seats remaining, limited offer)

### 3.4 Telephony / Zoho Voice
- **Virtual numbers** — Local, toll-free, international
- **IVR** — Multi-level call routing (Press 1 for sales, 2 for support)
- **Call queues** — Distribute among agents
- **Click-to-call** — From any phone field
- **Auto-call logging** — Every call linked to CRM record
- **Call recording** — For training and compliance
- **Call pop-up** — Incoming call shows CRM record immediately
- **Voicemail to text** — Transcribed and logged
- **Disposition/call notes** — Tag outcomes (Interested, Callback, Not interested)
- **Missed call → Lead** — Auto-create lead on missed calls
- **SMS on missed call** — Auto-reply with info

### 3.5 Facebook & Instagram Lead Ads
- **Auto-sync leads** from Facebook/Instagram Page CTAs
- **Field mapping** — Map Facebook fields → CRM fields
- **Source tracking** — Mark all social leads with source
- **Campaign ID capture** — Which ad generated the lead
- **Auto-assignment** — Round-robin or territory
- **Instant workflow** — Send welcome email/SMS on capture
- **Deduplication** — Match against existing contacts

---

## 🔷 AUTOMATION ENGINE

### 4.1 Workflow Rules
**Triggers:**
- Record created
- Record created OR edited
- Record edited
- Scheduled (daily/weekly/monthly at set time)
- Date field reached (e.g., "30 days before closing date")

**Conditions:**
- Field equals / not equals / contains / starts with / ends with
- Is empty / Is not empty
- Date before / after / between
- AND/OR logic with unlimited nesting
- Cross-field conditions

**Actions:**
- Send Email Alert (to user, lead, external email)
- Create Task (subject, due date, priority, assignee)
- Update Field (single or multiple fields)
- Create Record (spawn related record)
- Assign Owner (change rep)
- Invoke Webhook (HTTP POST to external URL)
- Clone Record
- Send SMS
- Send WhatsApp Template
- Execute Deluge Function (custom logic)
- RSS Feed notification
- Submit for Approval

**Execution modes:**
- Instant — runs immediately on trigger
- Scheduled — batch process at defined intervals

### 4.2 Blueprints (Process Management)
- Define mandatory process flow for ANY module
- Stages with:
  - Description
  - Assigned tasks
  - Required fields (can't proceed without)
  - Optional actions (field auto-fill, notifications)
  - Due dates for stage completion
- **Milestones** — Key checkpoints within stages
- **Conditional transitions** — Skip/reorder stages based on data
- **Deny progression** — Block next stage until action completed
- **Restrict back-tracking** — Prevent returning to earlier stages
- **Bulk stage update** — Move multiple records at once

### 4.3 Approval Processes
- **Multi-step sequential approval**
- **Parallel approval paths**
- **Escalation** — Auto-escalate after time threshold
- **Delegate** — Forward to another approver
- **Criteria-based** — Only records matching conditions need approval
- **On approve** — Field updates, notifications, record creation
- **On reject** — Return to submitter with comments
- **Mass approval** — Admin bulk approve/reject
- **Recall** — Submitter can recall pending approval

### 4.4 Assignment Rules
- **Round-robin** — Equal distribution among team
- **Load-balanced** — Assign to rep with fewest open deals
- **Territory-based** — By region, zip code, city, country
- **Criteria-based** — Lead source = Trade Show → Event team
- **Weighted distribution** — 70% to Team A, 30% to Team B
- **SLA-based reassign** — Unclaimed after 24hrs → escalation queue
- **Skip unavailable** — Don't assign to on-leave reps

### 4.5 Macros
- **Bulk actions** — Apply to multiple records in one click
- **Action sequences** — Update fields + send email + create task
- **Per-record or mass apply**
- **Scheduled macros** — Run on filtered record sets automatically
- **Template for common operations** — "Convert hot lead", "Archive closed won"

---

## 🔷 ZIA — AI ENGINE

### 5.1 Predictive Lead Scoring
- ML model analyzes 100+ signals
- Demographic (industry, title, company size, location)
- Behavioral (email engagement, website visits, form submissions)
- Engagement recency and frequency
- Outputs: 0–100 score per lead
- Continuously retrains on converted/lost data
- Segment by score → trigger workflows (score > 80 = hot lead)

### 5.2 Deal Prediction (Win Probability)
- Predicts: Will this deal close? When?
- Win probability % per deal
- Risk indicators ("Deal at risk: no activity in 14 days")
- Predicted close date
- Deal health score (green/amber/red)
- Inputs: stage, amount, engagement, activity, competitor mentions

### 5.3 Best Next Action
- AI recommends optimal next step per record
- Best time to contact (based on past engagement patterns)
- Best channel (call, email, WhatsApp, meeting)
- Suggested talk tracks / scripts
- Auto-created reminders
- Cross-sell / upsell suggestions based on purchase history

### 5.4 Anomaly Detection
- Auto-detects unusual patterns
- Deal velocity anomalies (deals moving too fast/slow)
- Revenue pipeline anomalies
- Activity pattern drops (unusual drop in calls)
- Field value anomalies (outlier data entries)
- Alert sent to manager when detected

### 5.5 Sentiment Analysis
- Analyzes email content, notes, case descriptions
- Tags as Positive / Negative / Neutral
- Highlights negative emails in inbox
- Trigger workflows on negative sentiment (→ escalate to senior rep)
- Trend tracking — is customer sentiment improving?

### 5.6 Email Sentiment
- Auto-scans inbound emails for emotional tone
- Flags frustrated/angry customers
- Summarizes tone trends over time
- Workflow trigger: negative sentiment → create urgent task

### 5.7 Activity Capture
- Auto-logs emails (sent, opened, clicked)
- Auto-logs calendar events (meetings, calls)
- Links documents to relevant CRM records
- Eliminates manual CRM data entry
- Rep focuses on selling, not logging

### 5.8 Zia Voice (Voice Assistant)
- "Hey Zia" natural language commands
- Query CRM data by voice
- "Show my deals closing this week"
- "Create a task for tomorrow"
- Hands-free while driving / in field
- Reads data back aloud

### 5.9 Zia Skills (Bot Builder)
- No-code conversational bot builder
- Multi-turn conversations
- Embed on website, WhatsApp, Slack, Facebook
- Handles: FAQs, lead qualification, appointment booking
- Intent recognition + entity extraction
- Analytics dashboard per bot
- Fallback handling for unanswered queries

### 5.10 Zia Labs (Custom ML)
- Self-service ML platform
- Build custom predictive models without coding
- Predictive segmentation
- Anomaly detection on custom metrics
- Data enrichment (auto-fill company info from domain)
- Date/time extraction from natural language

### 5.11 Zia Analytics
- Conversational analytics — ask questions in plain English
- "What was my win rate Q1 vs Q2?"
- Auto-generates charts and reports
- Trend analysis and anomaly explanation
- Pipeline health analysis
- Why deals dropped — Zia investigates and explains

---

## 🔷 ANALYTICS & REPORTING

### 6.1 Dashboard Builder
- Drag-and-drop modular dashboards
- **Component types:**
  - Charts (bar, line, pie, area, funnel, scatter, donut, pyramid, gauge, bullet)
  - Tables (sortable, filterable)
  - Summary views (grouped aggregations)
  - KPI tiles (single metric highlights)
  - Matrix reports
  - Embedded Zoho Reports
  - External data feeds
- Multiple dashboard tabs (Weekly Sales, Manager View, Executive)
- Share with roles, users, or public
- Conditional formatting (red/amber/green thresholds)

### 6.2 Report Builder
- **Tabular** — Classic row/column with sorting
- **Summary** — Group-by with subtotals (pivot)
- **Matrix** — Cross-tabulation
- **Chart-only** — Visual only
- **Filters** — Column-level, custom
- **Conditional formatting** — Color by value
- **Scheduled delivery** — Email daily/weekly/monthly
- **Export** — PDF, CSV, Excel, HTML
- **Drill-down** — Click data point → underlying records

### 6.3 Zoho Analytics (Advanced BI)
- Self-service BI with AI insights
- Predictive analytics
- What-if scenario modeling
- Custom KPI formulas
- Data blending (CRM + non-CRM sources)
- Natural language queries (ask Zia)
- Mobile-optimized dashboards
- Custom branding

### 6.4 Sales Signals
- Real-time alerts on pipeline changes
- Deal at risk notifications
- Activity droughts (no touchpoints in X days)
- Champion left company (via Zia)
- Competitor mentioned in email
- Budget changes detected
- Decision-maker engaged

### 6.5 KPI Tracking
| Category | KPIs |
|----------|------|
| Revenue | Total, by product, by rep, by region |
| Pipeline | Value, velocity, stage conversion rates |
| Activity | Calls, emails, meetings, tasks completed |
| Lead Metrics | MQLs, lead-to-opp rate, response time, CPL |
| Win/Loss | Win rate, avg deal size, deal velocity, cycle length |
| Forecasting | Commit vs quota, accuracy trend |

---

## 🔷 INTEGRATION ECOSYSTEM

### 7.1 Native Zoho Integrations
| App | What it does |
|-----|-------------|
| **Zoho Mail** | Email with CRM sync, shared inbox |
| **Zoho Calendar** | Meeting scheduling, activity logging |
| **Zoho Docs** | Document storage linked to CRM records |
| **Zoho Flow** | No-code automation between Zoho + 3rd party apps |
| **Zoho Books** | Accounting, invoicing — syncs with CRM Deals/Invoices |
| **Zoho Inventory** | Stock, orders, shipments — syncs with Products |
| **Zoho Desk** | Advanced support ticketing |
| **Zoho Campaign** | Advanced email marketing |
| **Zoho Social** | Social media management + CRM lead sync |
| **Zoho Sign** | E-signatures on quotes/contracts |
| **Zoho Lens** | AR-based remote assistance |
| **Zoho Expense** | Expense tracking linked to deals/projects |

### 7.2 Third-Party Integrations
| Category | Integrations |
|----------|-------------|
| **Email/Calendar** | Gmail, Outlook, Google Calendar, Yahoo |
| **Telephony** | Twilio, Asterisk, Plivo, MSG91, Sinch |
| **Payments** | Stripe, Razorpay, PayPal, Square |
| **Accounting** | QuickBooks, Xero, Tally |
| **E-commerce** | Shopify, WooCommerce, Magento, BigCommerce |
| **Communication** | Slack, Microsoft Teams |
| **Marketing** | Mailchimp, HubSpot, ActiveCampaign |
| **Webinar** | Zoom, GoToMeeting, Webex |
| **Forms** | Typeform, Google Forms, JotForm |
| **Analytics** | Google Analytics, Mixpanel |
| **SMS** | Twilio, MSG91, Plivo, Sinch |
| **WhatsApp** | WhatsApp Business API (native) |
| **Social** | Facebook Lead Ads, Instagram, LinkedIn |
| **Maps** | Google Maps (customer location) |
| **Productivity** | Zapier, Make (Integromat) |
| **Shipping** | ShipRocket, Delhivery, FedEx |
| **IVR** | Exotel, Knowlarity |

### 7.3 API & Developer Tools
- **REST API v2** — Full CRUD on all modules
- **OAuth 2.0** — Secure authentication
- **Webhooks** — Real-time HTTP callbacks on record events
- **Deluge Script** — Zoho's own scripting language for custom logic
- **Zoho Flow** — Visual workflow automation between apps
- **Custom functions** — Run in Zoho's cloud, no server needed
- **Scheduled functions** — Cron-like batch processing
- **External handlers** — Connect to external APIs

---

## 🔷 MOBILE CRM

### 8.1 Mobile Features
- Full CRM access on iOS and Android
- Offline mode — work without internet, sync when online
- Mobile-optimized layouts (separate from desktop)
- Push notifications — deal updates, task reminders, lead assignments
- Click-to-call from mobile
- Camera integration — scan business cards, receipts
- GPS — location tracking for field sales
- Voice input — add notes by voice
- Barcode/QR scanning
- GPS check-in for field visits
- Mobile offline data entry + auto-sync

---

## 🔷 CUSTOMER SUPPORT (CASE MANAGEMENT)

### 9.1 Case Lifecycle
- **Case creation** — Email-to-case, web forms, phone, API
- **Case routing** — Assignment rules, round-robin, territory
- **SLA management** — Response and resolution time targets
- **Escalation rules** — Auto-escalate if SLA breached
- **Case layout** — Custom fields for product, issue type, priority
- **Related cases** — Link similar cases together
- **Knowledge base** — Link solutions to cases
- **Customer portal** — Submit and track cases externally
- **Email to case** — Auto-create case from inbound support email

### 9.2 Support Automation
- Auto-assign based on issue category
- Auto-respond with solution suggestions
- Survey on case resolution (CSAT)
- Auto-close after X days of no activity
- Merge duplicate cases

---

## 🔷 DATA ADMINISTRATION

### 10.1 Import / Export
- **CSV, XML, VCard** import
- Field mapping wizard
- Duplicate detection during import
- Scheduled import (auto-fetch from FTP/email attachment)
- Bulk export — records, reports, templates

### 10.2 Data Quality
- **Duplicate detection** — Prevent or warn on duplicates
- **Duplicate merge** — Consolidate duplicate records
- **Validation rules** — Block invalid data entry
- **Field-level security** — Hide/edit restrict by role
- **Data encryption** — At rest and in transit
- **Audit logs** — Track every field change with timestamp + user

### 10.3 Security & Access
- **Roles** — Level-based permissions (CEO, Manager, Rep)
- **Profiles** — Field-level visibility rules
- **Data sharing rules** — Owner-based, criteria-based
- **Territories** — Geographic data segmentation
- **IP-based access restriction** — Only allow office IPs
- **Session timeout** — Auto-logout after inactivity
- **2FA** — Two-factor authentication
- **Password policy** — Strength, expiry, reuse prevention

### 10.4 Organization Settings
- Multi-currency with exchange rates
- Fiscal year configuration
- Business hours + holidays
- Time zone settings
- Company branding (logo, colors)
- Email signature management
- Number formatting localization

---

## 🔷 EXTENSIONS & MARKETPLACE

### 11.1 Popular Extensions
| Extension | Function |
|-----------|---------|
| **Zoho CRM Sync for Google Workspace** | Bidirectional Google Calendar/Contacts sync |
| **Outlook Sidebar** | CRM inside Outlook |
| **Zoho Invoice Integration** | Auto-generate invoices from deals |
| **Zoho CRM Extra Add-in** | Enhanced list views, duplicate merge |
| **Leadzee** | WhatsApp marketing from CRM |
| **Callify** | Advanced telephony integration |
| **Forms** | Advanced web forms with CRM sync |
| **PhoneBurner** | Power dialer for outbound sales |
| **LeadFuze** | B2B lead enrichment |
| **CloudCall** | Call tracking and recording |
| **ManyContacts** | Web contact capture |
| **Convert Assistant** | Lead conversion optimization |
| **Quote Builder** | Advanced quote/proposal builder |
| **DocuSign Integration** | E-signature on quotes |
| **HelloSign Integration** | E-signature |
| **Zendesk Connector** | Sync CRM with Zendesk |

### 11.2 CPQ (Configure, Price, Quote)
- Product configurator with rules
- Dynamic pricing based on quantity/bundle/date
- Guided selling — recommend add-ons
- Quote generation with branding
- E-signature integration
- Version control on quotes
- Discount approvals
- Real-time inventory check

---

## 🔷 WEB FORMS & LANDING PAGES

- **Embeddable forms** — Capture leads directly on website
- **Standalone landing pages** — Without website
- **Conditional fields** — Show/hide based on answers
- **Lead scoring on submission** — Assign score on form fill
- **Auto-assignment** — Route to correct rep
- **Auto-response** — Send email/SMS on submission
- **Google reCAPTCHA** — Block spam
- **UTM tracking** — Capture ad source data
- **Embed in website** — iframe or popup

---

# PART 2: INDUSTRY USE CASE MAPPING

---

## 🏢 INDUSTRY 1: SOLAR ENERGY (HIGH PRIORITY — Bangalore)

### Business Context
Residential + Commercial solar installations. Customer journey: Ad click → Site survey → Proposal → Installation → AMC.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Facebook/Instagram Lead Ads → Auto-create Lead with source tracking |
| **Lead Qualification** | Zia Lead Scoring — Score on: residential vs commercial, budget, electricity usage, roof type |
| **Assignment** | Territory assignment — Bangalore localities → assigned to field reps |
| **Site Survey** | Custom module "Site Surveys" — with Blueprint: Survey Booked → Survey Done → Report Submitted |
| **Proposal** | Deals module with custom fields: System size (kW), panel type, subsidy eligibility, EMI options |
| **WhatsApp Outreach** | WhatsApp API: Send proposal PDF, savings calculator screenshot, subsidy documents |
| **EMI/Financing** | Zoho Books integration for loan tracking; WhatsApp with EMI breakup link |
| **Installation Tracking** | Blueprint: Survey → Design Approval → Installation → Inspection → Meter Connection → Handover |
| **AMC Tracking** | Custom module "AMC Contracts" with renewal reminders via workflows |
| **Payment Tracking** | Zoho Books + Deals linked to invoices; payment milestone workflows |
| **Post-Installation** | Zia activity capture; follow-up workflow at 30/60/90 days post-install |
| **Service/Support** | Cases module for complaints; SLA-based escalation |
| **Cross-sell** | Battery upgrade, EV charging — upsell via WhatsApp templates |
| **Analytics** | Dashboard: Leads by locality, Conversion rate by stage, Avg deal size, Revenue forecast |
| **Marketing** | Mass SMS for festive offers; Email campaigns via Zoho Campaign |
| **Corporate Deals** | Custom module "Corporate Deals" — bulk MW installations for housing societies, factories |

### Custom Fields Needed
- `System_Size_kW` (number)
- `Roof_Type` (dropdown: RCC, Sheet, Terrace)
- `Monthly_Electricity_Bill` (currency)
- `Subsidy_Eligible` (checkbox)
- `Panel_Type` (dropdown: Mono PERC, Poly, Bifacial)
- `Financing_Required` (checkbox)
- `Survey_Status` (lookup to Site Survey module)
- `Locality` (dropdown: Whitefield, HSR, Marathahalli, etc.)
- `Installation_Capacity_MW` (for corporate)

---

## 🏥 INDUSTRY 2: HOSPITAL & HEALTHCARE

### Business Context
Multi-specialty hospital chains. Patient journey: Ad → Appointment → Consultation → Treatment → Discharge → Follow-up → Loyalty.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Facebook Lead Ads (by department: Cardiology, Ortho, etc.); website appointment form |
| **Lead Scoring** | Zia — Score on: urgency indicated, insurance status, proximity to hospital |
| **Appointment Booking** | Custom module "Appointments" with Calendar integration; WhatsApp confirmation |
| **Department Routing** | Assignment rules by department → respective HOD/rep |
| **Patient Records** | Custom module "Patients" (post-conversion) linked to Cases for support |
| **WhatsApp Journey** | Pre-visit (confirmation, prep instructions); Post-visit (reports, feedback) |
| **Insurance** | Custom fields for insurance provider, policy number, pre-auth status |
| **Campaign Tracking** | UTM → CRM field mapping; which department ad → which specialist |
| **Corporate Tie-ups** | Custom module "Corporate Accounts" — companies for employee health checks |
| **Telemedicine** | Cases + Video (Zoom integration) for online consultation |
| **Analytics** | Dashboard: Appointments per department, Conversion enquiry→visit, Revenue per specialty |
| **Follow-up Sequences** | Workflow: No show → Reminder SMS; Post-discharge → Day 3 follow-up |
| **Feedback** | Post-visit email survey via Zoho Survey → sentiment analysis by Zia |

### Custom Fields
- `Department` (dropdown)
- `Insurance_Provider`
- `Policy_Number`
- `Appointment_Type` (New/Review/Emergency)
- `Attending_Doctor` (lookup)
- `Pre_auth_Status`
- `Corporate_Patient` (checkbox)
- `Treatment_Type`

---

## 🏠 INDUSTRY 3: RESIDENTIAL REAL ESTATE

### Business Context
Apartment/villa projects. Customer journey: Ad → Website visit → Site visit → Booking → Registration → Possession.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Facebook/Instagram Lead Ads (by BHK, location, budget); website enquiry form |
| **Lead Scoring** | Zia — Score on: site visit booked, brochure downloaded, pricing viewed, loan interest |
| **Assignment** | Territory assignment by project location → sales rep |
| **Project Catalog** | Custom module "Projects" linked to Deals; fields: location, price/sqft, possession date |
| **Unit Inventory** | Custom module "Inventory" — Track available units by tower/floor/BHK |
| **Site Visit Scheduling** | Custom module "Site Visits"; workflow → WhatsApp reminder 24hrs before |
| **WhatsApp Outreach** | Send floor plans, 3D visuals, price PDF, location advantages |
| **Booking Workflow** | Blueprint: Enquiry → Site Visit → Expression of Interest → Booking → Agreement → Registration |
| **Payment Tracking** | Zoho Books linked to Deals; milestone-based payment schedule |
| **Loan Tracking** | Custom fields for loan status, bank, approved amount |
| **Possession** | Workflow: Post-registration → Handover checklist → Possession date reminder |
| **Referral Program** | Custom module "Referrals"; macro to generate referral bonus tracking |
| **Analytics** | Dashboard: Leads by project, Conversion rate, Avg booking value, Pipeline by stage |
| **Marketing** | Retargeting: Custom audience from CRM → Facebook; festive SMS campaigns |

### Custom Fields
- `Project_Name` (lookup)
- `Unit_Number`
- `Tower_Name`
- `Floor`
- `BHK_Type` (dropdown: 1BHK, 2BHK, 3BHK, 4BHK)
- `Carpet_Area`
- `Price_Per_Sqft`
- `Total_Price`
- `Booking_Status` (dropdown)
- `Loan_Required` (checkbox)
- `Possession_Date`
- `Source_Channel`

---

## 🏫 INDUSTRY 4: EDUCATION (SCHOOLS & COACHING)

### Business Context
K-12 schools, coaching institutes, colleges. Journey: Ad → Enquiry → Visit → Admission → Engagement → Alumni.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Facebook Lead Ads (by class, exam: JEE, NEET, UPSC); website enquiry |
| **Demo Class Tracking** | Custom module "Demo Classes" linked to Leads |
| **Lead Scoring** | Zia — Score on: demo attended, board preference, location, budget |
| **Assignment** | Round-robin or territory: by locality → admission counselor |
| **WhatsApp Outreach** | Admission confirmations, fee structure, EMI options, event invites |
| **Visit Scheduling** | Custom module "School Visits" → WhatsApp calendar invite |
| **Fee Management** | Zoho Books — Fee collection, receipt generation |
| **Batch Assignment** | Custom module "Batches" linked to Students |
| **Attendance Tracking** | Custom module "Attendance"; parent notification via WhatsApp |
| **Progress Reports** | Custom module "Academic Records" linked to Students |
| **Parent Communication** | WhatsApp API — Daily homework, test results, event updates |
| **Event Management** | Custom module "Events" → invitation tracking + follow-up |
| **Coaching Institute** | Batch-wise schedule, test performance tracking, rank management |
| **College Add-ons** | Alumni network, placement tracking, counselling booking |
| **Analytics** | Dashboard: Enquiries by source, Admission conversion rate, Batch occupancy |
| **Marketing** | Seasonal SMS (exam season, new batch opening); referral program |

### Custom Fields
- `Class_Interest`
- `Board` (CBSE, ICSE, State)
- `Demo_Attended` (checkbox)
- `Parent_Name`
- `Fee_Structure`
- `Batch_Allocated`
- `Attendance_Percent`
- `Test_Rank`
- `Scholarship_Eligible`

---

## 🏨 INDUSTRY 5: HOSPITALITY (HOTELS & RESTAURANTS)

### Business Context
Hotels, resorts, restaurants. Journey: Ad → Enquiry → Booking → Stay/Dine → Review → Loyalty.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Google Ads + Instagram Lead Ads; website booking engine |
| **Lead Scoring** | Zia — Score on: dates selected, room type viewed, package viewed, group booking |
| **Booking Source Tracking** | UTM → CRM; Direct vs OTA vs Partner vs Ad |
| **WhatsApp Outreach** | Booking confirmations, pre-arrival details, offers, upsells |
| **Room Availability** | Custom module "Room Inventory" with real-time availability tracking |
| **Dynamic Pricing** | Formula fields: Base price × seasonal multiplier × demand factor |
| **Upsell Engine** | Workflow: Booking confirmed → Upgrade offer via WhatsApp (room, spa, dining) |
| **Telephony** | Zoho Voice for reservation calls; IVR for 24/7 booking |
| **Guest Preferences** | Custom fields: Dietary, room preference, occasion (anniversary, birthday) |
| **Event/Banquet Booking** | Custom module "Events" — with Blueprint: Enquiry → Proposal → Confirmation |
| **Post-Stay** | Feedback survey via Zoho Survey → Zia sentiment analysis |
| **Loyalty Program** | Custom module "Memberships" with points tracking |
| **Retargeting** | 30 days post-stay → "We miss you" WhatsApp + exclusive offer |
| **Analytics** | Dashboard: Occupancy rate, RevPAR, Booking source mix, Avg spend per guest |
| **OTA Management** | Integration with MakeMyTrip, OYO; sync bookings via API |

### Custom Fields
- `Check_In_Date`
- `Check_Out_Date`
- `Room_Type` (dropdown)
- `Guest_Count`
- `Special_Occasion`
- `Dietary_Requirements`
- `Booking_Source` (dropdown)
- `Loyalty_Points`
- `Total_Spend`

---

## 🚗 INDUSTRY 6: AUTOMOTIVE (DEALERSHIPS & SERVICE)

### Business Context
Vehicle sales, service, accessories. Journey: Ad → Test Drive → Purchase → Service → AMC → Resale.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Facebook/Instagram Lead Ads (by vehicle type: SUV, Sedan, EV; fuel type) |
| **Lead Scoring** | Zia — Score on: test drive booked, specs viewed, finance calculator used, exchange interest |
| **Vehicle Catalog** | Products module with variants: model, variant, color, fuel |
| **Test Drive Booking** | Custom module "Test Drives" linked to Leads; WhatsApp reminder |
| **Financing** | Custom fields: Loan required, down payment, tenure; integrate with NBFC partners |
| **Exchange Vehicle** | Custom module "Exchange" — vehicle details, valuation |
| **Sales Pipeline** | Blueprint: Enquiry → Test Drive → Finance Discussion → Order → Delivery |
| **Insurance & Accessories** | Cross-sell workflow at order stage: accessories, extended warranty |
| **Delivery Tracking** | Workflow: Vehicle dispatched → WhatsApp to customer; ETA update |
| **Service Booking** | Cases module for service appointments; AMC plans as Products |
| **Service History** | All service records linked to Contact + Vehicle (custom module) |
| **AMC/NAC Tracking** | Custom module "AMC Contracts" with renewal reminders |
| **WhatsApp Post-Service** | Feedback request + next service reminder |
| **Resale/Buyback** | Custom module "Resale"; workflow to invite back for new vehicle |
| **Analytics** | Dashboard: Test drive conversion, Booking-to-delivery ratio, Service revenue, AMC renewal rate |

### Custom Fields
- `Vehicle_Model`
- `Variant`
- `Color`
- `Fuel_Type`
- `Exchange_Vehicle`
- `Finance_Required`
- `Test_Drive_Status`
- `Delivery_Date`
- `Registration_Number`

---

## 💪 INDUSTRY 7: FITNESS & GYMS

### Business Context
Gyms, yoga studios, personal training. Journey: Ad → Trial → Membership → Engagement → Retention → Referral.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Facebook Lead Ads (by interest: weight loss, muscle gain, yoga, HIIT); Instagram |
| **Lead Scoring** | Zia — Score on: trial booked, plan viewed, trainer preference indicated |
| **Trial Class Booking** | Custom module "Trial Classes"; WhatsApp confirmation + reminder |
| **Fitness Assessment** | Custom module "Assessments" — goals, body metrics, health history |
| **Program Recommendation** | Formula field: Based on goal + assessment → recommended program |
| **WhatsApp Outreach** | Trial reminder, membership details, EMI/payment plan, transformation stories |
| **Membership Plans** | Products with variants: Monthly, Quarterly, Annual, PT, Group |
| **Attendance Tracking** | Custom module "Attendance"; SMS if连续3 days absent |
| **Progress Tracking** | Custom module "Progress Reports" linked to Members |
| **Batch/Class Schedule** | Custom module "Classes" with timing, trainer, capacity |
| **Trainer Assignment** | Assignment rules: Trainer → Member (by locality or preference) |
| **Renewal Workflow** | Workflow: 15 days before expiry → WhatsApp renewal offer |
| **Upsell/Cross-sell** | Macro: Yoga member → "Add Personal Training"; Gym member → Nutrition plan |
| **Referral Program** | Custom module "Referrals"; automated reward tracking |
| **Corporate Tie-ups** | Custom module "Corporate Accounts" — bulk membership for offices |
| **Analytics** | Dashboard: Lead conversion rate, Monthly recurring revenue, Churn rate, Attendance trends |

### Custom Fields
- `Fitness_Goal` (dropdown)
- `Preferred_Program`
- `Trial_Date`
- `Membership_Plan`
- `Trainer_Assigned` (lookup)
- `Batch_Timing`
- `Joining_Date`
- `Expiry_Date`
- `Attendance_Last_7_Days`

---

## 🛒 INDUSTRY 8: RETAIL & E-COMMERCE

### Business Context
Fashion, accessories, QSR, quick commerce. Journey: Ad → Browse → Cart → Order → Delivery → Review → Loyalty.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | Facebook/Instagram Lead Ads; Google Shopping Ads; website |
| **Lead Scoring** | Zia — Score on: product viewed, size checked, cart started, wishlist added |
| **Source Tracking** | UTM parameters → CRM field mapping; which channel → which product interest |
| **WhatsApp Outreach** | Order confirmation, delivery update, cart abandonment, review request |
| **Cart Recovery** | Workflow: Cart abandoned → WhatsApp with cart items + discount code |
| **Inventory Tracking** | Products module with stock levels; low-stock alerts via workflow |
| **Order Management** | Zoho Books + Inventory integration; order status updates via WhatsApp |
| **Loyalty Program** | Custom module "Loyalty Points" linked to Contacts |
| **Personalization** | Zia: Based on purchase history → "You might like these" recommendations |
| **QSR-specific** | Order source (Zomato, Swiggy, direct) tracked; retargeting to move offline |
| **Size/Restock Alert** | Workflow: Product out of stock → Notify interested leads when back |
| **Festival Campaigns** | Mass SMS/WhatsApp for Diwali, New Year, anniversary sales |
| **Analytics** | Dashboard: Orders by channel, AOV, Repeat purchase rate, Cart abandonment rate |

### Custom Fields
- `Size_Preference`
- `Product_Interest`
- `Order_Source` (dropdown: Direct, Zomato, Swiggy, Myntra, etc.)
- `Loyalty_Points_Balance`
- `Cart_Value`
- `Preferred_Delivery_Slot`

---

## ⚡ INDUSTRY 9: IT SERVICES & SaaS

### Business Context
B2B IT services, software sales, digital agencies. Journey: LinkedIn Ad → Demo → Proposal → Contract → Delivery → Renewal.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | LinkedIn Lead Ads; website demo request form |
| **Lead Scoring** | Zia — Score on: company size, industry, budget indicator, demo booked |
| **Demo Scheduling** | Custom module "Demos" linked to Leads; Calendar booking |
| **Proposal/CBQ** | Deals module with CPQ extension; multi-product bundle quoting |
| **Contract Management** | Custom module "Contracts" with renewal dates; SLA reminders |
| **Project Delivery** | Custom module "Projects" linked to Accounts; milestone tracking |
| **Billing** | Zoho Books integration; milestone-based invoicing |
| **Upsell Engine** | Zia: When project 80% complete → trigger upsell conversation |
| **NPS Feedback** | Zoho Survey → NPS score → Zia sentiment → Workflow for low NPS |
| **Partner/Channel Management** | Custom module "Partners" with referral commission tracking |
| **Analytics** | Dashboard: Pipeline by service line, Win rate by industry, Avg contract value, Renewal rate |
| **Marketing Automation** | Zoho Campaign for nurture sequences based on service interest |

### Custom Fields
- `Company_Size` (employees)
- `IT_Budget`
- `Demo_Scheduled`
- `Solution_Interest` (multi-select)
- `Contract_Value`
- `Contract_Start_Date`
- `Contract_End_Date`
- `NPS_Score`

---

## 🏗️ INDUSTRY 10: CONSTRUCTION & REAL ESTATE (COMMERCIAL)

### Business Context
Commercial real estate, interiors, construction materials. Journey: Ad → Enquiry → Site Visit → Proposal → Deal → Execution → Repeat.

### Zoho CRM Feature Mapping

| Stage | Zoho Feature Used |
|-------|------------------|
| **Lead Capture** | LinkedIn + Google Ads; website RFQ form |
| **Lead Scoring** | Zia — Score on: space requirement, location interest, budget, timeline |
| **Property Inventory** | Custom module "Properties" (commercial spaces); linked to Deals |
| **Site Visit Scheduling** | Custom module "Site Visits"; WhatsApp with directions + checklist |
| **Broker Management** | Custom module "Brokers" with commission tracking |
| **Proposal/Quotation** | Quotes module with custom terms; E-sign via Zoho Sign |
| **Blueprint** | Blueprint: Enquiry → Site Visit → Proposal → Negotiation → LOI → Agreement |
| **Project Management** | Custom module "Projects" linked to Accounts; milestone workflows |
| **Payment Tracking** | Zoho Books linked to Deals; milestone billing |
| **Interiors-specific** | Custom module "Designs" linked to Projects; design approval workflow |
| **Follow-up** | Zia Best Next Action → Manager gets alert if deal stalled 14+ days |
| **Analytics** | Dashboard: Pipeline by property type, Avg lease value, Conversion rate, Broker performance |

### Custom Fields
- `Property_Type` (Office/Retail/Warehouse)
- `Area_Required_SqFt`
- `Location_Preference`
- `Budget_Per_SqFt`
- `Lease_Type` (Direct/BOOT)
- `Timeline`
- `Broker_ID`
- `Design_Required`

---

## 🔋 INDUSTRY 11: SOLAR ENERGY (EXPANDED — Corporate & Housing Societies)

### Additional Use Cases Beyond Residential

#### Corporate Solar (MW-scale)
- **Lead:** LinkedIn targeting manufacturing plants, warehouses
- **Custom module:** "Corporate Solar Projects" with MW capacity, land/roof type, timeline
- **Multi-stakeholder:** Decision-makers tracked as Contacts with roles (CFO, Ops Head)
- **Proposal:** Large deal → multi-approval workflow → legal review
- **Analytics:** Pipeline MW capacity, conversion by industry, avg project value

#### Housing Society Rooftop
- **WhatsApp group:** Society secretary + all interested residents
- **Bulk booking:** Custom module "Society Subscriptions" per flat
- **Maintenance tracking:** AMC linked to society Account
- **Referral:** Society champion gets referral fee per additional subscriber

---

## 🌍 PART 3: CROSS-INDUSTRY PLAYBOOKS

---

### PLAYBOOK A: THE FULL LEAD NURTURE SEQUENCE (Any Industry)

```
Day 0: Lead captured (Facebook/Website/Form)
  ↓ Workflow: Auto-assign round-robin
  ↓ Workflow: Send welcome email + SMS
  ↓ Zia: Score lead (1-100)

Day 1-3: Follow-up
  If score > 70 (Hot) → WhatsApp: "Thanks for your interest! Can I call you today?"
  If score 40-70 (Warm) → Email: Nurture content (case study / brochure)
  If score < 40 (Cold) → Enter drip sequence

Day 7:
  Hot → Call logged → WhatsApp with product demo video
  Warm → 2nd email with testimonial

Day 14:
  Hot → Proposal/Quote → WhatsApp PDF
  Warm → 3rd email with limited-time offer

Day 21:
  No response → Send via WhatsApp: "Just checking in — still interested?"
  Still cold → Assign to re-engagement queue

Day 30:
  Cold → Retarget ad via Facebook custom audience (from CRM)
```

### PLAYBOOK B: WHATSAPP AUTOMATION TEMPLATES

| Template Category | Use Case | Template Name |
|-------------------|----------|---------------|
| **Marketing** | Festival offer | "🎉 {First_Name}! Solar panel installation starting at ₹{price}/month. Govt subsidy available. Reply YES for free site survey!" |
| **Utility** | Appointment confirmation | "Hi {First_Name}, your site visit is confirmed for {Date} at {Time}. Our engineer will call you 30 mins before. Reply HELP for any questions." |
| **Utility** | Payment reminder | "Hi {First_Name}, your EMI of ₹{amount} is due on {Date}. Pay now: {payment_link}" |
| **Marketing** | Abandoned cart | "👋 {First_Name}, you viewed {product_name} but didn't complete booking. 10% extra discount ends in 24hrs! {link}" |
| **Utility** | Delivery update | "📦 {First_Name}, your order is dispatched! Tracking: {link}. Expected delivery: {Date}" |
| **Marketing** | Urgency | "⚡ {First_Name}, only {seats} spots left in our {date} batch! Book now: {link}" |
| **Marketing** | Re-engagement | "We miss you, {First_Name}! It's been {days} since your last visit. Here's 20% off your next session: {code}" |

### PLAYBOOK C: ZIA AI PLAYBOOK

| Zia Feature | Industry Application |
|------------|-------------------|
| **Lead Scoring** | Solar: Score on roof type + budget + electricity bill → hot vs cold |
| **Deal Prediction** | Real Estate: Which deal will actually close this quarter? |
| **Sentiment Analysis** | Hospitality: Flag negative email reviews immediately |
| **Best Next Action** | Gym: "Best time to call this lead is Tuesday 3-4 PM" |
| **Anomaly Detection** | Solar: "Win rate dropped 30% for residential this month — investigate" |
| **Activity Capture** | Auto-log all emails/calls so sales rep focuses on talking |
| **Zia Voice** | Field rep asks: "Show my Bangalore solar leads closing this week" |

### PLAYBOOK D: BLUEPRINT TEMPLATES BY INDUSTRY

#### Solar Installation Blueprint:
```
Lead Created
  ↓
Site Survey Booked → Task: "Confirm date with customer"
  ↓
Site Survey Completed → Fields: Roof_Type, System_Size, Shading_Factor
  ↓
Proposal Created → Deal auto-created with amount from calculator
  ↓
Customer Approval → Email quote + WhatsApp summary
  ↓
Document Collection → Task: "Get electricity bill, ID proof"
  ↓
Installation Scheduled → Field team notified
  ↓
Installation Completed → Inspections booked
  ↓
Meter Connection → MESCOC/DISCOM workflow triggered
  ↓
Handover → AMC offer presented
  ↓
AMC Active / Closed Won
```

#### Coaching Institute Enrollment Blueprint:
```
Enquiry Received
  ↓
Demo Class Scheduled → SMS reminder 24hrs before
  ↓
Demo Class Attended → Update: Demo_Attended = Yes
  ↓
Counseling Session → Create Task for counselor
  ↓
Fee Structure Shared → Send via WhatsApp + Email
  ↓
Admission Form Submitted → Documents uploaded
  ↓
Fee Payment → Zoho Books invoice generated
  ↓
Batch Allocated → Timetable shared via WhatsApp
  ↓
Ongoing: Attendance tracked, Progress shared monthly
  ↓
Renewal → 30 days before expiry → WhatsApp renewal offer
```

---

## 📊 PART 4: ANALYTICS & DASHBOARD TEMPLATES

---

### Dashboard 1: Sales Manager (Any Industry)
```
┌─────────────────────────────────────────────────────────────┐
│ TODAY'S NUMBERS                                              │
├─────────────┬─────────────┬──────────────┬─────────────────┤
│ New Leads   │ Deals Today │ Revenue Today│ Calls Made       │
│    23       │     5       │   ₹8,50,000   │      47          │
└─────────────┴─────────────┴──────────────┴─────────────────┘

Pipeline Health:
[PIPELINE VALUE: ₹45L] [CLOSING THIS MONTH: ₹12L] [WIN RATE: 32%]

Top 3 At-Risk Deals (Zia Alert):
⚠️ Sunbeam Industries — No activity 18 days
⚠️ Greenfield Apartments — Champion left company
⚠️ Apex Solutions — Budget reduced by 40%

Team Leaderboard:
🥇 Rahul — 142% quota
🥈 Priya — 118% quota  
🥉 Arjun — 89% quota
```

### Dashboard 2: Solar Business (Bangalore-Specific)
```
┌─────────────────────────────────────────────────────────────┐
│ SOLAR PIPELINE — BANGALORE                                   │
├────────────────┬────────────────┬───────────────────────────┤
│ This Month     │ This Quarter   │ This Year                  │
│ ₹18,00,000     │ ₹52,00,000     │ ₹2,10,00,000               │
└────────────────┴────────────────┴───────────────────────────┘

Lead Sources:
[Google Ads: 45%] [Facebook: 30%] [Referral: 15%] [Organic: 10%]

Locality Hotspots:
HSR Layout: 23 hot leads | Whitefield: 18 hot leads
Marathahalli: 15 hot leads | Electronic City: 12 hot leads

Conversion Funnel:
Inquiries: 450 → Site Survey: 180 → Proposal: 90 → Won: 32
```

---

## 🔧 PART 5: IMPLEMENTATION PRIORITY ROADMAP

---

### Phase 1: Foundation (Week 1-2)
1. Setup Zoho CRM account with company branding
2. Configure roles + profiles (Admin, Manager, Sales Rep)
3. Customize layouts for Leads, Contacts, Deals, Accounts
4. Add custom fields specific to your industry
5. Setup WhatsApp Business API (apply to Meta, get templates approved)
6. Configure email + SMS channels
7. Import existing lead data via CSV

### Phase 2: Automation (Week 3-4)
1. Build Assignment Rules (round-robin + territory)
2. Create Workflow Rules for instant lead response
3. Build Blueprints for your core sales process
4. Setup WhatsApp templates for key use cases
5. Configure Zia Lead Scoring
6. Build first dashboard

### Phase 3: Integration (Week 5-6)
1. Connect Zoho Books for invoicing
2. Connect telephony (Zoho Voice or Twilio)
3. Setup Zoho Flow for third-party integrations
4. Connect Google Analytics for website tracking
5. Setup Facebook Lead Ads sync

### Phase 4: AI & Optimization (Week 7-8)
1. Train Zia with your historical data
2. Enable Zia Best Next Action for sales reps
3. Setup anomaly detection alerts
4. Build advanced analytics dashboards
5. A/B test WhatsApp templates
6. Implement retargeting campaigns

---

## 📝 NOTES FOR AI-NATIVE CRM BUILD

### Where AI Can Enhance Zoho CRM:
1. **Lead Intent Detection** — Analyze website behavior (heatmaps, scroll depth) → trigger CRM workflow
2. **Dynamic Lead Scoring** — Beyond Zia's 100 signals: add website intent data, WhatsApp engagement signals
3. **Conversational CRM** — Build a chatbot on WhatsApp that auto-logs all conversations into CRM
4. **Speech-to-Note** — After site visits, field rep speaks notes → transcribed into CRM via Whisper API
5. **Proposal Generation** — AI writes custom proposals based on deal data + industry templates
6. **Sentiment-Triggered Escalation** — If Zia flags negative sentiment → auto-create urgent task + WhatsApp alert
7. **Predictive Locality Scoring** — For solar: Score Bangalore localities by solar potential + competition
8. **Auto-ROI Calculator** — Show customers their exact savings with specific system size

### Solar CRM-Specific AI Features to Build:
- **Shading analysis from satellite images** → Estimate system output loss
- **Government subsidy calculator** → Auto-calculate MNRE subsidy based on system size + customer type
- **EMI optimizer** — Recommend best EMI tenure based on customer income
- **Lead-to-quote time** — Compress the proposal turnaround with AI
- **Weather API integration** — Factor in Bangalore's rainy season in installation timelines

---

*Document compiled: May 2026*
*Source: Zoho CRM Knowledge Base + Industry Use Case Analysis*
*Purpose: AI-Native CRM Build for Solar Solutions (Bangalore)*
