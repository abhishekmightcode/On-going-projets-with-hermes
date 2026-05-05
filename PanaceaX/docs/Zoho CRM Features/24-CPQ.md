# CPQ - Configure Price Quote

> **Feature ID:** `24-CPQ`  
> **Knowledge Base Articles:** 80  
> **Last Updated:** 2026-05-05

## Overview

Configure-Price-Quote, guided selling, price books, product bundles, quote generation

---

## 1. Core Functionality

### 1. Understanding and building reports

As your organization grows, you notice two things: Your CRM data becomes increasingly complex. This data contains valuable insights about your customers, employees, profits, sales, and opportunities. You need to leverage this data to gain clarity about your business and make confident decisions. Data-driven support is essential to provide evidence and build trust in your choices. Reports in Zoho CRM help you do this by compiling relevant data to achieve specific goals , such as a monthly report that tracks newly acquired leads. Once created, you can share the report in multiple ways to those w
### 2. Setting Field Updates

The Field Update option helps you to automatically update certain field values in the records, when the associated workflow rule is triggered. Availability Permission Required Users with administrative profile can access this feature. To create field updates Go to Setup[ ] > Automation > Actions > Field Updates . In the Workflow Field Updates page, click Configure Field Update . In the New Workflow Field Update page, do the following: Enter a Name for the field update. Select the Module from the drop-down list. You can also update the field values of the related parent records associated to th
### 3. Common COQL Errors

