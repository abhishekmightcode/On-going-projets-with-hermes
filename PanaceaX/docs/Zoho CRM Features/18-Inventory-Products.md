# Inventory & Products

> **Feature ID:** `18-Inventory-Products`  
> **Knowledge Base Articles:** 204  
> **Last Updated:** 2026-05-05

## Overview

Products, price books, inventory modules, quotes, orders, invoices, purchase orders

---

## 1. Core Functionality

### 1. Zia Usage Data Mapping of Events

This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction. Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing. It enables seamless import of usage data from various sources into Zoho CRM, providing accurate insights on customer engagement, retention, and personalized service delivery. What is Usage Data? All businesses need transactional data as a base to study user purchase behavior on metrics like customer details, date and time, payment methods, discounts, and 
### 2. Setting up Zoho Creator Integration

Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account. You should have a Zoho Creator account with any edition. If you do not have a Zoho Creator account, please create an account from Zoho Create. An account with the Free Edition will be automatically created. After which you can proceed with integrating it with Zoho CRM. Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for testing. Applications where the production environment is enabled will only be listed to be integrated with Zoho CRM. Other applications that are not in the production environment will not be listed fo
### 3. Zia for Workflow Rules

You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people. However, keeping track of triggers made through workflow rules to see what works best and what doesn't could be cumbersome. Zia does just that for you. Zia brings AI to your workflow automation processes by detecting anomalies and provide suggestions for your workflow rules. Zia also identifies and prevents you from making mistakes, such as sending multiple email templates to the same customer on the same day. Availability Permission Required Users with manage Automation permission in their profile can access this feature. To view Workflow Anomalies and Suggestions from Zia Click Zia icon in the bottom right corner. You can click open the al
### 4. Capabilities of Zia in Zoho CRM— A perspective

Zoho CRM harnesses the transformative power of Artificial Intelligence (AI) to revolutionise decision-making across all critical areas of your business, from initial customer interactions to their entire journey. With Zia, AI-powered assistant, Zoho CRM offers valuable insights and suggestions that permeate every aspect of CRM management, including automation, customer engagement, analytics, and data management. Take a look at this video to understand how Zia can help your businesses Zia offers you the AI experience across the breadth of Zoho CRM under six key categories: Data Management Productivity Customer Experience Insights and Analytics Intelligent Alerts Customer engagement and retention. Data Management Zia facilitates data management in Zoho CRM by providing advanced capabilities 
### 5. RingCentral Video

Every business, no matter what size, deals with setting up professional meetings almost everyday. It can be a meeting with customers on a product demo or a discussion with the team members on a project, setting up a meeting is almost inevitable. Among other requirements, the most essential are identifying availability of the attendees, host and, the venue. Also, at times, conducting physical meetings take up a lot of time and money which is not feasible in every situation. As an alternative, online meetings doesn't involve these external factors. All you need to do is to decide a suitable time, and invite your attendees. You also need not worry about any geographical boundaries. Zoho CRM lets you integrate with RingCenral Video, a web conferencing solution to conduct online meetings. Once 
### 6. Zoho CRM for iPhone - An Overview

Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above. From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc. Availability Permission Required Administrators need to activate it for users in other profiles. Features Zia Voice - Call or Chat with Zia to get answers for all your questions in Zoho CRM. Spotlight - Spotlight Search lets you see the contact information that you are searching for in a jiffy. Proactive Suggestions - Proactive suggestions let you take the fastest route to make your sale. They allow the frequently used apps to predict the data and h
### 7. FAQs: Zoho CRM Integration with Zoho Desk

Why should I integrate Zoho CRM with Zoho Desk? Zoho Desk is a cloud-based help desk application that lets you manage and resolve your customer inquiries, complaints, and doubts along with offering self-help articles to help your customers resolve issues themselves. CRM lets your business acquire customers and make deals with them, but what about after-sales services? If your company is poor at providing after-sales services to your customers, it will directly impact your customer retention. Businesses need to be customer-centric and customers shall be the king, but this can only be achieved if you’re able to provide real-time support to your customers when they need you. Zoho Desk has been created keeping these factors in mind to empower your support team to assist your customers and impr
### 8. Survey Comparison

The Survey Comparison dashboard is extremely helpful for marketing exercises and also for improving your products/services based on customer feedback. If you want to analyze customer feedback specifically from surveys and draw insights by comparing a set of surveys and responses, this dashboard is for you. Zia makes an analysis of survey responses and provides you with details on the underlying sentiment and intent of those responses. In addition to this, Zia also gives you snapshot of competitor mentions and customer trend (promoters vs detractors) based on survey responses. You will also have detailed insights on the keywords that may have contributed to a high or low score on your NPS surveys and the underlying sentiments of those keywords so you have a quick picture of what predominant


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `INVENTORY`

**Standard Fields (inherited):**
- `Created_By` (User) — Record creator
- `Modified_By` (User) — Last modifier
- `Created_Time` (DateTime) — Creation timestamp
- `Modified_Time` (DateTime) — Last modification
- `Owner` (User) — Record owner for access control

