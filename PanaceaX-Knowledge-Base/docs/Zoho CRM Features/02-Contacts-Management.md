# Contacts & Accounts Management

> **Feature ID:** `02-Contacts-Management`  
> **Knowledge Base Articles:** 757  
> **Last Updated:** 2026-05-05

## Overview

Contact records, organization accounts, duplicate management, and relationship mapping

---

## 1. Core Functionality

### 1. Spotfone

Spotfone is a cloud telephony platform integrated with Zoho PhoneBridge to provide better communication to your customers. Perform all call-related activities right inside your CRM account. Setup integration To set up this integration, Go to Setup > Channels > Telephony. Choose Spotfone from the PhoneBridge Marketplace . Click Integrate . Click Get it now . For configuration steps, click here . Using Spotfone integration Spotfone for Zoho PhoneBridge help you perform all your call related activities directly within your CRM account. Once the set up is done, you can do the following: When you r
### 2. FAQs: Zoho CRM for Google Ads

Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration. However, this does not erase the details fetched from the previous accounts. Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts. Can I configure more than one client account with Zoho CRM? Yes. If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would w
### 3. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 4. Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics

1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketplace requires an administrator to initiate the process. The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM. There may be some backend issues that prevent you from integrating advanced analytics into your CRM. In such cases, please feel free to contact the support team, support@zohocrm.com 2. Why am I unabl
### 5. Voice based forecast analysis

As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams. The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exactly know why your deals are falling out of the pipeline. Or you may not know what is it that you are
### 6. Importing Contacts from G Suite

The Import Contacts feature helps you import contacts from G Suite to Zoho CRM. It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google account, every time you want to import. The imported contacts from G Suite will be assigned to you and shared with Zoho CRM users as per your organization's hierarchy. We recommend that you import business contacts only. Standard Field Mapping Zoho CRM Field Google Apps Field First Name - Last Name Name Email Email Phone Phone - Address - Website Birthday Birthday Description Notes To import contacts
### 7. Setting up Zoho Creator Integration

Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account. You should have a Zoho Creator account with any edition. If you do not have a Zoho Creator account, please create an account from Zoho Create. An account with the Free Edition will be automatically created. After which you can proceed with integrating it with Zoho CRM. Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for t
### 8. Zia for Workflow Rules

You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people. However, keeping track of triggers made through workflow rules to see what works best and what doesn't could be cumbersome. Zia does just that for you. Zia brings AI to your workflow automation processes by detecting anomalies and provide suggestions for your workflow rules. Zia also identifies and prevents you from making mistakes, such as sending multiple email templates to the same customer on the same day. Availability Permission Required Us


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `CONTACTS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Spotfone`
- `FAQs: Zoho CRM for Google Ads`
- `Consent Management`
- `Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/contacts` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Contacts & Accounts Management - Example Implementation
// Triggered on record creation/update

if(input.module == "SPOTFONE")
{
    // Spotfone is a cloud telephony platform integrated with Zoho PhoneBridge to provide better communication to your customers. Perform all call-related ac
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
- [Deals-Pipeline](../Deals-Pipeline/README.md)
- [Activities](../Activities/README.md)
- [Tagging-Feeds](../Tagging-Feeds/README.md)
- [Customization-Builder](../Customization-Builder/README.md)

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

### Spotfone
**Purpose:** Spotfone is a cloud telephony platform integrated with Zoho PhoneBridge to provide better communication to your customers. Perform all call-related activities right inside your CRM account. Setup inte

**Key Points:**
Spotfone is a cloud telephony platform integrated with Zoho PhoneBridge to provide better communication to your customers.
Perform all call-related activities right inside your CRM account.
Setup integration To set up this integration, Go to Setup > Channels > Telephony.
Choose Spotfone from the PhoneBridge Marketplace.
For configuration steps, click here.
Using Spotfone integration Spotfone for Zoho PhoneBridge help you perform all your call related activities directly within your CRM account


### FAQs: Zoho CRM for Google Ads
**Purpose:** Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho

**Key Points:**
Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM.
You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration.
However, this does not erase the details fetched from the previous accounts.
Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts.
Can I configure more than one client account with Zoho CRM.
If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would want to be tracked inside Zoho CRM


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


### Voice based forecast analysis
**Purpose:** As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you ar

**Key Points:**
As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc).
By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams.
The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exactly know why your deals are falling out of the pipeline.
Or you may not know what is it that you are doing well, that is giving you winning deals, for that matter.
Knowledge of this winning/losing pattern will help you set better goals and also meet them better.
This is where VoC enters the picture


