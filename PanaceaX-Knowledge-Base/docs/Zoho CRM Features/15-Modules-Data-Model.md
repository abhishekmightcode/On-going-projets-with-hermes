# Modules & Data Model

> **Feature ID:** `15-Modules-Data-Model`  
> **Knowledge Base Articles:** 640  
> **Last Updated:** 2026-05-05

## Overview

Module creation, standard fields, custom fields, data types, formula fields, lookup fields

---

## 1. Core Functionality

### 1. FAQs: Zoho CRM for Google Ads

Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration. However, this does not erase the details fetched from the previous accounts. Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts. Can I configure more than one client account with Zoho CRM? Yes. If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would w
### 2. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made o
### 3. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 4. Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics

1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketplace requires an administrator to initiate the process. The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM. There may be some backend issues that prevent you from integrating advanced analytics into your CRM. In such cases, please feel free to contact the support team, support@zohocrm.com 2. Why am I unabl
### 5. Importing Contacts from G Suite

The Import Contacts feature helps you import contacts from G Suite to Zoho CRM. It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google account, every time you want to import. The imported contacts from G Suite will be assigned to you and shared with Zoho CRM users as per your organization's hierarchy. We recommend that you import business contacts only. Standard Field Mapping Zoho CRM Field Google Apps Field First Name - Last Name Name Email Email Phone Phone - Address - Website Birthday Birthday Description Notes To import contacts
### 6. Setting up Zoho Creator Integration

Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account. You should have a Zoho Creator account with any edition. If you do not have a Zoho Creator account, please create an account from Zoho Create. An account with the Free Edition will be automatically created. After which you can proceed with integrating it with Zoho CRM. Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for t
### 7. FAQs: Calls Module

How do I schedule a call? To schedule a call Go to the calls module on the CRM home page Click on Create Call Select Schedule a call option. On the Schedule a Call page fill in the required details. Click Schedule You call has been successfully scheduled. How do I delete a scheduled call? You can delete a scheduled call from the Calls details page from the Calls module. To delete a scheduled call Go to the Calls module. Click the All Calls dropdown. Choose Scheduled Calls . Click on the call you want to cancel. Click the ellipsis icon and then click Cancel C all. How do I set a call reminder f
### 8. Create category columns in reports

What are category columns? Category columns allow you to organize large data sets into categories. When viewing reports with a wide range of data, it can be challenging to get an overview of the entire dataset. This feature helps you to create user-defined categories to group data into easily digestible information. This enables you to draw context from the vast report values. In Zoho CRM, you can create two types of category columns: Number category columns - To group numerical data into columns Picklist category columns - To group picklist data into columns Let's understand this better with


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `MODULES`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `FAQs: Zoho CRM for Google Ads`
- `Schedule annual notifications for subscription renewals`
- `Consent Management`
- `Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/modules` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Modules & Data Model - Example Implementation
// Triggered on record creation/update