**Key Articles:**
- `Zia Usage Data Mapping of Events`
- `Setting up Zoho Creator Integration`
- `Zia for Workflow Rules`
- `Capabilities of Zia in Zoho CRM— A perspective`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/inventory` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Inventory & Products - Example Implementation
// Triggered on record creation/update

if(input.module == "ZIA USAGE DATA MAPPING OF EVENTS")
{
    // This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important t
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

- [Deals-Pipeline](../Deals-Pipeline/README.md)
- [CPQ](../CPQ/README.md)
- [Analytics-Dashboards](../Analytics-Dashboards/README.md)

### This Feature Enables

- **Deals-Pipeline** — shares data model and workflows
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

### Zia Usage Data Mapping of Events
**Purpose:** This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is 

**Key Points:**
- This guide helps you with the mapping of events of your usage data under Zia.
- Before getting into greater detail, let's quickly revise the important terms.
- What is mapping of events? Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction.
- Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing.
- It enables seamless import of usage data from various sou


### Setting up Zoho Creator Integration
**Purpose:** Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Z

**Key Points:**
- Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account.
- You should have a Zoho Creator account with any edition.
- If you do not have a Zoho Creator account, please create an account from Zoho Create.
- An account with the Free Edition will be automatically created.
- After which you can proceed with integrating it with Zoho CRM


### Zia for Workflow Rules
**Purpose:** You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people. However, keeping track of triggers made through w

**Key Points:**
- You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people.
- However, keeping track of triggers made through workflow rules to see what works best and what doesn't could be cumbersome.
- Zia does just that for you.
- Zia brings AI to your workflow automation processes by detecting anomalies and provide suggestions for your workflow rules.
- Zia also identifies and prevents you from making mistakes, such as sendin


### Capabilities of Zia in Zoho CRM— A perspective
**Purpose:** Zoho CRM harnesses the transformative power of Artificial Intelligence (AI) to revolutionise decision-making across all critical areas of your business, from initial customer interactions to their ent

**Key Points:**
- Zoho CRM harnesses the transformative power of Artificial Intelligence (AI) to revolutionise decision-making across all critical areas of your business, from initial customer interactions to their entire journey.
- With Zia, AI-powered assistant, Zoho CRM offers valuable insights and suggestions that permeate every aspect of CRM management, including automation, customer engagement, analytics, and data management.
- Take a look at this video to understand how Zia can help your businesses Zia offers


### RingCentral Video
**Purpose:** Every business, no matter what size, deals with setting up professional meetings almost everyday. It can be a meeting with customers on a product demo or a discussion with the team members on a projec

**Key Points:**
- Every business, no matter what size, deals with setting up professional meetings almost everyday.
- It can be a meeting with customers on a product demo or a discussion with the team members on a project, setting up a meeting is almost inevitable.
- Among other requirements, the most essential are identifying availability of the attendees, host and, the venue.
- Also, at times, conducting physical meetings take up a lot of time and money which is not feasible in every situation.
- As an alternative, onl


### Zoho CRM for iPhone - An Overview
**Purpose:** Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above

**Key Points:**
- Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone.
- 0 version of the native CRM app is available in iOS 8.
- From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc.
- Availability Permission Required Administrators need to activate it for users in other profiles.
- Features Zia Voice - Call or Chat with Zia to get answer


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

- [Zia Usage Data Mapping of Events](https://help.zoho.com/portal/en/kb/crm/articles/usage-data-event-mapping)
- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [Zia for Workflow Rules](https://help.zoho.com/portal/en/kb/crm/articles/zia-intelligence-automation)
- [Capabilities of Zia in Zoho CRM— A perspective](https://help.zoho.com/portal/en/kb/crm/articles/zia-overview)
- [RingCentral Video](https://help.zoho.com/portal/en/kb/crm/articles/ringcentral-video)
- [Zoho CRM for iPhone - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-iphone-an-overview)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [Survey Comparison](https://help.zoho.com/portal/en/kb/crm/articles/survey-comparison)
- [Zoho Survey Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-survey-crm-integration)
- [FAQs: Path Finder](https://help.zoho.com/portal/en/kb/crm/articles/faqs-path-finder)
- [Understanding and building reports](https://help.zoho.com/portal/en/kb/crm/articles/understanding-and-building-reports)
- [Setting up Email Sharing Permissions](https://help.zoho.com/portal/en/kb/crm/articles/setting-up-email-sharing-permissions)
- [Zoho Projects Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/overview-zoho-projects-crm-integration)
- [Using Zoho Finance Suite Integration](https://help.zoho.com/portal/en/kb/crm/articles/use-zoho-finance-suite-crm-integration)
- [Acting on VoC insights](https://help.zoho.com/portal/en/kb/crm/articles/acting-on-voc-insights)
- [Setting Field Updates](https://help.zoho.com/portal/en/kb/crm/articles/field-updates)
- [Cross sell analytics](https://help.zoho.com/portal/en/kb/crm/articles/cross-sell-analytic)
- [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/articles/webform-analytics)
- [Trello](https://help.zoho.com/portal/en/kb/crm/articles/trello)
- [Common COQL Errors](https://help.zoho.com/portal/en/kb/crm/articles/troubleshoot-coql)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/working-with-analytics-in-zoho-crm-android-app)
- [Bigin for Zoho CRM - FAQs](https://help.zoho.com/portal/en/kb/crm/articles/bigin-for-zoho-crm-faqs)
- [An overview of user management in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/an-overview-of-user-management-in-zoho-crm)
- [Migrating from Sugar CRM to Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/migrating-from-sugar-crm-to-zoho-crm)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