### Importing Contacts from G Suite
**Purpose:** The Import Contacts feature helps you import contacts from G Suite to Zoho CRM. It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google acc

**Key Points:**
The Import Contacts feature helps you import contacts from G Suite to Zoho CRM.
It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google account, every time you want to import.
The imported contacts from G Suite will be assigned to you and shared with Zoho CRM users as per your organization's hierarchy.
We recommend that you import business contacts only.
Standard Field Mapping Zoho CRM Field Google Apps Field First Name - Last Name Name Email Email Phone Phone - Address - Website Birthday Birthday Description Notes To import contacts from G Suite, follow these steps: In G Suite , click on (the Apps icon).
You will be redirected to Zoho CRM


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

- [Spotfone](https://help.zoho.com/portal/en/kb/crm/articles/integrate-spotfone)
- [FAQs: Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/faqs-google-adwords)
- [Consent Management](https://help.zoho.com/portal/en/kb/crm/articles/consent-management)
- [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics)
- [Voice based forecast analysis](https://help.zoho.com/portal/en/kb/crm/articles/voice-based-forecast-analysis)
- [Importing Contacts from G Suite](https://help.zoho.com/portal/en/kb/crm/articles/import-contacts-g-suite)
- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [Zia for Workflow Rules](https://help.zoho.com/portal/en/kb/crm/articles/zia-intelligence-automation)
- [Managing Process](https://help.zoho.com/portal/en/kb/crm/articles/managing-process-in-zoho-crm-android-app)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Setting up Zoho Writer Add-on](https://help.zoho.com/portal/en/kb/crm/articles/zoho-writer-crm-integration)
- [SurveyMonkey](https://help.zoho.com/portal/en/kb/crm/articles/surveymonkey-crm-integration)
- [Kaizen posts 2024: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2024)
- [FAQs: Developer Hub](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-developer-hub)
- [Managing Web Tabs](https://help.zoho.com/portal/en/kb/crm/articles/web-tabs)
- [Charts](https://help.zoho.com/portal/en/kb/crm/articles/create-charts)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [What is ABM?](https://help.zoho.com/portal/en/kb/crm/articles/what-is-abm)
- [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/naijasmsportal-for-zoho-crm)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [Decision Guide for Territory Management](https://help.zoho.com/portal/en/kb/crm/articles/territory-decision-management)
- [RingCentral Video](https://help.zoho.com/portal/en/kb/crm/articles/ringcentral-video)
- [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/articles/set-email-notifications)
- [Address Locator for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/address-locator-for-zoho-crm)
- [WeChat for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/wechat-for-zoho-crm-3-8-2021)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **21 KB articles** with **182 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Analytics for Zia Best Time to Contact](https://help.zoho.com/portal/en/kb/crm/zia-best-time-to-contact-analytics) | 22 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-best-time-to-contact-analytics) |
| 2 | [Engagement strategy for target accounts](https://help.zoho.com/portal/en/kb/crm/engagement-strategy-for-target-accounts) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/engagement-strategy-for-target-accounts) |
| 3 | [Understand your CRM Account](https://help.zoho.com/portal/en/kb/crm/understand-crm-account) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/understand-crm-account) |
| 4 | [Account overview dashboard](https://help.zoho.com/portal/en/kb/crm/account-overview-dashboard-24-2-2026) | 19 | [View Article](https://help.zoho.com/portal/en/kb/crm/account-overview-dashboard-24-2-2026) |
| 5 | [Overall Account Insights](https://help.zoho.com/portal/en/kb/crm/overall-account-insights) | 15 | [View Article](https://help.zoho.com/portal/en/kb/crm/overall-account-insights) |
| 6 | [Managing CRM Account Settings](https://help.zoho.com/portal/en/kb/crm/manage-account-settings) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/manage-account-settings) |
| 7 | [Contact roles support for deals in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/contact-roles-support-for-deals-in-zoho-crm-ios-app) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/contact-roles-support-for-deals-in-zoho-crm-ios-app) |
| 8 | [Managing Zoho Account Settings](https://help.zoho.com/portal/en/kb/crm/crm-setup-zoho-account-settings) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/crm-setup-zoho-account-settings) |
| 9 | [Synchronizing the G Suite Contacts](https://help.zoho.com/portal/en/kb/crm/synchronize-g-suite-contacts) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/synchronize-g-suite-contacts) |
| 10 | [Associate a contact with multiple companies or accounts](https://help.zoho.com/portal/en/kb/crm/associate-a-contact-with-multiple-companies-or-accounts) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/associate-a-contact-with-multiple-companies-or-accounts) |
| 11 | [Creating Accounts](https://help.zoho.com/portal/en/kb/crm/create-accounts) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-accounts) |
| 12 | [Set up your Organization Account](https://help.zoho.com/portal/en/kb/crm/get-started-setup-organization-account) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/get-started-setup-organization-account) |
| 13 | [Working with Contacts](https://help.zoho.com/portal/en/kb/crm/contacts-overview) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/contacts-overview) |
| 14 | [Synchronizing Meetings, Contacts, and Tasks with Office 365](https://help.zoho.com/portal/en/kb/crm/sync-meetings-contacts-tasks-with-office365) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/sync-meetings-contacts-tasks-with-office365) |
| 15 | [Migrating Data Between Zoho CRM Accounts](https://help.zoho.com/portal/en/kb/crm/migrating-between-zoho-crm-accounts) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/migrating-between-zoho-crm-accounts) |
| 16 | [Managing Accounts](https://help.zoho.com/portal/en/kb/crm/manage-accounts) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/manage-accounts) |
| 17 | [Creating Contacts](https://help.zoho.com/portal/en/kb/crm/create-contacts) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-contacts) |
| 18 | [Deleting the Zoho CRM Account](https://help.zoho.com/portal/en/kb/crm/close-zoho-crm-account) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/close-zoho-crm-account) |
| 19 | [Best Mode to Contact Customers](https://help.zoho.com/portal/en/kb/crm/best-mode-to-contact-customers) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/best-mode-to-contact-customers) |
| 20 | [Best Time to Contact Customers](https://help.zoho.com/portal/en/kb/crm/using-best-time-to-contact) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/using-best-time-to-contact) |
| 21 | [FAQs: Contact Management](https://help.zoho.com/portal/en/kb/crm/contact-management) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/contact-management) |

### Sample Image URLs (from top articles)
**[Analytics for Zia Best Time to Contact](https://help.zoho.com/portal/en/kb/crm/zia-best-time-to-contact-analytics)** — 22 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b577fa9cadc9c1960d7311a3d86f7330569766d83db2882133a78f78a32ed61dda34bf89e5665099cd508ae42e890bc605b?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57cf3d177879cb6e3bffb6130ba92862578316ce03cca3fcb4a707118ff7b89872f03113334530c7eb378d44da4e93bbe1?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b577d8f28ea28eac353dc53a2d638e4a82b5e6ce6277ab0f32d1ca9f09b27439599c0cdfbb1c04614d57a6a08cbe64cca2d?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57bf5f96e23fd5f80fbea5113ffedcf75501e24484acbf4b6d78db7a0412a2f22ce2eeca4e48c51202b7d1a857b59de07a?inline=true`
[View all 22 images in article →](https://help.zoho.com/portal/en/kb/crm/zia-best-time-to-contact-analytics)

**[Engagement strategy for target accounts](https://help.zoho.com/portal/en/kb/crm/engagement-strategy-for-target-accounts)** — 20 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57fb9298dee1af5d1a2278d2a6c4bfbb025e3f7c2457008785d6039be6201e474caea86ba9fb68c13272971ec6d92c13d1?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579e004c2e3d55c5040b764b1f21d65c6d117499819b1677299e2bf3e06759f2a30d657f4396993e573753239f51b28945?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e18acbd2203d077c110793b051fc343adc582a7d19dc17202f4b60017ff7a44c719901b280a6dab55d5bdc1a496649af?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b576c55b485feaaca59d2d6d3d45764e1b2f71fd306296931998e554408f802df34804f1af36d701fdc1356acbdc5513e6e?inline=true`
[View all 20 images in article →](https://help.zoho.com/portal/en/kb/crm/engagement-strategy-for-target-accounts)

**[Understand your CRM Account](https://help.zoho.com/portal/en/kb/crm/understand-crm-account)** — 20 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579cac74d23bc36027c1b44f96a21df2ea400f4239767b53848743e7f404cfd84ab076a2d88187d183e43d2ecee8dd466b?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsna597f2a01f7490217648912e7cea1862cbaf931fcb4b9776365217525c5a4848d491f6254fe685c81dc982d4eeba9e62e0cc55afde6752947d66cabd8262066c?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsna597f2a01f7490217648912e7cea18621db957faee6cc5352608dde5191ab588dc714307cae898ae7106e424f634d099fca64213ec3db960bb0c717628e0cf08?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsna597f2a01f7490217648912e7cea18629d7a966865ad80003f77ddf2407f349af31045f893308e2b20d63b0a3da03304ab69db2bd628a0ed75cafa038c687959?inline=true`
[View all 20 images in article →](https://help.zoho.com/portal/en/kb/crm/understand-crm-account)

**[Account overview dashboard](https://help.zoho.com/portal/en/kb/crm/account-overview-dashboard-24-2-2026)** — 19 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5757787fd3184f1b389a10099d5cba9cae05da8412b7b146a5a4083ff2126d2f6ed85f885b09c6920bed5c95d4abee45da?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5781cf9d47a9d0ba9171c75c673646ffce0dc17cfaf34f759f1cad208dd699d61eab01579d12cc1ffe60051afe96f11840?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57adbc72535cf17dc10dd33bc1d1485d77e9ec0a775dafd0d5a8ada50e429e66985a8275737d4b8a709789518fef3c4e61?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57096038f0e4af93747ffe70c3735cce9ab1eda895d5fdb3c59926443983c2a93c67b1a11e58e09351248a6b084c9d7524?inline=true`
[View all 19 images in article →](https://help.zoho.com/portal/en/kb/crm/account-overview-dashboard-24-2-2026)

**[Overall Account Insights](https://help.zoho.com/portal/en/kb/crm/overall-account-insights)** — 15 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57078064c2d7666f29b22e13b3a5655de037b8783983ce3b5f20a372fec5dc6805ae2d899a52229e04d1cf6e19d8fd0ad7?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b570e2c3bc30cf77d8ab175fb7f3cefe1d259d1737a939f7473456ed0588ce359fdd61f0b59ccc23bcfd4ec780dd203b920?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5744f508d164ff91258bf14bed7269659004c18d337e33d0ebd07519b8cc92c428fb487a2cc26b37bfc7fbe511db10c787?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57a58b18f6a4108b65bd88861ae319dd39d9df4d96b6c6fac729d2bfdba18bb3cf9528f6a57ee0b0a60998693a4b521317?inline=true`
[View all 15 images in article →](https://help.zoho.com/portal/en/kb/crm/overall-account-insights)

