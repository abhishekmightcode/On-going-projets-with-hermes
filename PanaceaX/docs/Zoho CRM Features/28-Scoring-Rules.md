# Scoring Rules

> **Feature ID:** `28-Scoring-Rules`  
> **Knowledge Base Articles:** 5  
> **Last Updated:** 2026-05-05

## Overview

Lead and contact scoring based on engagement, attributes, and behavioral signals

---

## 1. Core Functionality

### 1. Segmentation Analysis

Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account. This dashboard presents five charts and are as follows. The Segmentation Analytics category on VoC is designed to offer you insights about the sentiments and keywords from segmented customers based on their labels created using RFM values. Analyzing customer behavior based on their recent purchase (R), frequent purchase (F), and monetary value (M) will help you decide on a better customer retention strategy. The different labels based on your customers' RFM scores help understand each customer's position in the sales cycle and take appropriate actions. The 5 charts lay out segmented customers based on scoring labels for these RFM values. These charts hel
### 2. Sales process: Lead engagement

Edition : Paid editions | Industry : Applicable for all industries | Features : Integrations with Zoho products and built-in features In the Lead Generation use case, we saw the marketing strategies used by Orange Interiorz to generate leads and capture them in CRM. In the next step, they engage the leads and qualify them for sales. Their lead engagement process is as follows: The sales team gets notifications whenever a lead is added to CRM so they can immediately begin the follow-up process. They prioritize the leads based on their responsiveness to different touch points used for contact and follow-up. This helps them move interested leads down the sales funnel faster. They contact hot leads via call and email and after they qualify these leads, the sales team passes them over to the de
### 3. Kaizen posts 2023: API series

Here is a complete list of Kaizen posts related to APIs published in 2023. Sl No Title Description 1 Scoring Rules - Part -1 Learn about scoring rules and how to create, delete, update and execute scoring rule APIs 2 Scoring Rules - Part -2 Learn about active and deactivate scoring roles, cloning scoring rules and getting a record's scoring rule using API 3 Portal APIs - Part I Learn about portals in Zoho CRM, and how to fetch, create and update a portal via APIs, and also how to fetch the portal user types, invite users to a portal, and get users of a particular user type via APIs. 4 Portal APIs - Part II Explore more of Portal APIs: Manage user types & access; create, update, delete; transfer users; change status; delete users from the portal for efficient user management. 5 User's Unava
### 4. Zia Scores

Zia Scores - Scope and benefits: Every lead or customer a business encounters is unique, and they all have different thought processes before making a purchase. While there are many ways to understand a customer's point of view, segmentation is a proven method. By segmenting customers in a CRM system based on various factors, such as interactions, support approach, demographics, customer journey, deal history, revenue spent, and conversion period, businesses can better understand which customers require attention, which ones to focus on, and what the next step in the sales cycle should be. Why Zia Scores? What if instead of you having to set up these rules manually, you had Zoho's artificial intelligent assistant automatically score records of any module in your system and make your job ea
### 5. Zoho CRM's Core Data Model and How You Extend It Safely

Zoho CRM ships with a complete set of standard modules covering every stage of the sales cycle, and gives your team structured, governed ways to extend that model as your business grows. Here is how the core data model is built, what it covers, and how customisation stays controlled. The core modules Zoho CRM includes foundational modules such as Leads, Accounts, Contacts, Deals, Forecasts, and Activities, along with extended modules like Campaigns, Products, Price Books, and CPQ. Together, these form a holistic platform that supports the entire sales and marketing lifecycle. What each one does: Leads: Unqualified prospects collected from web forms, trade shows, campaigns, or manual entry. When a rep qualifies a lead, it converts automatically into a Contact, Account, and Deal. Field mappi


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `SCORING`

**Standard Fields (inherited):**
- `Created_By` (User) — Record creator
- `Modified_By` (User) — Last modifier
- `Created_Time` (DateTime) — Creation timestamp
- `Modified_Time` (DateTime) — Last modification
- `Owner` (User) — Record owner for access control

**Key Articles:**
- `Segmentation Analysis`
- `Sales process: Lead engagement`
- `Kaizen posts 2023: API series`
- `Zia Scores`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/scoring` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Scoring Rules - Example Implementation
// Triggered on record creation/update

if(input.module == "SEGMENTATION ANALYSIS")
{
    // Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account. This dashboa
}
```