if(input.module == "FAQS: ZOHO CRM FOR GOOGLE ADS")
{
    // Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of clien
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

- [Customization-Builder](../Customization-Builder/README.md)
- [Data-Tools](../Data-Tools/README.md)
- [Validation-Rules](../Validation-Rules/README.md)

### This Feature Enables

- **Customization-Builder** -- shares data model and workflows
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

### FAQs: Zoho CRM for Google Ads
**Purpose:** Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho

**Key Points:**
Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM.
You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration.
However, this does not erase the details fetched from the previous accounts.
Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts.
Can I configure more than one client account with Zoho CRM.
If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would want to be tracked inside Zoho CRM


### Schedule annual notifications for subscription renewals
**Purpose:** Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.

**Key Points:**
Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.
Every month, they publish new editions of the magazines.
The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team.
The sales agents send reminder emails to the existing customers for annual subscription renewal.
If the subscription is renewed, they are sent the magazines every month.
To be sure that the renewal payment is made on time, they require a process to automatically start sending reminder emails 15 days before the renewal date, and upgrade the subscription status based on the payment


### Consent Management
**Purpose:** Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set con

**Key Points:**
Zoho CRM's consent management settings help you get consent from your prospects and customers.
We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details.
Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules.
It cannot be applied for team modules.
Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be.
You will begin by marking the records whose data needs to be processed after obtaining consent


### Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics
**Purpose:** 1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketp

**Key Points:**
Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM.
Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM.
The integration of apps from the marketplace requires an administrator to initiate the process.
The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM.
There may be some backend issues that prevent you from integrating advanced analytics into your CRM.
In such cases, please feel free to contact the support team, support@zohocrm


### Importing Contacts from G Suite
**Purpose:** The Import Contacts feature helps you import contacts from G Suite to Zoho CRM. It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google acc

**Key Points:**
The Import Contacts feature helps you import contacts from G Suite to Zoho CRM.
It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google account, every time you want to import.
The imported contacts from G Suite will be assigned to you and shared with Zoho CRM users as per your organization's hierarchy.
We recommend that you import business contacts only.
Standard Field Mapping Zoho CRM Field Google Apps Field First Name - Last Name Name Email Email Phone Phone - Address - Website Birthday Birthday Description Notes To import contacts from G Suite, follow these steps: In G Suite , click on (the Apps icon).
You will be redirected to Zoho CRM


### Setting up Zoho Creator Integration
**Purpose:** Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Z

**Key Points:**
Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account.
You should have a Zoho Creator account with any edition.
If you do not have a Zoho Creator account, please create an account from Zoho Create.
An account with the Free Edition will be automatically created.
After which you can proceed with integrating it with Zoho CRM.
Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for testing


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

- [FAQs: Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/faqs-google-adwords)
- [Schedule annual notifications for subscription renewals](https://help.zoho.com/portal/en/kb/crm/articles/automatic-schedule-notifications)
- [Consent Management](https://help.zoho.com/portal/en/kb/crm/articles/consent-management)
- [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics)
- [Importing Contacts from G Suite](https://help.zoho.com/portal/en/kb/crm/articles/import-contacts-g-suite)
- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [FAQs: Calls Module](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-calls-module)
- [Create category columns in reports](https://help.zoho.com/portal/en/kb/crm/articles/create-category-columns-in-reports)
- [Managing Process](https://help.zoho.com/portal/en/kb/crm/articles/managing-process-in-zoho-crm-android-app)
- [Kaizen posts 2023: SDK series](https://help.zoho.com/portal/en/kb/crm/articles/sdk-2023)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Setting up Zoho Writer Add-on](https://help.zoho.com/portal/en/kb/crm/articles/zoho-writer-crm-integration)
- [SurveyMonkey](https://help.zoho.com/portal/en/kb/crm/articles/surveymonkey-crm-integration)
- [FAQs: Developer Hub](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-developer-hub)
- [Managing Web Tabs](https://help.zoho.com/portal/en/kb/crm/articles/web-tabs)
- [Charts](https://help.zoho.com/portal/en/kb/crm/articles/create-charts)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/naijasmsportal-for-zoho-crm)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [RingCentral Video](https://help.zoho.com/portal/en/kb/crm/articles/ringcentral-video)
- [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/articles/set-email-notifications)
- [Address Locator for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/address-locator-for-zoho-crm)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [Including Opt-in Checkbox in Web Forms for Consent](https://help.zoho.com/portal/en/kb/crm/articles/opt-in-checkbox)
- [Adding Team Users](https://help.zoho.com/portal/en/kb/crm/articles/adding-team-users)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **14 KB articles** with **151 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Working with the Inventory modules in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/working-with-the-inventory-modules-in-zoho-crm-android-app-26-4-2026) | 50 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-the-inventory-modules-in-zoho-crm-android-app-26-4-2026) |
| 2 | [Configuring Team Module](https://help.zoho.com/portal/en/kb/crm/configuring-team-modules) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/configuring-team-modules) |
| 3 | [Configuring Module-Specific Settings](https://help.zoho.com/portal/en/kb/crm/configuring-module-specific-settings-in-zoho-crm-android-app) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/configuring-module-specific-settings-in-zoho-crm-android-app) |
| 4 | [Many-to-Many Module Association](https://help.zoho.com/portal/en/kb/crm/linking-modules) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/linking-modules) |
| 5 | [Working with Team Module](https://help.zoho.com/portal/en/kb/crm/working-with-team-modules) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-team-modules) |
| 6 | [An overview of module views](https://help.zoho.com/portal/en/kb/crm/module-views) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/module-views) |
| 7 | [Team modules in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/team-modules-in-zoho-crm-ios-app) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/team-modules-in-zoho-crm-ios-app) |
| 8 | [Team modules in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/team-modules-in-zoho-crm-android-app) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/team-modules-in-zoho-crm-android-app) |
| 9 | [FAQs: Team Module](https://help.zoho.com/portal/en/kb/crm/faqs-team-module) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-team-module) |
| 10 | [FAQs: Modules](https://help.zoho.com/portal/en/kb/crm/faqs-modules) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-modules) |
| 11 | [FAQs: Calls Module](https://help.zoho.com/portal/en/kb/crm/faqs-on-calls-module) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-on-calls-module) |
| 12 | [Team Module: Read-Me-First Guide for Admins](https://help.zoho.com/portal/en/kb/crm/team-modules-read-me-first-guide-for-admins) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/team-modules-read-me-first-guide-for-admins) |
| 13 | [Zoho CRM's Core Data Model and How You Extend It Safely](https://help.zoho.com/portal/en/kb/crm/zoho-crm-s-core-data-model-and-how-you-extend-it-safely) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-crm-s-core-data-model-and-how-you-extend-it-safely) |
| 14 | [Appointments module in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/appointments-module-in-zoho-crm-ios-app) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/appointments-module-in-zoho-crm-ios-app) |

### Sample Image URLs (from top articles)
**[Working with the Inventory modules in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/working-with-the-inventory-modules-in-zoho-crm-android-app-26-4-2026)** — 50 images
- `https://desk.zoho.in/galleryDocuments/edbsnb7e38b636eb93010941ea9e4d72f95fa11db9797d0955a54e94c4c57debbe3a2b1d3e3dbb4ae592a636c5ef552a867cdbf5105ceaf87bd0802ab5d6e1e281f71?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsnb7e38b636eb93010941ea9e4d72f95faac66482c1638727ec38096a6e27f7b0b176dd7a5e7294c34d5c4d557769005304d70ef3c8024abadf025c5ee2f63bcdf?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsnb7e38b636eb93010941ea9e4d72f95fa922f1a2b433599ee8c0a5b2bc94c2f23ca769fdc540748744c7af261de4e64f288e8b533f5fc99a04125efb28f73cda0?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsnb7e38b636eb93010941ea9e4d72f95fa9402cbb0ede44370072f46fb9865036ff655bab49ba36f20d52fcdec87044c3a8f21fe9a11a19135fa56f3090fe8a753?inline=true`
[View all 50 images in article →](https://help.zoho.com/portal/en/kb/crm/working-with-the-inventory-modules-in-zoho-crm-android-app-26-4-2026)

**[Configuring Team Module](https://help.zoho.com/portal/en/kb/crm/configuring-team-modules)** — 23 images
- `https://desk.zoho.in/galleryDocuments/edbsne8ef3e2eb643dbfee7c7045d83210932e95df2f62cc03f94852465c23b8ddf6badcb7d497504046752d384f4d157f61ccdedfe02b97df3a9ad13cb7f8cde3a20?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsne8ef3e2eb643dbfee7c7045d832109328f5fa4653ea6dbef521d3f869615ced0dc3abd2762e193aca4025d385c3aa30e178a2ae05fb6fe805ce041ffb0978b0e?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579c79a17ee56f5df56d0b86fd9f458b547d65c0b3746a8427411a2ae04ebf21274a7b4eab31793291a144cecc36880db9?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57bdacbd6f0d4c3942fcf358fc88edcb28fa48397c5c9d8a8412011115d2b4796b3a56bca5076b29fceef58ffee44b15e8?inline=true`
[View all 23 images in article →](https://help.zoho.com/portal/en/kb/crm/configuring-team-modules)

**[Configuring Module-Specific Settings](https://help.zoho.com/portal/en/kb/crm/configuring-module-specific-settings-in-zoho-crm-android-app)** — 14 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5792dedf00b5f1a6b48c8a5f9ac41d0b7e568f62460d31cece67d03b3b9e8bb709c769b8ea99f91dc5fe7bc241208a42c4?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ed1d4635751351571e814a416899d1167a27d4dc90a6b6acb26c173976ab734d4bdc577e636977d48e3913bcc79896ad?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f0a0719138efdc558369d8d36a2c5999aa496c1f73cd4c189a2293ea1f6d52351c79d9826884d72d364e53529a9b7110?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5782e57fcbcf3b59809210678ccc969a98fbe534088fd19e7a71fdeacae43e630727a3972753f46f64f70598958083cebe?inline=true`
[View all 14 images in article →](https://help.zoho.com/portal/en/kb/crm/configuring-module-specific-settings-in-zoho-crm-android-app)

**[Many-to-Many Module Association](https://help.zoho.com/portal/en/kb/crm/linking-modules)** — 12 images
- `https://desk.zoho.in/galleryDocuments/edbsn919a3b2f9f6c11853f287881feac30d02039e914946c8888df559bcd6d76131fe0b804cf6d982efb8f9bf223fcfe9946b5eb90f5065bb154525ceb402e61b109?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn919a3b2f9f6c11853f287881feac30d026e211add1d99d57bd76d2f2b72c94e4b895eb4f9ed2fd0f4dc804ea48c2a36f9ded4f4a46926e34bb33dd5bb0e1916b?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn919a3b2f9f6c11853f287881feac30d0c8c679540c113dfe9bafba46aea0e8cf3857997ae3ea61eb5e4bc994a47604ea3fe2b15c8b4808a21599d99e7253b589?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn919a3b2f9f6c11853f287881feac30d09f26fc40ea2159b54ef130d572acb2741ae64ce6e8679688e3b5ebd5531f9114de430c02aafb0ca0d82ad8e6510e7aa0?inline=true`
[View all 12 images in article →](https://help.zoho.com/portal/en/kb/crm/linking-modules)

**[Working with Team Module](https://help.zoho.com/portal/en/kb/crm/working-with-team-modules)** — 12 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d40592cfb7fcaa43f4d94c5956122f8c82567aeec9869f57313367e01004ca61d698d7f51b422dac459294b8d5142a2a?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b578d89c6267a77e794d9266b45b1ebe3d4bdd8130fcf6c883c8d7897e94731aea204c804e2d1d898834c3b8fa599cf3075?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57c7bc2f4efaa47f753d062a6ad399521a24b3352e0007564228b22eca27fdfcccd3902035dc17c1fbf4a3a992b44cfc62?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f2d37fe6196231d9162cabd3111495f2047406fae93dfd2dff6045dc1741e10cab7d9d7cd2ab8357c8621b33a9665129?inline=true`
[View all 12 images in article →](https://help.zoho.com/portal/en/kb/crm/working-with-team-modules)

