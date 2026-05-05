# Deals & Pipeline Management

> **Feature ID:** `03-Deals-Pipeline`  
> **Knowledge Base Articles:** 320  
> **Last Updated:** 2026-05-05

## Overview

Deal tracking, multi-stage pipelines, deal workflows, and sales process management

---

## 1. Core Functionality

### 1. Voice based forecast analysis

As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams. The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exactly know why your deals are falling out of the pipeline. Or you may not know what is it that you are
### 2. Field of Lookup

Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list. While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duratio
### 3. RingCentral Video

Every business, no matter what size, deals with setting up professional meetings almost everyday. It can be a meeting with customers on a product demo or a discussion with the team members on a project, setting up a meeting is almost inevitable. Among other requirements, the most essential are identifying availability of the attendees, host and, the venue. Also, at times, conducting physical meetings take up a lot of time and money which is not feasible in every situation. As an alternative, online meetings doesn't involve these external factors. All you need to do is to decide a suitable time
### 4. FAQs: Zoho CRM Integration with Zoho Desk

Why should I integrate Zoho CRM with Zoho Desk? Zoho Desk is a cloud-based help desk application that lets you manage and resolve your customer inquiries, complaints, and doubts along with offering self-help articles to help your customers resolve issues themselves. CRM lets your business acquire customers and make deals with them, but what about after-sales services? If your company is poor at providing after-sales services to your customers, it will directly impact your customer retention. Businesses need to be customer-centric and customers shall be the king, but this can only be achieved i
### 5. SharePoint for Zoho CRM

Microsoft SharePoint is a document management tool that enables you to share and manage content, and thereby collaborate easily and securely with members both inside and outside your organization. With the SharePoint extension for Zoho CRM, you can access, manage, and organize your SharePoint libraries from within Zoho CRM. You can also create customized folders for your Zoho CRM records in SharePoint libraries, where you can store files related to your deals and accounts and share those files and folders securely with your contacts, leads, and vendors. Note: Please note that the SharePoint ex
### 6. Setting up Agents

Before you begin: How agents work inside CRM Before jumping into the setup steps, it helps to understand the three key decisions that shape how an agent operates inside CRM. Every agent configuration comes down to these three things. Deciding what triggers the agent Choosing the activation condition decides the entry point for your agent's actions. You start by selecting the module where the agent should be activated. For example, if the agent should assist with sales deals, you pick the Deals module. This determines the data scope the agent can access during execution. Then you select the eve
### 7. Zoho Survey Integration - Overview

Surveys are useful marketing tools that help you enhance your business. It's a method by which you put specific questions to a group of people whose answers will help you improve your products or services. There are many applications to create surveys. Zoho Survey is one such simple tool that helps you create and send surveys to your contacts easily. Why Integrate Zoho Survey with Zoho CRM Once you collect survey responses, the next step is usually to follow up with the respondents. For example, let's say you have mailed a bunch of survey questions to your leads in Zoho CRM. After you receive
### 8. Working with notes in Zoho CRM iOS app 

