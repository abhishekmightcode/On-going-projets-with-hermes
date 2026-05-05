# Customization & Canvas

> **Feature ID:** `14-Customization-Builder`  
> **Knowledge Base Articles:** 218  
> **Last Updated:** 2026-05-05

## Overview

Custom fields, layouts, Canvas design studio, wizards, conditional layouts

---

## 1. Core Functionality

### 1. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 2. Setting up an Unsubscribe Link

Allow the customers to unsubscribe from your email communications by creating an unsubscribe link and embedding it in the emails or hosting on the webpages. You can use the system defined default link or create a custom link. The default unsubscribe link will be available for all users and that cannot be customized. Availability Permission Required Users with the Unsubscribe Form permission in profile can access this feature. Creating an Unsubscribe Link Two essential things you need to set this up are: Location URL It is the web page where the unsubscribe link will be hosted. You can choose a
### 3. FAQs: Data Administration

How can I delete the existing data in my Zoho CRM account and start with a fresh account? You need to manually delete all the data in your account to start a fresh account. You can also close the existing account and sign up for a new Zoho CRM account with the same email address (Not Recommended). Related Link Deleting the Zoho CRM Account How do I delete attachments to free up storage space? When mails (with attachments) are sent using the email template, the attachment is counted only once for your storage, For example, if you send emails to 100 users, the document attached is not counted on
### 4. Charts

Some of the options mentioned in this document are being released in a phased manner and may only be available to specific users. The Dashboards tab is renamed as Analytics for selected accounts. A chart presents data from various records of a module(s) in a visual or graphical representation for an easy analysis. The data is seemingly comprehensible as users can easily pick out the patterns, trends, etc., which may otherwise be difficult to interpret. For example, you are the Sales Manager for Asia Pacific region and want to compare the number of leads created by the sales representatives in
### 5. Field of Lookup

Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list. While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duratio
### 6. Installing the MS Word Plug-in

System Requirements The basic system requirements to install the Zoho CRM Plug-in for Microsoft Word are below: Hardware x486 with minimum of 256 Mb RAM; minimum 10 Mb disk space Operating System Windows 7, 8, and 10 Software Microsoft Word 2010 / 2013 / 2016 Browser Only Internet Explorer (Version 6 and above) Installation Prerequisites You must have sufficient system privileges to install the Zoho CRM Plug-in for Microsoft Word You must have valid login details to connect to the Zoho CRM server You must close all Microsoft Word documents before installing the Plug-in Install Zoho CRM Plug-in
### 7. Zoho CRM for iPhone - An Overview

Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above. From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc. Availability Permission Required Administrators need to activate it for users in other profiles. Features Zia Voice - Call or Chat with Zia to get answers for all your questions in Zoho CRM. Spotlight - Spotlight Search lets you see the contact informat
### 8. FAQs: Zoho CRM Integration with Zoho Desk

Why should I integrate Zoho CRM with Zoho Desk? Zoho Desk is a cloud-based help desk application that lets you manage and resolve your customer inquiries, complaints, and doubts along with offering self-help articles to help your customers resolve issues themselves. CRM lets your business acquire customers and make deals with them, but what about after-sales services? If your company is poor at providing after-sales services to your customers, it will directly impact your customer retention. Businesses need to be customer-centric and customers shall be the king, but this can only be achieved i


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `CUSTOMIZATION`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Consent Management`
- `Setting up an Unsubscribe Link`
- `FAQs: Data Administration`
- `Charts`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/customization` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Customization & Canvas - Example Implementation
// Triggered on record creation/update

