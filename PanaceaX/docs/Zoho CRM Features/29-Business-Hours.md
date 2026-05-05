# Business Hours & SLAs

> **Feature ID:** `29-Business-Hours`  
> **Knowledge Base Articles:** 42  
> **Last Updated:** 2026-05-05

## Overview

Business hours configuration, SLA management, escalation rules

---

## 1. Core Functionality

### 1. Call analytics

Call analytics is a VoC dashboard that displays charts on key insights observed in your call correspondences. Importance of call analytics The conventional mode of communication, calls , are versatile and on-demand when it comes to understanding and resolving customer requirements. However, identifying and resolving issues on-the-go, is just one advantage of jumping into a call. Calls are an actual treasure trove that could reveal subtle cues that were not intentionally part of your agenda. Let's look at how call analytics can help your business! Discovering customer interests: Along your leng
### 2. Acting on VoC insights

In today's technologically-rich business market, companies are in close quarters with customers and their opinions. Through various channels, customers are expressing their contentment and discontentment; gratitude and grievances about your business. This is an opportunity to understand your customers truly and grow at scale. But, businesses just do not succeed by mere understanding their customers. Of course, understanding helps at a greater level. But, success lies in action. Your customers leave different kinds of feedback with distinct purposes like a complaint to report a fault, a suggest
### 3. FAQs: Zoho CRM for Google Apps

Why is information from Google Ads not populating for the CRM records? It could be possible that the Campaigns module is disabled in your CRM account. It is MANDATORY to have the Campaigns module enabled for proper functioning of Google Ads. However, note that information from GCLID will be populated even if the campaigns module is not enabled. How can I integrate CRM with Google Ads? Zoho CRM facilitates integration with Google Ads (formerly Google AdWords) so that you can have a clearer overview of the returns on your Google Ads investment. You are spending a significant amount of money on G
### 4. Working with Translations

Overview Many companies nowadays have a global presence, and to serve their customers better their employees are often stationed locally. With a CRM system, they can effectively manage to store sales and customer information in a common database, however, the employees may prefer to view the system in the language of their preference. Consider an organization headquartered in Germany operating in the US, Europe, Japan, and other regions. The locale set in CRM is Germany, and the preferred language is German. However, sales personnel entering information might prefer to view fields in English,
### 5. Zoho CRM Uptime SLA and Availability  

The SLA commitment Zoho's availability SLA commitment is 99.9% monthly uptime. We have redundancies implemented at various levels starting from the infrastructure to the ISP to achieve this. Data from the primary data center is replicated in the secondary, and a read-only version of Zoho apps is always served from the secondary data center. The 99.9% guarantee applies to monthly availability of the service. Three categories of downtime are excluded from this calculation: Planned maintenance: customers are notified at least 48 hours in advance of any scheduled updates. Factors outside Zoho's co
### 6. Set up your Organization Account

As an administrator your first step towards implementing Zoho CRM for your organization will involve entering details in the personal settings and defining the organization details, which will be visible to all users across the departments. You will also need to define the email settings in your CRM account and configure Motivator to keep your team members motivated by giving timely rewards and perks. Personal Settings First, personalize your CRM account by changing language and time zone. Then, you can set other personal preferences like date format, time format, number format, and so on. You
### 7. Managing Notes and Attachments

File attachments are documents, such as Marketing Collateral, Sales Quotes/Orders/Invoices, SLA, and others that can be associated to the CRM modules. Notes are the electronic equivalent of paper sticky notes. You can use the notes to write questions, reminders, and anything you would write on notepaper. These are useful for storing bits of information related to customers, which you may need later. File Storage We provide default storage based on your Zoho CRM Edition. Apart from this you can also purchase extra file storage at USD 4/month for 5 GB. Please note that the option to purchase add
### 8. CPQ for Zoho CRM — Scope, Purpose and Benefits