COQL "Minimum Successful Response" script for testing/setup: coqlurl = " https://www.zohoapis.com/crm/v3/coql"; queryMap = Map(); query = "select Last_Name from Contacts where Last_Name is not null" queryMap.put("select_query", query); response = invokeUrl [ url: coqlurl type: POST parameters: queryMap.toString() connection: "zcrm" ]; info response; Generic Error Message (may be sent for a number of issues): {"code":"INVALID_REQUEST","details":{},"message":"unable to process your request. please verify whether you have entered proper method name, parameter and parameter values.","status":"erro
### 4. Setting up Webforms

Creating a webform involves three steps: Building the form - Drag and drop fields to build a form and format it easily with the WYSIWYG editor. Specifying the form details - Add details such as form name, landing page URL (where the visitor needs to be redirected after the form is submitted) record assignment rule, notification details, etc. Generating the code for the form - Embed the form using various code formats. Codes for some third-party sites (WordPress, Google Sites, Facebook, and Joomla) are readily available. You can build webforms to generate records for the Leads , Contacts , Case
### 5. Working with Analytics in Zoho CRM Android app

Dashboards in CRM are an effective way to view summaries of your sales data. The dashboards created in the Zoho CRM web application can be accessed and shared from the mobile app. To view a dashboard Tap the icon in your Zoho CRM app. Tap Analytics . Tap on one of the dashboards in the list to view it. You can also use the search bar to search for a dashboard. T o change between views for a dashboard component Go to the dashboard and tap on one component. Tap Change View. Tap a view option (Pie, Bar, Funnel, etc). To share dashboard charts Go to the dashboard and tap on one component. Tap Shar
### 6. Migrating from Sugar CRM to Zoho CRM

Welcome to Zoho CRM! Migrating your data from Sugar CRM to Zoho CRM can be done seamlessly using our data migration feature. All you need is to have an export file from Sugar, ready to use. Click here to learn to export data from their CRM. Before you start migrating your data, it is important that you convert it to the Zoho supported import format- .CSV. Convert your data to .CSV format To convert your data to .CSV format, you can contact our experts ( migration@zohocrm.com ), who will assess the possibilities and help convert the data from .SQL to .CSV. Alternatively, you can submit a conver
### 7. Creating Quotes

In Zoho CRM, you can store quote details by manually entering the data in the quote details form. Note Some of the standard fields may not be visible or editable depending on your organization business process. In case you want to add or modify fields, please contact your System Administrator for more details on the usage of other fields. Create Quotes Individually To create quotes In the Quotes module, click Create Quote . In the Create Quote page, enter the quotes details. Under the Quoted Items section, enter the Product details. Under Product Name search for the desired product and choose
### 8. MF Cloud Invoice Extension

This integration is supported for users in the US, and JP DCs. Scope: Money Forward Cloud Invoice is an online invoicing application designed to simplify and automate the process of creating, sending, and managing invoices. Integrating MF Cloud with Zoho CRM allows you to utilize the features and functionalities available in the Accounts, Quotes, and Product modules of Zoho CRM. Step 1: Installing the MF Cloud Invoice Extension Navigate to CRM Setup > Marketplace > All . Click All Extensions , then browse for and click MF Cloud Invoice Integration . Click Install Now . Select the following che


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `CPQ`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Understanding and building reports`
- `Setting Field Updates`
- `Common COQL Errors`
- `Setting up Webforms`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/cpq` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // CPQ - Configure Price Quote - Example Implementation
// Triggered on record creation/update

if(input.module == "UNDERSTANDING AND BUILDING REPORTS")
{
    // As your organization grows, you notice two things: Your CRM data becomes increasingly complex. This data contains valuable insights about your custome
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

- [Inventory-Products](../Inventory-Products/README.md)
- [Deals-Pipeline](../Deals-Pipeline/README.md)
- [Approval-Process](../Approval-Process/README.md)

### This Feature Enables

- **Inventory-Products** -- shares data model and workflows
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

### Understanding and building reports
**Purpose:** As your organization grows, you notice two things: Your CRM data becomes increasingly complex. This data contains valuable insights about your customers, employees, profits, sales, and opportunities.

**Key Points:**
As your organization grows, you notice two things: Your CRM data becomes increasingly complex.
This data contains valuable insights about your customers, employees, profits, sales, and opportunities.
You need to leverage this data to gain clarity about your business and make confident decisions.
Data-driven support is essential to provide evidence and build trust in your choices.
Reports in Zoho CRM help you do this by compiling relevant data to achieve specific goals , such as a monthly report that tracks newly acquired leads.
Once created, you can share the report in multiple ways to those who need it


### Setting Field Updates
**Purpose:** The Field Update option helps you to automatically update certain field values in the records, when the associated workflow rule is triggered. Availability Permission Required Users with administrativ

**Key Points:**
The Field Update option helps you to automatically update certain field values in the records, when the associated workflow rule is triggered.
Availability Permission Required Users with administrative profile can access this feature.
To create field updates Go to Setup[ ] > Automation > Actions > Field Updates.
In the Workflow Field Updates page, click Configure Field Update.
In the New Workflow Field Update page, do the following: Enter a Name for the field update.
Select the Module from the drop-down list


### Common COQL Errors
**Purpose:** COQL "Minimum Successful Response" script for testing/setup: coqlurl = " https://www.zohoapis.com/crm/v3/coql"; queryMap = Map(); query = "select Last_Name from Contacts where Last_Name is not null" q

**Key Points:**
COQL "Minimum Successful Response" script for testing/setup: coqlurl = " https://www.
com/crm/v3/coql"; queryMap = Map(); query = "select Last_Name from Contacts where Last_Name is not null" queryMap.
put("select_query", query); response = invokeUrl [ url: coqlurl type: POST parameters: queryMap.
toString() connection: "zcrm" ]; info response; Generic Error Message (may be sent for a number of issues): {"code":"INVALID_REQUEST","details":{},"message":"unable to process your request.
please verify whether you have entered proper method name, parameter and parameter values.
","status":"error"} Things to check: 1


### Setting up Webforms
**Purpose:** Creating a webform involves three steps: Building the form - Drag and drop fields to build a form and format it easily with the WYSIWYG editor. Specifying the form details - Add details such as form n

**Key Points:**
Creating a webform involves three steps: Building the form - Drag and drop fields to build a form and format it easily with the WYSIWYG editor.
Specifying the form details - Add details such as form name, landing page URL (where the visitor needs to be redirected after the form is submitted) record assignment rule, notification details, etc.
Generating the code for the form - Embed the form using various code formats.
Codes for some third-party sites (WordPress, Google Sites, Facebook, and Joomla) are readily available.
You can build webforms to generate records for the Leads , Contacts , Cases and any other Custom modules.
While building a webform, the following elements are available in the form: Option Description Add fields Drag and drop the fields that are required in the form


### Working with Analytics in Zoho CRM Android app
**Purpose:** Dashboards in CRM are an effective way to view summaries of your sales data. The dashboards created in the Zoho CRM web application can be accessed and shared from the mobile app. To view a dashboard

**Key Points:**
Dashboards in CRM are an effective way to view summaries of your sales data.
The dashboards created in the Zoho CRM web application can be accessed and shared from the mobile app.
To view a dashboard Tap the icon in your Zoho CRM app.
Tap on one of the dashboards in the list to view it.
You can also use the search bar to search for a dashboard.
T o change between views for a dashboard component Go to the dashboard and tap on one component


### Migrating from Sugar CRM to Zoho CRM
**Purpose:** Welcome to Zoho CRM! Migrating your data from Sugar CRM to Zoho CRM can be done seamlessly using our data migration feature. All you need is to have an export file from Sugar, ready to use. Click here

**Key Points:**
Migrating your data from Sugar CRM to Zoho CRM can be done seamlessly using our data migration feature.
All you need is to have an export file from Sugar, ready to use.
Click here to learn to export data from their CRM.
Before you start migrating your data, it is important that you convert it to the Zoho supported import format-.
CSV format To convert your data to.
CSV format, you can contact our experts ( migration@zohocrm


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

- [Understanding and building reports](https://help.zoho.com/portal/en/kb/crm/articles/understanding-and-building-reports)
- [Setting Field Updates](https://help.zoho.com/portal/en/kb/crm/articles/field-updates)
- [Common COQL Errors](https://help.zoho.com/portal/en/kb/crm/articles/troubleshoot-coql)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/working-with-analytics-in-zoho-crm-android-app)
- [Migrating from Sugar CRM to Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/migrating-from-sugar-crm-to-zoho-crm)
- [Creating Quotes](https://help.zoho.com/portal/en/kb/crm/articles/create-quotes)
- [MF Cloud Invoice Extension](https://help.zoho.com/portal/en/kb/crm/articles/mf-cloud-integration-for-zoho-crm)
- [Using Native App for Tablets](https://help.zoho.com/portal/en/kb/crm/articles/using-native-app-for-tablets)
- [Kaizen posts 2019: API series](https://help.zoho.com/portal/en/kb/crm/articles/api-2019)
- [Managing Notes and Attachments](https://help.zoho.com/portal/en/kb/crm/articles/manage-notes-and-attachments)
- [Understand your CRM Account](https://help.zoho.com/portal/en/kb/crm/articles/understand-crm-account)
- [CPQ for Zoho CRM — Scope, Purpose and Benefits](https://help.zoho.com/portal/en/kb/crm/articles/what-is-cpq)
- [ Modules supported in the Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/modules-supported-in-ios-app)
- [Functions in Formula Fields](https://help.zoho.com/portal/en/kb/crm/articles/formula-fields-functions)
- [Standard Modules & Fields](https://help.zoho.com/portal/en/kb/crm/articles/standard-modules-fields)
- [Standard Fields in Accounts](https://help.zoho.com/portal/en/kb/crm/articles/standard-fields-accounts)
- [Creating Purchase Orders](https://help.zoho.com/portal/en/kb/crm/articles/create-purchase-orders)
- [Customize Zoho CRM for B2C](https://help.zoho.com/portal/en/kb/crm/articles/customize-crm-b2c-companies)
- [Standard Fields in Price Books](https://help.zoho.com/portal/en/kb/crm/articles/standard-fields-price-books)
- [FAQs: Modules](https://help.zoho.com/portal/en/kb/crm/articles/faqs-modules)
- [FAQ: Reports](https://help.zoho.com/portal/en/kb/crm/articles/faqs-reports)
- [Standard Fields in Sales Orders](https://help.zoho.com/portal/en/kb/crm/articles/standard-fields-sales-orders)
- [Working with Invoices](https://help.zoho.com/portal/en/kb/crm/articles/invoices)
- [FAQs: CommandCenter](https://help.zoho.com/portal/en/kb/crm/articles/faqs-commandcenter)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **4 KB articles** with **59 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [CPQ for Zoho CRM — How it works](https://help.zoho.com/portal/en/kb/crm/how-it-works) | 29 | [View Article](https://help.zoho.com/portal/en/kb/crm/how-it-works) |
| 2 | [Guided selling in CPQ](https://help.zoho.com/portal/en/kb/crm/guided-selling) | 21 | [View Article](https://help.zoho.com/portal/en/kb/crm/guided-selling) |
| 3 | [FAQs: CPQ](https://help.zoho.com/portal/en/kb/crm/faqs-on-cpq) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-on-cpq) |
| 4 | [CPQ for Zoho CRM — Scope, Purpose and Benefits](https://help.zoho.com/portal/en/kb/crm/what-is-cpq) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/what-is-cpq) |

### Sample Image URLs (from top articles)
**[CPQ for Zoho CRM — How it works](https://help.zoho.com/portal/en/kb/crm/how-it-works)** — 29 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575f6d22c62749d216b08bf173e1287c240d6d0a49c636dbb605e2ca6b6388c95e28b0100791f7bc7ede6f9e369743cc87?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b518536d4621321515abaee756069c374a06d421dd980e03da66017f09b9fce0bc0ddd11a4002ba8deaf3c1d1e663783?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b578396261c8d6edf8fafc499ec4e3cd10557bd2ff296ce661d1f5b7770c615a437fdb4594393a2d73c95386f61c6ba9823?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b570c7f8be63042a028d8aa42fae411301599647c636b47d4496b9465433a6d8934f75c6ccea39ce79228f34e7b0ab052da?inline=true`
[View all 29 images in article →](https://help.zoho.com/portal/en/kb/crm/how-it-works)

**[Guided selling in CPQ](https://help.zoho.com/portal/en/kb/crm/guided-selling)** — 21 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579611736fb3443a1adb91c0c4cd22ddb009b2ffff49d006a945c606f86ba26dc2a67e4f01157e24b702d9058c12ee6b9c?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5786e35da2db6a3717b79c43abec07a8e4d3acd110322b706624ff2f84d708255a8398b55615870bd720b808657f4758df?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5747f51526cdebab4e4513ca8c24806a30db10c7756457ec37efafb74aa1fc264d3f6c13061b6bf4141a8c738b0a8f2521?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ee062363aa08c5a1ebbe462f2831433c0ab228e4563407581069c230d51f8a773e294093a3a9a30d09a3bedc64749c8a?inline=true`
[View all 21 images in article →](https://help.zoho.com/portal/en/kb/crm/guided-selling)

**[FAQs: CPQ](https://help.zoho.com/portal/en/kb/crm/faqs-on-cpq)** — 7 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b578d5e8ef11889404e9dc28a1f5aec7c62f6de7bbc04e0054d1462c2b95181a7d2d03beb07a4800f9822a0ff6329748282?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5790cebf2880ac5d862120511207ca7f93bf26aa8a8f97b626fd05243239f8842dded65c0670236446b038defc6d3bead4?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b71d9ff0d53e82e9ada70d6a7a3d144c9a5ee91193d3aebe63333dc1221199e0153b637da1b30ceb21685e5272a4d3a2?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57451588c2c49ec11d9c9fe7f3eac1ae4a53c9a69488c79e73839a81469abb05d33ecab26b65ebfff218414525fbeb22eb?inline=true`
[View all 7 images in article →](https://help.zoho.com/portal/en/kb/crm/faqs-on-cpq)

**[CPQ for Zoho CRM — Scope, Purpose and Benefits](https://help.zoho.com/portal/en/kb/crm/what-is-cpq)** — 2 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57eb6a2a797d084258e75339e7f8f3b56aaecfbe2e41c833bc18cfebece17f10870ca158b6f97d2bc23546d85afb6517d3?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d5b2044171ea22cb108b9b81068cbeb2df7ce0c47c59eb133d6236130521baf2fb1f5df9eb17959b9b609bb3ba96456f?inline=true`
[View all 2 images in article →](https://help.zoho.com/portal/en/kb/crm/what-is-cpq)