### Architectural Pattern

```
User Action -> CRM Record Created/Updated 
    |
Workflow Rule Evaluated (if configured)
    |
Actions Executed:
  - Field Updates
  - Email Notifications  
  - Task Creation
  - Webhook Calls
  - Deluge Function Execution
    |
Record State Changed
    |
Related Records Updated (via lookup)
    |
Analytics/Reports Updated
```

---

## 3. Relationship With Other CRM Features

### Dependencies

- [Leads-Management](../Leads-Management/README.md)
- [Contacts-Management](../Contacts-Management/README.md)
- [Assignment-Rules](../Assignment-Rules/README.md)
- [Zia-AI](../Zia-AI/README.md)

### This Feature Enables

- **Leads-Management** — shares data model and workflows
- **Analytics** — generates reports based on this module's data
- **Automation** — triggers workflows based on record changes
- **Mobile** — fully accessible via Zoho CRM mobile apps

### Interaction Patterns

| Pattern | Description |
|---------|-------------|
| Parent-Child | Module can have sub-modules (subforms) |
| Lookup | References records from other modules |
| Related List | Shows associated records from other modules |
| Workflow Trigger | Changes in this module trigger automation |

---

## 4. Standalone Functions

### Segmentation Analysis
**Purpose:** Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account. This dashboard presents five charts and are as follows. The Se

**Key Points:**
- Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account.
- This dashboard presents five charts and are as follows.
- The Segmentation Analytics category on VoC is designed to offer you insights about the sentiments and keywords from segmented customers based on their labels created using RFM values.
- Analyzing customer behavior based on their recent purchase (R), frequent purchase (F), and monetary value (M) will help yo


### Sales process: Lead engagement
**Purpose:** Edition : Paid editions | Industry : Applicable for all industries | Features : Integrations with Zoho products and built-in features In the Lead Generation use case, we saw the marketing strategies u

**Key Points:**
- Edition : Paid editions | Industry : Applicable for all industries | Features : Integrations with Zoho products and built-in features In the Lead Generation use case, we saw the marketing strategies used by Orange Interiorz to generate leads and capture them in CRM.
- In the next step, they engage the leads and qualify them for sales.
- Their lead engagement process is as follows: The sales team gets notifications whenever a lead is added to CRM so they can immediately begin the follow-up process


### Kaizen posts 2023: API series
**Purpose:** Here is a complete list of Kaizen posts related to APIs published in 2023. Sl No Title Description 1 Scoring Rules - Part -1 Learn about scoring rules and how to create, delete, update and execute sco

**Key Points:**
- Here is a complete list of Kaizen posts related to APIs published in 2023.
- Sl No Title Description 1 Scoring Rules - Part -1 Learn about scoring rules and how to create, delete, update and execute scoring rule APIs 2 Scoring Rules - Part -2 Learn about active and deactivate scoring roles, cloning scoring rules and getting a record's scoring rule using API 3 Portal APIs - Part I Learn about portals in Zoho CRM, and how to fetch, create and update a portal via APIs, and also how to fetch the porta


### Zia Scores
**Purpose:** Zia Scores - Scope and benefits: Every lead or customer a business encounters is unique, and they all have different thought processes before making a purchase. While there are many ways to understand

**Key Points:**
- Zia Scores - Scope and benefits: Every lead or customer a business encounters is unique, and they all have different thought processes before making a purchase.
- While there are many ways to understand a customer's point of view, segmentation is a proven method.
- By segmenting customers in a CRM system based on various factors, such as interactions, support approach, demographics, customer journey, deal history, revenue spent, and conversion period, businesses can better understand which customers


### Zoho CRM's Core Data Model and How You Extend It Safely
**Purpose:** Zoho CRM ships with a complete set of standard modules covering every stage of the sales cycle, and gives your team structured, governed ways to extend that model as your business grows. Here is how t

**Key Points:**
- Zoho CRM ships with a complete set of standard modules covering every stage of the sales cycle, and gives your team structured, governed ways to extend that model as your business grows.
- Here is how the core data model is built, what it covers, and how customisation stays controlled.
- The core modules Zoho CRM includes foundational modules such as Leads, Accounts, Contacts, Deals, Forecasts, and Activities, along with extended modules like Campaigns, Products, Price Books, and CPQ


---

## 5. Use Cases Across Industries

### Implementation Matrix