CPQ stands for Configure, Price, Quote. In simple words, CPQ is a software application designed to enable sales teams to create bespoke, accurate quotes for their customers, efficiently and quickly. CPQ is especially valuable when you have multiple product lines or service categories which involve dynamic pricing. With a good CPQ system, you will be able to: CONFIGURE multiple product combinations and bundles, based on how you wish to sell them. This way, every possible configuration is already saved in the system, and so, when it's time for you to send a quote to a customer, you do not have t


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `BUSINESS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Call analytics`
- `Acting on VoC insights`
- `FAQs: Zoho CRM for Google Apps`
- `Working with Translations`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/business` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Business Hours & SLAs - Example Implementation
// Triggered on record creation/update

if(input.module == "CALL ANALYTICS")
{
    // Call analytics is a VoC dashboard that displays charts on key insights observed in your call correspondences. Importance of call analytics The convent
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

- [Approval-Process](../Approval-Process/README.md)
- [Assignment-Rules](../Assignment-Rules/README.md)
- [Customer-Support](../Customer-Support/README.md)

### This Feature Enables

- **Approval-Process** -- shares data model and workflows
- **Analytics** -- generates reports based on this module's data
- **Automation** -- triggers workflows based on record changes
- **Mobile** -- fully accessible via Zoho CRM mobile apps

### Interaction Patterns

| Pattern | Description |
|---------|-------------|
| Parent-Child | Module can have sub-modules (subforms) |
| Lookup | References records from other modules |
| Related List | Shows associated records from other modules |
| Workflow Trigger | Changes in this module trigger automation |

---

## 4. Standalone Functions

### Call analytics
**Purpose:** Call analytics is a VoC dashboard that displays charts on key insights observed in your call correspondences. Importance of call analytics The conventional mode of communication, calls , are versatile

**Key Points:**
Call analytics is a VoC dashboard that displays charts on key insights observed in your call correspondences.
Importance of call analytics The conventional mode of communication, calls , are versatile and on-demand when it comes to understanding and resolving customer requirements.
However, identifying and resolving issues on-the-go, is just one advantage of jumping into a call.
Calls are an actual treasure trove that could reveal subtle cues that were not intentionally part of your agenda.
Let's look at how call analytics can help your business.
Discovering customer interests: Along your lengthy sale pipeline, you will have discussed varying subjects with your prospects and customers


### Acting on VoC insights
**Purpose:** In today's technologically-rich business market, companies are in close quarters with customers and their opinions. Through various channels, customers are expressing their contentment and discontentm

**Key Points:**
In today's technologically-rich business market, companies are in close quarters with customers and their opinions.
Through various channels, customers are expressing their contentment and discontentment; gratitude and grievances about your business.
This is an opportunity to understand your customers truly and grow at scale.
But, businesses just do not succeed by mere understanding their customers.
Of course, understanding helps at a greater level.
But, success lies in action


### FAQs: Zoho CRM for Google Apps
**Purpose:** Why is information from Google Ads not populating for the CRM records? It could be possible that the Campaigns module is disabled in your CRM account. It is MANDATORY to have the Campaigns module enab

**Key Points:**
Why is information from Google Ads not populating for the CRM records.
It could be possible that the Campaigns module is disabled in your CRM account.
It is MANDATORY to have the Campaigns module enabled for proper functioning of Google Ads.
However, note that information from GCLID will be populated even if the campaigns module is not enabled.
How can I integrate CRM with Google Ads.
Zoho CRM facilitates integration with Google Ads (formerly Google AdWords) so that you can have a clearer overview of the returns on your Google Ads investment


### Working with Translations
**Purpose:** Overview Many companies nowadays have a global presence, and to serve their customers better their employees are often stationed locally. With a CRM system, they can effectively manage to store sales

**Key Points:**
Overview Many companies nowadays have a global presence, and to serve their customers better their employees are often stationed locally.
With a CRM system, they can effectively manage to store sales and customer information in a common database, however, the employees may prefer to view the system in the language of their preference.
Consider an organization headquartered in Germany operating in the US, Europe, Japan, and other regions.
The locale set in CRM is Germany, and the preferred language is German.
However, sales personnel entering information might prefer to view fields in English, Japanese, or other regional languages.
To address this requirement, Zoho CRM provides an option to translate Modules, Subforms, Related Lists, Fields, and Picklist values to an individual's preferred language


### Zoho CRM Uptime SLA and Availability  
**Purpose:** The SLA commitment Zoho's availability SLA commitment is 99.9% monthly uptime. We have redundancies implemented at various levels starting from the infrastructure to the ISP to achieve this. Data from

**Key Points:**
The SLA commitment Zoho's availability SLA commitment is 99.
We have redundancies implemented at various levels starting from the infrastructure to the ISP to achieve this.
Data from the primary data center is replicated in the secondary, and a read-only version of Zoho apps is always served from the secondary data center.
9% guarantee applies to monthly availability of the service.
Three categories of downtime are excluded from this calculation: Planned maintenance: customers are notified at least 48 hours in advance of any scheduled updates.
Factors outside Zoho's control: ISP failures, natural disasters, denial-of-service attacks, and similar external events


### Set up your Organization Account
**Purpose:** As an administrator your first step towards implementing Zoho CRM for your organization will involve entering details in the personal settings and defining the organization details, which will be visi

**Key Points:**
As an administrator your first step towards implementing Zoho CRM for your organization will involve entering details in the personal settings and defining the organization details, which will be visible to all users across the departments.
You will also need to define the email settings in your CRM account and configure Motivator to keep your team members motivated by giving timely rewards and perks.
Personal Settings First, personalize your CRM account by changing language and time zone.
Then, you can set other personal preferences like date format, time format, number format, and so on.
You can also set up accessibility controls to make the CRM experience work for you.
Organization Settings Company details: Add your company details such as the company name for all your business communication, address, contact details, time zone, and also the company logo


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

**EdTech / Schools** -- Student inquiry management, enrollment pipeline, course tracking
**Solar / Renewable Energy** -- Site assessment pipeline, proposal workflow, project milestones
**Healthcare** -- Patient inquiry, appointment scheduling, treatment plan tracking
**Real Estate** -- Property inquiry to closing, viewing scheduling, document management
**BFSI** -- Loan application processing, policy enrollment, compliance workflows
**Manufacturing** -- Inquiry to order pipeline, production scheduling, quality checks
**Retail** -- Order processing, customer onboarding, post-purchase engagement
**Hospitality** -- Booking inquiry to confirmation, event planning, preference tracking

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
  |__ Roles (Sales Rep, Manager, Admin)
        |__ Profiles (Standard, Limited, Read-Only)
              |__ Field-Level Permissions (Visible, Editable, Hidden)
                    |__ Record-Level Access (Owner, Assigned, All)
```