Notes make it easy to capture your interactions with customers and prospects in CRM. You can add notes to leads, contacts, accounts, deals, activities, and more. These notes are stored as related items under each entry, so all your interaction details stay connected and organized. You can add notes in the following ways: Text notes Voice notes Voice-to-text notes ${accordionSetId_2026_0_20_17_6_53} To add text notes Open the record. Go to Notes under the related list. Tap on the icon Type out the note and apply rich text formatting if needed ( bold, italics, text color, etc.). Tap on the icon


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `DEALS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Voice based forecast analysis`
- `Field of Lookup`
- `RingCentral Video`
- `FAQs: Zoho CRM Integration with Zoho Desk`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/deals` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Deals & Pipeline Management - Example Implementation
// Triggered on record creation/update

if(input.module == "VOICE BASED FORECAST ANALYSIS")
{
    // As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter et
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
- [Activities](../Activities/README.md)
- [Forecasts](../Forecasts/README.md)
- [Blueprint-Process-Management](../Blueprint-Process-Management/README.md)

### This Feature Enables

- **Leads-Management** -- shares data model and workflows
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

### Voice based forecast analysis
**Purpose:** As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you ar

**Key Points:**
As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc).
By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams.
The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exactly know why your deals are falling out of the pipeline.
Or you may not know what is it that you are doing well, that is giving you winning deals, for that matter.
Knowledge of this winning/losing pattern will help you set better goals and also meet them better.
This is where VoC enters the picture


### Field of Lookup
**Purpose:** Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Stu

**Key Points:**
Overview Lookup fields enable users to associate records between two modules.
Let's say, for example, you have two modules: Students and Courses.
By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list.
While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duration, subjects, course instructor, and so on—you can use the field of lookup module option.
Business scenarios View additional details of a contact in the Deals module Sales associates can view a contact's email address, phone number, referrer, and—alongside the primary lookup field—the contact's name.
They can also view the values in these fields in a report created for the Deals module


### RingCentral Video
**Purpose:** Every business, no matter what size, deals with setting up professional meetings almost everyday. It can be a meeting with customers on a product demo or a discussion with the team members on a projec

**Key Points:**
Every business, no matter what size, deals with setting up professional meetings almost everyday.
It can be a meeting with customers on a product demo or a discussion with the team members on a project, setting up a meeting is almost inevitable.
Among other requirements, the most essential are identifying availability of the attendees, host and, the venue.
Also, at times, conducting physical meetings take up a lot of time and money which is not feasible in every situation.
As an alternative, online meetings doesn't involve these external factors.
All you need to do is to decide a suitable time, and invite your attendees


### FAQs: Zoho CRM Integration with Zoho Desk
**Purpose:** Why should I integrate Zoho CRM with Zoho Desk? Zoho Desk is a cloud-based help desk application that lets you manage and resolve your customer inquiries, complaints, and doubts along with offering se

**Key Points:**
Why should I integrate Zoho CRM with Zoho Desk.
Zoho Desk is a cloud-based help desk application that lets you manage and resolve your customer inquiries, complaints, and doubts along with offering self-help articles to help your customers resolve issues themselves.
CRM lets your business acquire customers and make deals with them, but what about after-sales services.
If your company is poor at providing after-sales services to your customers, it will directly impact your customer retention.
Businesses need to be customer-centric and customers shall be the king, but this can only be achieved if you’re able to provide real-time support to your customers when they need you.
Zoho Desk has been created keeping these factors in mind to empower your support team to assist your customers and improve the overall customer experience


### SharePoint for Zoho CRM
**Purpose:** Microsoft SharePoint is a document management tool that enables you to share and manage content, and thereby collaborate easily and securely with members both inside and outside your organization. Wit

**Key Points:**
Microsoft SharePoint is a document management tool that enables you to share and manage content, and thereby collaborate easily and securely with members both inside and outside your organization.
With the SharePoint extension for Zoho CRM, you can access, manage, and organize your SharePoint libraries from within Zoho CRM.
You can also create customized folders for your Zoho CRM records in SharePoint libraries, where you can store files related to your deals and accounts and share those files and folders securely with your contacts, leads, and vendors.
Note: Please note that the SharePoint extension for Zoho CRM is available in US, EU, CN, IN, AU , CA, and JP datacenters.
Installing the extension You can install the SharePoint extension either from the Zoho Marketplace or from within your Zoho CRM account.
To install the extension from Zoho CRM: Go to Setup > Marketplace > All


### Setting up Agents
**Purpose:** Before you begin: How agents work inside CRM Before jumping into the setup steps, it helps to understand the three key decisions that shape how an agent operates inside CRM. Every agent configuration

**Key Points:**
Before you begin: How agents work inside CRM Before jumping into the setup steps, it helps to understand the three key decisions that shape how an agent operates inside CRM.
Every agent configuration comes down to these three things.
Deciding what triggers the agent Choosing the activation condition decides the entry point for your agent's actions.
You start by selecting the module where the agent should be activated.
For example, if the agent should assist with sales deals, you pick the Deals module.
This determines the data scope the agent can access during execution


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

- [Voice based forecast analysis](https://help.zoho.com/portal/en/kb/crm/articles/voice-based-forecast-analysis)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [RingCentral Video](https://help.zoho.com/portal/en/kb/crm/articles/ringcentral-video)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [SharePoint for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/sharepoint-for-zoho-crm)
- [Setting up Agents](https://help.zoho.com/portal/en/kb/crm/articles/setting-up-agents-26-4-2026)
- [Zoho Survey Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-survey-crm-integration)
- [Working with notes in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/working-with-notes-in-zoho-crm-ios-app)
- [Understanding and building reports](https://help.zoho.com/portal/en/kb/crm/articles/understanding-and-building-reports)
- [Call analytics](https://help.zoho.com/portal/en/kb/crm/articles/call-analytics)
- [Team modules in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/articles/team-modules-in-zoho-crm-ios-app)
- [Installing the CRM Mobile App](https://help.zoho.com/portal/en/kb/crm/articles/installing-crm-mobile-app)
- [Zoho Projects Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/overview-zoho-projects-crm-integration)
- [Acting on VoC insights](https://help.zoho.com/portal/en/kb/crm/articles/acting-on-voc-insights)
- [FUJIFILM IWpro Document for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/fujifilm-iwpro-document-for-zoho-crm)
- [OneNote](https://help.zoho.com/portal/en/kb/crm/articles/onenote-integration)
- [Setting Field Updates](https://help.zoho.com/portal/en/kb/crm/articles/field-updates)
- [Converting Leads](https://help.zoho.com/portal/en/kb/crm/articles/convert-leads)
- [FAQs: Zoho CRM for Google Apps](https://help.zoho.com/portal/en/kb/crm/articles/faqs-zoho-crm-for-google-apps)
- [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/articles/webform-analytics)
- [Trello](https://help.zoho.com/portal/en/kb/crm/articles/trello)
- [Common COQL Errors](https://help.zoho.com/portal/en/kb/crm/articles/troubleshoot-coql)
- [Integrating Zoho Campaigns with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/zoho-campaigns-crm-integration)
- [Telephony - An Introduction](https://help.zoho.com/portal/en/kb/crm/articles/telephony-introduction)
- [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/working-with-analytics-in-zoho-crm-android-app)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
