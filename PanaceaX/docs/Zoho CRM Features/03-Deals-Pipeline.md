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

---
## UI Screenshots & Image Reference
This feature has **11 KB articles** with **62 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Stage component](https://help.zoho.com/portal/en/kb/crm/stage-component) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/stage-component) |
| 2 | [Creating Deals](https://help.zoho.com/portal/en/kb/crm/create-deals) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-deals) |
| 3 | [Email Association With Deals](https://help.zoho.com/portal/en/kb/crm/email-association-with-deal) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-association-with-deal) |
| 4 | [Enhance Sales Collaboration with Team Selling and Deal Split](https://help.zoho.com/portal/en/kb/crm/team-selling-and-deal-split) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/team-selling-and-deal-split) |
| 5 | [Troubleshooting Zoho Backstage integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/troubleshooting-zoho-backstage-integration-with-zoho-crm) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-zoho-backstage-integration-with-zoho-crm) |
| 6 | [Troubleshooting Sales Pipelines](https://help.zoho.com/portal/en/kb/crm/troubleshooting-pipelines) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-pipelines) |
| 7 | [Standardize naming convention for deals with auto-creation of deal names](https://help.zoho.com/portal/en/kb/crm/automatically-create-a-deal-name) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/automatically-create-a-deal-name) |
| 8 | [Idle Deal Alert](https://help.zoho.com/portal/en/kb/crm/idle-deal-alert-crm-integration) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/idle-deal-alert-crm-integration) |
| 9 | [FAQs: Deals](https://help.zoho.com/portal/en/kb/crm/faqs-deals) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-deals) |
| 10 | [Multiple Sales Pipeline](https://help.zoho.com/portal/en/kb/crm/multiple-sales-pipeline) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/multiple-sales-pipeline) |
| 11 | [Zoho Backstage Integration](https://help.zoho.com/portal/en/kb/crm/zoho-backstage) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-backstage) |

### Sample Image URLs (from top articles)
**[Stage component](https://help.zoho.com/portal/en/kb/crm/stage-component)** — 12 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571f0a33e460c0bfe03ec0abd11d6f6e0392a8ca47469834c2295558d83f28c035b07605c5a3d4990adc0a95dcfc7ce299?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b578fcf42a6240ea008c8726af8b01227302e517acbba24fb90224cbec1c3e201c63b59988690aeac685031576f2d175dd7?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f16148951ff2ab8c0af6be98ff9cdac89b0fa2466bbc767ac2e2cb4f21c311e1fe46702aa378089b4dedfa0a53333cb6?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5765547ab32a8b02b8e132be356b4690ee2500721eeeed197935ad9813342feaf6404be1e234fb05e3faacdde10a4dd768?inline=true`
[View all 12 images in article →](https://help.zoho.com/portal/en/kb/crm/stage-component)

**[Creating Deals](https://help.zoho.com/portal/en/kb/crm/create-deals)** — 10 images
- `https://www.zoho.com/crm/help/img/deals-list-view.png`
- `https://www.zoho.com/crm/help/img/deals-stage-view.png`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57dc2eaa8344016f614a77cda0653d18352de7fc2c96ed329f47a42b1f18b06ff44aa67e6f165d461c1829ebd52f22afce?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b570e0c19b0e91b70d26a08f65fdd63d6f9e26380c5621ef16d7342a05bdb010db63e4e6a7377d37f99b70625182fcc589b?inline=true`
[View all 10 images in article →](https://help.zoho.com/portal/en/kb/crm/create-deals)

**[Email Association With Deals](https://help.zoho.com/portal/en/kb/crm/email-association-with-deal)** — 8 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574cfca4f99b6cd1708ba2704f5b2591baac07cf8a97f09623db35e7e2f27aa3ec88cef8d7a8dee36e36991555752aa507?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57a6f6ef9ea58b9aa2d6686636cce0645172adb7a116093cb9efde7d3f709e343eda922204f751884c6d07396548a1dfc3?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ee38ae09871db29a0ba53f68ccefccdffd9f0e1a49ea9f56c57e76ccd1286b219f60a8ceb29b141d4da62711b1721f09?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57bd5ab58ca2d4326fdfb2af00c615f16ddf2e78d667b719d23500792936055c3c20139a80787347a5826ca682997bd038?inline=true`
[View all 8 images in article →](https://help.zoho.com/portal/en/kb/crm/email-association-with-deal)

**[Enhance Sales Collaboration with Team Selling and Deal Split](https://help.zoho.com/portal/en/kb/crm/team-selling-and-deal-split)** — 7 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57db738ef60236bf4e993e58a2fc1e54809603fc736007cffb7d134eaa4e9631a14d4cfdf83f8e74d344fb7519616f6ce5?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ef22f75995da1912cd8ec9bf9774ce6d94929f7ed207580cbccb2dbfc7ce0896303adbb1085fd2ecde1c087ce1ba1806?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f9d56d68e9a813519a088901743ac3364e398eb36da35fe26e8d42c375ed3b1ae46efe0c47ca5cc6c2ab92fe36b8f086?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b570ad778622c09214f9628c286b3f5c7b4a16d47201490e2464d2b5003a6ada24a22a6f610f6613c6ab2def0676ba8620d?inline=true`
[View all 7 images in article →](https://help.zoho.com/portal/en/kb/crm/team-selling-and-deal-split)

**[Troubleshooting Zoho Backstage integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/troubleshooting-zoho-backstage-integration-with-zoho-crm)** — 6 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ae24bff6736e2f98d1f5130751154b99f4f6e4c2498f45b58b69e0dced92574b37a4fcdd1ca5333eabc98eab3d7132ec?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579b0b6a424bbf38afeb643c2fa5ebb67c1308f597645badc0ce932bf27bbfef4cc64d37e461f490b7542b5b3d21a80a07?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b570759c5baff126740c49a8dfd0352cc31f6f1bacbfd4ac8407451b6f981cd103180a3d685a3e8388af0ee0c5f3ac8231c?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b578a63867ce6efe6157ccb22388abcc62a774a9c6b66cc766e5901097a2975400e9016c1ad8c64a5a8fcdb360b07fb5397?inline=true`
[View all 6 images in article →](https://help.zoho.com/portal/en/kb/crm/troubleshooting-zoho-backstage-integration-with-zoho-crm)