### Scalability

- **Horizontal:** Multi-node deployment for high availability
- **Vertical:** Increased compute for batch processing
- **Sharding:** Data partitioned by organization (multi-tenant)
- **CDN:** Static assets served via edge network

---

## Article Sources

- [Call analytics](https://help.zoho.com/portal/en/kb/crm/articles/call-analytics)
- [Acting on VoC insights](https://help.zoho.com/portal/en/kb/crm/articles/acting-on-voc-insights)
- [FAQs: Zoho CRM for Google Apps](https://help.zoho.com/portal/en/kb/crm/articles/faqs-zoho-crm-for-google-apps)
- [Working with Translations](https://help.zoho.com/portal/en/kb/crm/articles/translations)
- [Zoho CRM Uptime SLA and Availability  ](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-uptime-sla-and-availability)
- [Set up your Organization Account](https://help.zoho.com/portal/en/kb/crm/articles/get-started-setup-organization-account)
- [Managing Notes and Attachments](https://help.zoho.com/portal/en/kb/crm/articles/manage-notes-and-attachments)
- [CPQ for Zoho CRM — Scope, Purpose and Benefits](https://help.zoho.com/portal/en/kb/crm/articles/what-is-cpq)
- [FAQs: Translation in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/faqs-translation-in-zoho-crm)
- [Exported language File](https://help.zoho.com/portal/en/kb/crm/articles/translation-file)
- [FAQs: Business Hours in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/faqs-business-hours-in-zoho-crm)
- [Email Parser](https://help.zoho.com/portal/en/kb/crm/articles/email-parser)
- [FAQs: Case Escalation Rules](https://help.zoho.com/portal/en/kb/crm/articles/faqs-case-escalation-rules)
- [Troubleshooting Blueprint](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-blueprint)
- [Working with Zoho Forms Integration](https://help.zoho.com/portal/en/kb/crm/articles/zoho-forms-crm-integration)
- [Zia's Smart Prompt - Frequently Asked Questions](https://help.zoho.com/portal/en/kb/crm/articles/zia-s-smart-prompt-frequently-asked-questions-26-4-2026)
- [Sales Force Automation (SFA) in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/sales-force-automation-sfa-in-zoho-crm)
- [Setting Case Escalation Rules](https://help.zoho.com/portal/en/kb/crm/articles/set-case-escalation-rules)
- [FAQs: CPQ](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-cpq)
- [Managing services with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/managing-services-with-zoho-crm)
- [Slack](https://help.zoho.com/portal/en/kb/crm/articles/slack-crm-integration)
- [Manage Hierarchy Preference](https://help.zoho.com/portal/en/kb/crm/articles/crm-setup-hierarchy-preference)
- [Deleting and Transferring Users](https://help.zoho.com/portal/en/kb/crm/articles/crm-delete-transfer-users)
- [Best Mode to Contact Customers](https://help.zoho.com/portal/en/kb/crm/articles/best-mode-to-contact-customers)
- [Zia Competitor Alert](https://help.zoho.com/portal/en/kb/crm/articles/zia-competitor-alert)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