| Industry | Priority | Complexity | Key Customization |
|----------|----------|------------|-------------------|
| EdTech / Schools | High | Medium | Custom fields + Workflows |
| Solar / Renewable Energy | High | Medium | Custom fields + Workflows |
| Healthcare | High | Medium | Custom fields + Workflows |
| Real Estate | High | Medium | Custom fields + Workflows |
| BFSI | High | Medium | Custom fields + Workflows |
| Manufacturing | High | Medium | Custom fields + Workflows |
| Retail / E-commerce | High | Medium | Custom fields + Workflows |
| Hospitality | High | Medium | Custom fields + Workflows |

### Industry-Specific Patterns

**EdTech / Schools** — Student inquiry management, enrollment pipeline, course tracking
**Solar / Renewable Energy** — Site assessment pipeline, proposal workflow, project milestones
**Healthcare** — Patient inquiry, appointment scheduling, treatment plan tracking
**Real Estate** — Property inquiry to closing, viewing scheduling, document management
**BFSI** — Loan application processing, policy enrollment, compliance workflows
**Manufacturing** — Inquiry to order pipeline, production scheduling, quality checks
**Retail** — Order processing, customer onboarding, post-purchase engagement
**Hospitality** — Booking inquiry to confirmation, event planning, preference tracking

---

## 6. User Workflow Use Cases

### Workflow A: Standard Record Lifecycle

```
1. Record Created (manual, webform, or API)
2. Assignment Rule assigns owner (if configured)
3. Workflow triggers -> Field updates, tasks created
4. User updates fields based on interaction
5. Stage/Status changed -> triggers next workflow
6. Related records linked (Contacts, Deals, etc.)
7. Approval initiated (if threshold met)
8. Record finalized -> Analytics captured
```

### Workflow B: Automated Engagement

```
1. New record enters system
2. Scoring rules evaluated -> Score calculated
3. Assignment based on score + territory
4. High-intent -> Immediate rep notification
5. Medium-intent -> Nurture sequence started
6. Low-intent -> Long-term campaign added
7. Zia analyzes pattern -> Suggests optimizations
```

### Workflow C: Multi-Stage Process

```
Stage 1: New/Incoming
  -> Auto-assign, send acknowledgment
  
Stage 2: In Progress
  -> Set reminder tasks, update fields
  
Stage 3: Pending Approval
  -> Lock record, notify approvers
  
Stage 4: Approved/Rejected
  -> Unlock, update status, trigger next steps
  
Stage 5: Completed/Closed
  -> Archive, generate report, trigger follow-up
```

---

## 7. Deeper Analysis

### Edge Cases

| Scenario | Handling |
|----------|----------|
| Duplicate record | Duplicate check workflow + merge option |
| Concurrent edit | Last-write-wins with audit log |
| Owner left company | Reassignment rule + manager backup |
| Mass import | Batch process with validation |
| API rate limit | Exponential backoff + queue |

### Performance Considerations

- **Query Optimization:** Use indexed fields for filters
- **Bulk Operations:** Batch API for 100+ records
- **Workflow Efficiency:** Avoid synchronous webhooks in high-volume triggers
- **Caching:** Frequently accessed layouts cached at app layer

### Security Model

```
Organization
  └── Roles (Sales Rep, Manager, Admin)
        └── Profiles (Standard, Limited, Read-Only)
              └── Field-Level Permissions (Visible, Editable, Hidden)
                    └── Record-Level Access (Owner, Assigned, All)
```

### Scalability

- **Horizontal:** Multi-node deployment for high availability
- **Vertical:** Increased compute for batch processing
- **Sharding:** Data partitioned by organization (multi-tenant)
- **CDN:** Static assets served via edge network

---

## Article Sources

- [Segmentation Analysis](https://help.zoho.com/portal/en/kb/crm/articles/segmentation-analysis)
- [Sales process: Lead engagement](https://help.zoho.com/portal/en/kb/crm/articles/sales-process-lead-engagement)
- [Kaizen posts 2023: API series](https://help.zoho.com/portal/en/kb/crm/articles/api-2023)
- [Zia Scores](https://help.zoho.com/portal/en/kb/crm/articles/scoring-rules-zia-scores)
- [Zoho CRM's Core Data Model and How You Extend It Safely](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-s-core-data-model-and-how-you-extend-it-safely)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