if(input.module == "CONSENT MANAGEMENT")
{
    // Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent
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

- [Modules-Data-Model](../Modules-Data-Model/README.md)
- [CRM-Canvas-UI](../CRM-Canvas-UI/README.md)
- [Validation-Rules](../Validation-Rules/README.md)

### This Feature Enables

- **Modules-Data-Model** -- shares data model and workflows
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

### Consent Management
**Purpose:** Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set con

**Key Points:**
Zoho CRM's consent management settings help you get consent from your prospects and customers.
We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details.
Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules.
It cannot be applied for team modules.
Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be.
You will begin by marking the records whose data needs to be processed after obtaining consent


### Setting up an Unsubscribe Link
**Purpose:** Allow the customers to unsubscribe from your email communications by creating an unsubscribe link and embedding it in the emails or hosting on the webpages. You can use the system defined default link

**Key Points:**
Allow the customers to unsubscribe from your email communications by creating an unsubscribe link and embedding it in the emails or hosting on the webpages.
You can use the system defined default link or create a custom link.
The default unsubscribe link will be available for all users and that cannot be customized.
Availability Permission Required Users with the Unsubscribe Form permission in profile can access this feature.
Creating an Unsubscribe Link Two essential things you need to set this up are: Location URL It is the web page where the unsubscribe link will be hosted.
You can choose a standard page designed by Zoho CRM, that will display the information and the link to unsubscribe as a location URL


### FAQs: Data Administration
**Purpose:** How can I delete the existing data in my Zoho CRM account and start with a fresh account? You need to manually delete all the data in your account to start a fresh account. You can also close the exis

**Key Points:**
How can I delete the existing data in my Zoho CRM account and start with a fresh account.
You need to manually delete all the data in your account to start a fresh account.
You can also close the existing account and sign up for a new Zoho CRM account with the same email address (Not Recommended).
Related Link Deleting the Zoho CRM Account How do I delete attachments to free up storage space.
When mails (with attachments) are sent using the email template, the attachment is counted only once for your storage, For example, if you send emails to 100 users, the document attached is not counted on your storage 100 times.
Only the document(s) attached to the template are considered for storage


### Charts
**Purpose:** Some of the options mentioned in this document are being released in a phased manner and may only be available to specific users. The Dashboards tab is renamed as Analytics for selected accounts. A ch

**Key Points:**
Some of the options mentioned in this document are being released in a phased manner and may only be available to specific users.
The Dashboards tab is renamed as Analytics for selected accounts.
A chart presents data from various records of a module(s) in a visual or graphical representation for an easy analysis.
The data is seemingly comprehensible as users can easily pick out the patterns, trends, etc.
, which may otherwise be difficult to interpret.
For example, you are the Sales Manager for Asia Pacific region and want to compare the number of leads created by the sales representatives in the previous year


### Field of Lookup
**Purpose:** Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Stu

**Key Points:**
Overview Lookup fields enable users to associate records between two modules.
Let's say, for example, you have two modules: Students and Courses.
By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list.
While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duration, subjects, course instructor, and so on—you can use the field of lookup module option.
Business scenarios View additional details of a contact in the Deals module Sales associates can view a contact's email address, phone number, referrer, and—alongside the primary lookup field—the contact's name.
They can also view the values in these fields in a report created for the Deals module


### Installing the MS Word Plug-in
**Purpose:** System Requirements The basic system requirements to install the Zoho CRM Plug-in for Microsoft Word are below: Hardware x486 with minimum of 256 Mb RAM; minimum 10 Mb disk space Operating System Wind

**Key Points:**
System Requirements The basic system requirements to install the Zoho CRM Plug-in for Microsoft Word are below: Hardware x486 with minimum of 256 Mb RAM; minimum 10 Mb disk space Operating System Windows 7, 8, and 10 Software Microsoft Word 2010 / 2013 / 2016 Browser Only Internet Explorer (Version 6 and above) Installation Prerequisites You must have sufficient system privileges to install the Zoho CRM Plug-in for Microsoft Word You must have valid login details to connect to the Zoho CRM server You must close all Microsoft Word documents before installing the Plug-in Install Zoho CRM Plug-in for Microsoft Word Installing Zoho CRM Plug-in for Microsoft Word allows you to create mail merge templates based on the CRM data source.
To install the Zoho CRM Plug-in Log in to Zoho CRM with your Username and Password.
Go to Setup > Marketplace > All > Plug-in for Microsoft Word.
In the Zoho CRM Plug-in for Microsoft Word page, click Download Now.
Save/Run the Adventnet_ZohoCRM_Word_Plugin.
exe In the Install Shield Wizard, click Next to start the installation process


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

- [Consent Management](https://help.zoho.com/portal/en/kb/crm/articles/consent-management)
- [Setting up an Unsubscribe Link](https://help.zoho.com/portal/en/kb/crm/articles/set-unsubscribe-link)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Charts](https://help.zoho.com/portal/en/kb/crm/articles/create-charts)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [Installing the MS Word Plug-in](https://help.zoho.com/portal/en/kb/crm/articles/install-ms-word-plug-in-crm-integration)
- [Zoho CRM for iPhone - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-iphone-an-overview)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [Including Opt-in Checkbox in Web Forms for Consent](https://help.zoho.com/portal/en/kb/crm/articles/opt-in-checkbox)
- [Lead Queue for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/lead-queue-for-zoho-crm)
- [SharePoint for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/sharepoint-for-zoho-crm)
- [HubSpot for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/hubspot-for-zoho-crm)
- [FAQs: Working with Emails](https://help.zoho.com/portal/en/kb/crm/articles/faq-working-with-emails)
- [Converting Leads](https://help.zoho.com/portal/en/kb/crm/articles/convert-leads)
- [Requesting Data Backup](https://help.zoho.com/portal/en/kb/crm/articles/requesting-data-backup)
- [Integrating Zoho Campaigns with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/zoho-campaigns-crm-integration)
- [Booking appointments for services](https://help.zoho.com/portal/en/kb/crm/articles/booking-appointments-for-services)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [FAQs: Data Enrichment](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-enrichment)
- [Troubleshooting Sales Pipelines](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-pipelines)
- [Associate a contact with multiple companies or accounts](https://help.zoho.com/portal/en/kb/crm/articles/associate-a-contact-with-multiple-companies-or-accounts)
- [Customizing the navigation bar in the Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/customizing-the-navigation-bar-in-the-zoho-crm-ios-app)
- [Building Formula Fields](https://help.zoho.com/portal/en/kb/crm/articles/build-formula-fields)
- [Frequently Asked Questions on CRM for Everyone](https://help.zoho.com/portal/en/kb/crm/articles/frequently-asked-questions-on-crm-for-everyone)
- [FAQs: Page layouts](https://help.zoho.com/portal/en/kb/crm/articles/faqs-page-layouts)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **51 KB articles** with **523 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Types of Custom Fields](https://help.zoho.com/portal/en/kb/crm/types-of-fields) | 46 | [View Article](https://help.zoho.com/portal/en/kb/crm/types-of-fields) |
| 2 | [Working with Page Layouts](https://help.zoho.com/portal/en/kb/crm/create-page-layouts) | 38 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-page-layouts) |
| 3 | [Voice of the Customer Settings — Enabling, disabling and more.](https://help.zoho.com/portal/en/kb/crm/voice-of-the-customer-settings) | 28 | [View Article](https://help.zoho.com/portal/en/kb/crm/voice-of-the-customer-settings) |
| 4 | [Customizing Module View Using the all-new Canvas design suite](https://help.zoho.com/portal/en/kb/crm/customizing-module-view-using-the-all-new-canvas-design-suite) | 27 | [View Article](https://help.zoho.com/portal/en/kb/crm/customizing-module-view-using-the-all-new-canvas-design-suite) |
| 5 | [Troubleshooting Settings and Customizations](https://help.zoho.com/portal/en/kb/crm/troubleshooting-settings-and-customization) | 25 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-settings-and-customization) |
| 6 | [Using Custom Buttons](https://help.zoho.com/portal/en/kb/crm/custom-buttons) | 21 | [View Article](https://help.zoho.com/portal/en/kb/crm/custom-buttons) |
| 7 | [Troubleshooting Module Customization](https://help.zoho.com/portal/en/kb/crm/troubleshooting-module-customization) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-module-customization) |
| 8 | [Working with Custom Fields](https://help.zoho.com/portal/en/kb/crm/use-custom-fields) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/use-custom-fields) |
| 9 | [Multi-select lookup fields in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/multi-select-lookup-fields-in-zoho-crm-android-app) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/multi-select-lookup-fields-in-zoho-crm-android-app) |
| 10 | [Auto-update multiple fields with same values.](https://help.zoho.com/portal/en/kb/crm/auto-upload-fields-that-have-similar-data) | 17 | [View Article](https://help.zoho.com/portal/en/kb/crm/auto-upload-fields-that-have-similar-data) |
| 11 | [Creating Custom Tabs](https://help.zoho.com/portal/en/kb/crm/custom-tabs-creator-crm-integration) | 17 | [View Article](https://help.zoho.com/portal/en/kb/crm/custom-tabs-creator-crm-integration) |
| 12 | [Multi-select lookup fields  in iOS app](https://help.zoho.com/portal/en/kb/crm/multi-select-lookup-fields-in-ios-app) | 16 | [View Article](https://help.zoho.com/portal/en/kb/crm/multi-select-lookup-fields-in-ios-app) |
| 13 | [Creating Formula Fields](https://help.zoho.com/portal/en/kb/crm/create-formula-fields) | 15 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-formula-fields) |
| 14 | [Address Field](https://help.zoho.com/portal/en/kb/crm/address-field-in-zoho-crm) | 13 | [View Article](https://help.zoho.com/portal/en/kb/crm/address-field-in-zoho-crm) |
| 15 | [Customizing Organization Modules](https://help.zoho.com/portal/en/kb/crm/customize-modules) | 13 | [View Article](https://help.zoho.com/portal/en/kb/crm/customize-modules) |
| 16 | [Create a Homepage using Home View in Canvas](https://help.zoho.com/portal/en/kb/crm/create-a-homepage-using-home-view-in-canvas) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-a-homepage-using-home-view-in-canvas) |
| 17 | [Personal customer insights by VoC](https://help.zoho.com/portal/en/kb/crm/personal-customer-insights-by-voc) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/personal-customer-insights-by-voc) |
| 18 | [Concatenate two fields — (Combining two field values onto a third field)](https://help.zoho.com/portal/en/kb/crm/concatenate-two-fields) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/concatenate-two-fields) |
| 19 | [Marking Personal Fields](https://help.zoho.com/portal/en/kb/crm/marking-personal-fields) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/marking-personal-fields) |
| 20 | [Communicating with customers through iPhone](https://help.zoho.com/portal/en/kb/crm/communicating-with-customers-through-iphone) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/communicating-with-customers-through-iphone) |
| 21 | [Using Copy Customization](https://help.zoho.com/portal/en/kb/crm/using-copy-customization) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/using-copy-customization) |
| 22 | [Customizing Home Tab](https://help.zoho.com/portal/en/kb/crm/customize-home-tab) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/customize-home-tab) |
| 23 | [Drill down into your customers' voices](https://help.zoho.com/portal/en/kb/crm/drill-down-into-your-customers-voices-7-1-2025) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/drill-down-into-your-customers-voices-7-1-2025) |
| 24 | [Communicating with Customers](https://help.zoho.com/portal/en/kb/crm/communicating-with-customers-using-zoho-crm-android-app) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/communicating-with-customers-using-zoho-crm-android-app) |
| 25 | [Voice of the Customer — Scope](https://help.zoho.com/portal/en/kb/crm/voice-of-the-customer-scope) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/voice-of-the-customer-scope) |
| 26 | [Customizations in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/customizations-in-zoho-crm) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/customizations-in-zoho-crm) |
| 27 | [Orchestrate customer journey using CommandCenter from Zoho CRM](https://help.zoho.com/portal/en/kb/crm/orchestrate-customer-journey-using-commandcenter-from-zoho-crm) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/orchestrate-customer-journey-using-commandcenter-from-zoho-crm) |
| 28 | [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/field-of-lookup) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/field-of-lookup) |
| 29 | [Conditional Layouts - Concept and Benefits](https://help.zoho.com/portal/en/kb/crm/conditional-layouts-concept-and-benefits) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/conditional-layouts-concept-and-benefits) |
| 30 | [FAQs: General questions on customization](https://help.zoho.com/portal/en/kb/crm/general-questions-on-customization) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/general-questions-on-customization) |
| 31 | [Customizing Setup Page](https://help.zoho.com/portal/en/kb/crm/customizing-setup-page) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/customizing-setup-page) |
| 32 | [Fields List Page](https://help.zoho.com/portal/en/kb/crm/fields-list-page) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/fields-list-page) |
| 33 | [Setting Field Updates](https://help.zoho.com/portal/en/kb/crm/field-updates) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/field-updates) |
| 34 | [Customizing the User Layout](https://help.zoho.com/portal/en/kb/crm/user-layout-customization) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/user-layout-customization) |
| 35 | [Connect with customers using LINE: Integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/connect-with-customers-using-line-integration-with-zoho-crm) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/connect-with-customers-using-line-integration-with-zoho-crm) |
| 36 | [Modifying Special Fields](https://help.zoho.com/portal/en/kb/crm/modify-special-fields) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/modify-special-fields) |
| 37 | [Customization](https://help.zoho.com/portal/en/kb/crm/customizing-in-zoho-crm-android-app) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/customizing-in-zoho-crm-android-app) |
| 38 | [Customize Zoho CRM for B2C](https://help.zoho.com/portal/en/kb/crm/customize-crm-b2c-companies) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/customize-crm-b2c-companies) |
| 39 | [FAQ: Canvas in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/faq-canvas-in-zoho-crm) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/faq-canvas-in-zoho-crm) |
| 40 | [Customizing the navigation bar in the Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/customizing-the-navigation-bar-in-the-zoho-crm-ios-app) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/customizing-the-navigation-bar-in-the-zoho-crm-ios-app) |
| 41 | [Canvas in sandbox](https://help.zoho.com/portal/en/kb/crm/canvas-in-sandbox) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/canvas-in-sandbox) |
| 42 | [Canvas Record Form](https://help.zoho.com/portal/en/kb/crm/canvas-record-form) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/canvas-record-form) |
| 43 | [FAQs on Page Layouts](https://help.zoho.com/portal/en/kb/crm/page-layout-faq) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/page-layout-faq) |
| 44 | [FAQs: Customer support](https://help.zoho.com/portal/en/kb/crm/faqs-on-customer-support) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-on-customer-support) |
| 45 | [Data types in Formula Fields](https://help.zoho.com/portal/en/kb/crm/formula-fields-data-type) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/formula-fields-data-type) |
| 46 | [Building Formula Fields](https://help.zoho.com/portal/en/kb/crm/build-formula-fields) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/build-formula-fields) |
| 47 | [Custom buttons and custom links in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/custom-buttons-and-custom-links-in-zoho-crm-ios-app) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/custom-buttons-and-custom-links-in-zoho-crm-ios-app) |
| 48 | [FAQs: Page layouts](https://help.zoho.com/portal/en/kb/crm/faqs-page-layouts) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-page-layouts) |
| 49 | [FAQs : Field Customization](https://help.zoho.com/portal/en/kb/crm/faqs-field-customization) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-field-customization) |
| 50 | [Rollup summary field in Android app](https://help.zoho.com/portal/en/kb/crm/rollup-summary-field-in-android-app) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/rollup-summary-field-in-android-app) |
| 51 | [Copy Customization](https://help.zoho.com/portal/en/kb/crm/copy-customization-from-crm) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/copy-customization-from-crm) |

### Sample Image URLs (from top articles)
**[Types of Custom Fields](https://help.zoho.com/portal/en/kb/crm/types-of-fields)** — 46 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5783df65545c7e2425dd901bdd3605b6802063d2937b65dbb5c07310b0a19bd075ca6d6b525a1d2437357837423923f25d?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b577660bca885e6b396046d2bbdf1a8f86b6dece7d80f0b7ec81d67a331f8b4ced6aa74bbcbe5fc170efd283788075d26b2?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57a116be7e77c1fdd4c2b487addc216b65bc7d260e1d33ae06d54d6d0deb49e1b82a8ad70e4b1f6dd76d06f00a60902769?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57c9949c968fdee062803569f41968e66a659da13e61eb358c85f2cacd6639f44b249bdfa60312517b22dbcad18eea62a1?inline=true`
[View all 46 images in article →](https://help.zoho.com/portal/en/kb/crm/types-of-fields)

**[Working with Page Layouts](https://help.zoho.com/portal/en/kb/crm/create-page-layouts)** — 38 images
- `https://www.zohowebstatic.com/sites/default/files/crm/mpl-image1.jpg`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d612695e48102543cc3dbc330d308618a96a28d64978acb2e1872812aa05bb908790844d3f3f9c89f2c0237511e73294?inline=true`
- `https://www.zohowebstatic.com/sites/default/files/mpl-create-new.png`
- `https://www.zohowebstatic.com/sites/default/files/mpl-clone-layout.png`
[View all 38 images in article →](https://help.zoho.com/portal/en/kb/crm/create-page-layouts)

**[Voice of the Customer Settings — Enabling, disabling and more.](https://help.zoho.com/portal/en/kb/crm/voice-of-the-customer-settings)** — 28 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571a0bf2854440af044dd364b1527c12bea49a761d9a8ed01acfa12e1922a100b43602b018fb4a76265ac6f7e1cce05707?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e19ffa329327460ed7bf68dba327bc8089b5ea596399bec2789c8981cf22f5003e6916c7d05b884cddb1d2cdb73f0f88?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d9bc543d3638d068e6986a78ac5e8211af0673ffd83ff7c78eecb1798d00602ec68af9fa7f93b1aceeb2b5c88255cb75?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ee10d8d92f17cb7b92ed78a5a037fdf5353e5dfafc987ecfe14c6ed9315c6a3de839a3988cd793b985e74d0ad465f3bc?inline=true`
[View all 28 images in article →](https://help.zoho.com/portal/en/kb/crm/voice-of-the-customer-settings)

**[Customizing Module View Using the all-new Canvas design suite](https://help.zoho.com/portal/en/kb/crm/customizing-module-view-using-the-all-new-canvas-design-suite)** — 27 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5738a9ed9c8a7190007f26da2b8ff4e4f1dda095b34c7cc1eaa6e9aebf8ebf7fdc896154952132418ffe29e5df48e27c16?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571bbf265732d3d142ce47b367283fa298e625ff1e4fb7417b5f244086171b4a3e5c711b76bbb4e2fa4ab4820932d7f5a1?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57bc6b7a747e6bd98515b478e192c9564089c48764aedc23b1133724a9d5829f63d6bf35c1b934eb2e57230b4a901a5a17?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57eefd2982cdba0590e2f8f332757ba9b5783e3b96a86c31e9a0c78e6879b5ae8ecab36c63493eefd7239bbccc554bb739?inline=true`
[View all 27 images in article →](https://help.zoho.com/portal/en/kb/crm/customizing-module-view-using-the-all-new-canvas-design-suite)

**[Troubleshooting Settings and Customizations](https://help.zoho.com/portal/en/kb/crm/troubleshooting-settings-and-customization)** — 25 images
- `https://desk.zoho.in/galleryDocuments/edbsndcf0d1c48438530e2935964033ef20ec21ba46274738c5a1ecf279668eef691d01a4250050f4efd086f7f716be48753c2dd08b002b9e8c53624476276f7e2045?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsndcf0d1c48438530e2935964033ef20ec9abd490e98425c671cc9f75b56eaeead30499bffa87fa6afca154db69412ed648407d131bca36dc8c1f3bcb94ca66f80?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsndcf0d1c48438530e2935964033ef20ecbeea75fcf9e923123149c855a558275e6e6f1d126eb6fa939996585ce53650b707e45ad5b2d8900dbf37551b4b467c4f?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsndcf0d1c48438530e2935964033ef20ecca43026429669a3e3164b8338d0de6e3ce20a2b0af546d35d5b65a1fc8da02f4cbe27faa58071e3f3a695f9fa856e586?inline=true`
[View all 25 images in article →](https://help.zoho.com/portal/en/kb/crm/troubleshooting-settings-and-customization)

