# Integrations & Telephony

> **Feature ID:** `17-Integrations`  
> **Knowledge Base Articles:** 288  
> **Last Updated:** 2026-05-05

## Overview

Third-party integrations, telephony, Google, Microsoft, Zoho suite integrations

---

## 1. Core Functionality

### 1. Spotfone

Spotfone is a cloud telephony platform integrated with Zoho PhoneBridge to provide better communication to your customers. Perform all call-related activities right inside your CRM account. Setup integration To set up this integration, Go to Setup > Channels > Telephony. Choose Spotfone from the PhoneBridge Marketplace . Click Integrate . Click Get it now . For configuration steps, click here . Using Spotfone integration Spotfone for Zoho PhoneBridge help you perform all your call related activities directly within your CRM account. Once the set up is done, you can do the following: When you r
### 2. FAQs: Zoho CRM for Google Ads

Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration. However, this does not erase the details fetched from the previous accounts. Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts. Can I configure more than one client account with Zoho CRM? Yes. If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would w
### 3. Zia Usage Data Mapping of Events

This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction. Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing. It enables seamless import of usage data from various sources into Zoho CRM, providing accurate insights on customer engagement, retention, and personalized
### 4. Zoho CRM for Google Ads

Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites. By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI). Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to ma
### 5. Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics

1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketplace requires an administrator to initiate the process. The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM. There may be some backend issues that prevent you from integrating advanced analytics into your CRM. In such cases, please feel free to contact the support team, support@zohocrm.com 2. Why am I unabl
### 6. Importing Contacts from G Suite

The Import Contacts feature helps you import contacts from G Suite to Zoho CRM. It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google account, every time you want to import. The imported contacts from G Suite will be assigned to you and shared with Zoho CRM users as per your organization's hierarchy. We recommend that you import business contacts only. Standard Field Mapping Zoho CRM Field Google Apps Field First Name - Last Name Name Email Email Phone Phone - Address - Website Birthday Birthday Description Notes To import contacts
### 7. Setting up Zoho Creator Integration

Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account. You should have a Zoho Creator account with any edition. If you do not have a Zoho Creator account, please create an account from Zoho Create. An account with the Free Edition will be automatically created. After which you can proceed with integrating it with Zoho CRM. Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for t
### 8. Kaizen posts 2023: SDK series

Here is a complete list of Kaizen posts related to SDKs published in 2023 . Sl. No. Title Description 1 PHP SDK - Part I Learn how to set up and initialize Zoho CRM's PHP SDK with this step-by-step guide. 2 PHP SDK - Part II Learn how to perform Record Operations with sample codes in this post. Read more for detailed information on getting started with your SDK journey. 3 PHP SDK - Part III Discover new use cases and expand your horizons with additional examples in Record and Send Mail Operations. Read more for further information. 4 Bulk Read in PHP SDK This post delves into the utilization o


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `INTEGRATIONS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Spotfone`
- `FAQs: Zoho CRM for Google Ads`
- `Zia Usage Data Mapping of Events`
- `Zoho CRM for Google Ads`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/integrations` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Integrations & Telephony - Example Implementation
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

- [Activities](../Activities/README.md)
- [Email-Tools](../Email-Tools/README.md)
- [Documents-Management](../Documents-Management/README.md)

### This Feature Enables

- **Activities** -- shares data model and workflows
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


### Zia Usage Data Mapping of Events
**Purpose:** This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is

**Key Points:**
This guide helps you with the mapping of events of your usage data under Zia.
Before getting into greater detail, let's quickly revise the important terms.
Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction.
Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing.
It enables seamless import of usage data from various sources into Zoho CRM, providing accurate insights on customer engagement, retention, and personalized service delivery.
All businesses need transactional data as a base to study user purchase behavior on metrics like customer details, date and time, payment methods, discounts, and inventory movements


### Zoho CRM for Google Ads
**Purpose:** Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner we

**Key Points:**
Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites.
By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI).
Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to make strategic marketing decisions for your business.
If you use Google Ads to drive potential customers to your website and a customer relationship management system (CRM) to track offline sales made through phone calls, emails, or direct sales, it can be difficult for your business to determine how your online campaign investments lead to offline conversion data stored in Zoho CRM.
With Zoho CRM for Google Ads , you can now import your Google Ads marketing investments into Zoho CRM so you can see which keywords and campaigns are responsible for each offline sale.
Plus, you can also export Zoho CRM sales data into Google Ads so you can better optimize your bids and budgets to yield maximum revenue and profits


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
- [Zia Usage Data Mapping of Events](https://help.zoho.com/portal/en/kb/crm/articles/usage-data-event-mapping)
- [Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/google-ads-crm-integration)
- [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics)
- [Importing Contacts from G Suite](https://help.zoho.com/portal/en/kb/crm/articles/import-contacts-g-suite)
- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [Kaizen posts 2023: SDK series](https://help.zoho.com/portal/en/kb/crm/articles/sdk-2023)
- [Kaizen posts 2024: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2024)
- [Installing the MS Word Plug-in](https://help.zoho.com/portal/en/kb/crm/articles/install-ms-word-plug-in-crm-integration)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [Address Locator for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/address-locator-for-zoho-crm)
- [WeChat for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/wechat-for-zoho-crm-3-8-2021)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [SharePoint for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/sharepoint-for-zoho-crm)
- [Zoho Survey Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-survey-crm-integration)
- [Mega Meeting](https://help.zoho.com/portal/en/kb/crm/articles/mega-meeting)
- [Cisco Telephony Integration](https://help.zoho.com/portal/en/kb/crm/articles/cisco-telephony-integration-beta-release)
- [Zoho Projects Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/overview-zoho-projects-crm-integration)
- [Using Zoho Finance Suite Integration](https://help.zoho.com/portal/en/kb/crm/articles/use-zoho-finance-suite-crm-integration)
- [Acting on VoC insights](https://help.zoho.com/portal/en/kb/crm/articles/acting-on-voc-insights)
- [FUJIFILM IWpro Document for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/fujifilm-iwpro-document-for-zoho-crm)
- [HubSpot for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/hubspot-for-zoho-crm)
- [OneNote](https://help.zoho.com/portal/en/kb/crm/articles/onenote-integration)
- [Zendesk](https://help.zoho.com/portal/en/kb/crm/articles/zendesk-crm-integration)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **29 KB articles** with **304 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Using Zoho Finance Suite Integration](https://help.zoho.com/portal/en/kb/crm/use-zoho-finance-suite-crm-integration) | 29 | [View Article](https://help.zoho.com/portal/en/kb/crm/use-zoho-finance-suite-crm-integration) |
| 2 | [Working with Zoho Forms Integration](https://help.zoho.com/portal/en/kb/crm/zoho-forms-crm-integration) | 24 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-forms-crm-integration) |
| 3 | [Business messaging using WhatsApp for Business: Integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/business-messaging-using-whatsapp-for-business-integration-with-zoho-crm) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/business-messaging-using-whatsapp-for-business-integration-with-zoho-crm) |
| 4 | [Setting up SalesIQ Integration](https://help.zoho.com/portal/en/kb/crm/zoho-salesiq-crm-integrations) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-salesiq-crm-integrations) |
| 5 | [Setting up Zoho Webinar Integration](https://help.zoho.com/portal/en/kb/crm/zoho-webinar) | 21 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-webinar) |
| 6 | [FAQs: Zoho CRM Integration with Zoho Projects](https://help.zoho.com/portal/en/kb/crm/faqs-zoho-crm-projects) | 17 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-zoho-crm-projects) |
| 7 | [Working with Zoho Desk Integration](https://help.zoho.com/portal/en/kb/crm/zoho-desk-crm-integration) | 16 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-desk-crm-integration) |
| 8 | [Avaya Cloud Office Integration](https://help.zoho.com/portal/en/kb/crm/avaya) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/avaya) |
| 9 | [FAQs: Zoho CRM Integration with Other Apps](https://help.zoho.com/portal/en/kb/crm/faqs-integration-with-other-apps) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-integration-with-other-apps) |
| 10 | [Configure Zoho Projects Integration](https://help.zoho.com/portal/en/kb/crm/configure-projects-crm-integration) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/configure-projects-crm-integration) |
| 11 | [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/zoho-crm-integration-zoho-desk) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-crm-integration-zoho-desk) |
| 12 | [Setting up and Configuring Zoho Finance Suite Integration](https://help.zoho.com/portal/en/kb/crm/zoho-finance-suite-crm-integration) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-finance-suite-crm-integration) |
| 13 | [FAQs: Zoho CRM Integration with Zoho Bookings](https://help.zoho.com/portal/en/kb/crm/is-it-possible-to-book-appointments-in-zoho-crm-using-zoho-bookings) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/is-it-possible-to-book-appointments-in-zoho-crm-using-zoho-bookings) |
| 14 | [Working with Zoho Projects Integration](https://help.zoho.com/portal/en/kb/crm/use-zoho-projects-crm-integration) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/use-zoho-projects-crm-integration) |
| 15 | [Troubleshooting Zoho CRM integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/troubleshooting-zoho-desk-integration-with-zoho-crm) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-zoho-desk-integration-with-zoho-crm) |
| 16 | [Setting up Zoho Cliq Integration](https://help.zoho.com/portal/en/kb/crm/zoho-cliq-crm-integration) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-cliq-crm-integration) |
| 17 | [Microsoft Teams integration](https://help.zoho.com/portal/en/kb/crm/teams-integration) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/teams-integration) |
| 18 | [Webinar integration in Sandbox](https://help.zoho.com/portal/en/kb/crm/webinar-integration-in-sandbox) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/webinar-integration-in-sandbox) |
| 19 | [Cisco Telephony Integration](https://help.zoho.com/portal/en/kb/crm/cisco-telephony-integration-beta-release) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/cisco-telephony-integration-beta-release) |
| 20 | [Desk integration in sandbox](https://help.zoho.com/portal/en/kb/crm/desk-integration-in-sandbox) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/desk-integration-in-sandbox) |
| 21 | [Survey integration in Sandbox](https://help.zoho.com/portal/en/kb/crm/survey-integration-in-sandbox) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/survey-integration-in-sandbox) |
| 22 | [FAQs: Zoho CRM Integration with Zoho Survey](https://help.zoho.com/portal/en/kb/crm/faqs-zoho-crm-integration-with-zoho-survey) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-zoho-crm-integration-with-zoho-survey) |
| 23 | [Integrate with RingCentral](https://help.zoho.com/portal/en/kb/crm/integrate-with-ringcentral-29-8-2024) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/integrate-with-ringcentral-29-8-2024) |
| 24 | [FAQs: Zoho CRM Integration with Zoho SalesIQ](https://help.zoho.com/portal/en/kb/crm/faqs-crm-integration-with-sales-iq) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-crm-integration-with-sales-iq) |
| 25 | [Social integration in sandbox](https://help.zoho.com/portal/en/kb/crm/social-integration-in-sandbox) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/social-integration-in-sandbox) |
| 26 | [Notification SMS integration with Zoho CRM - An Overview](https://help.zoho.com/portal/en/kb/crm/notification-sms-integration-with-zoho-crm) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/notification-sms-integration-with-zoho-crm) |
| 27 | [Google chat integration](https://help.zoho.com/portal/en/kb/crm/google-chat-integration) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/google-chat-integration) |
| 28 | [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/set-up-creator-crm-integration) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/set-up-creator-crm-integration) |
| 29 | [Zoho Directory integration with CRM](https://help.zoho.com/portal/en/kb/crm/zoho-directory-integration-with-crm) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-directory-integration-with-crm) |

### Sample Image URLs (from top articles)
**[Using Zoho Finance Suite Integration](https://help.zoho.com/portal/en/kb/crm/use-zoho-finance-suite-crm-integration)** — 29 images
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqzf07ce11005144c78b7aee98149bb7e06`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqze574afd099794ab7a9903f7a44faaca7`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqzd65f02c4031c4a90841a7ce9019b01ca`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqz2c385061a95e49048761b970905d6413`
[View all 29 images in article →](https://help.zoho.com/portal/en/kb/crm/use-zoho-finance-suite-crm-integration)

**[Working with Zoho Forms Integration](https://help.zoho.com/portal/en/kb/crm/zoho-forms-crm-integration)** — 24 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b572405a4a87ee1220d1cfb6d824397549dc00a2ec9114e415f679a7a1ceb5ae046328fb81ee71bb0bb9c2b07ae0daf6a27?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d760de2134b87e4fe0bf4f83d6d7f07fbf5e29fffe63421464016e7e5fa756cfd6339bc1aec2222de2a0182a94fd2f33?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57efc61fbb69a8ffd4b3c8dc88596fb7c3e666432b545d46a779c70f12829528cf4df09e8a3b4d968e7c88a03597d91474?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579d35a5caecacccb8e269d73809d133e1cf5a71469b0bb4b9341936a567e542b2ffd47db3e96fb54a52d7095ff41293b4?inline=true`
[View all 24 images in article →](https://help.zoho.com/portal/en/kb/crm/zoho-forms-crm-integration)

**[Business messaging using WhatsApp for Business: Integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/business-messaging-using-whatsapp-for-business-integration-with-zoho-crm)** — 23 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d4cd3259f0b88bc056ad0a028331df24d5796aa2bbac9219345dd0c1365e620a8c9f8ca4907092e2275746c5077a4dda?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5740f379bc0b15f9e633f260c7dc0d42ded2cd7f297e8680fce5fdb6c02c0e1afc877579a5a1b610880cb95d8b1793d291?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579d2e9eb64c646f99ab6eb347afaf094dc7181b57879cf79d109defb0f74c4f0b818c6bbec685164eb3de8a93ff3ec37b?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d1f7c9307eb6fea43649a9d0afdd8b3e80b584591b4ceac6d3db50101b5808203eb005196da6dd417b3cc120d6d5967a?inline=true`
[View all 23 images in article →](https://help.zoho.com/portal/en/kb/crm/business-messaging-using-whatsapp-for-business-integration-with-zoho-crm)

**[Setting up SalesIQ Integration](https://help.zoho.com/portal/en/kb/crm/zoho-salesiq-crm-integrations)** — 23 images
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqzbed8ffe607d9459088aaa49e68b18a97`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqz659ac12949644ec78cab5437b344bc98`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqz7bf97c3167bb497db75259c4ab7b72e8`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqz17849bcd12534af695f9c11899afc7bd`
[View all 23 images in article →](https://help.zoho.com/portal/en/kb/crm/zoho-salesiq-crm-integrations)

**[Setting up Zoho Webinar Integration](https://help.zoho.com/portal/en/kb/crm/zoho-webinar)** — 21 images
- `https://www.zohowebstatic.com/sites/default/files/crm/initial-steps.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/reminder-webinar.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/push-participants.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/member-status-dropdown.jpg`
[View all 21 images in article →](https://help.zoho.com/portal/en/kb/crm/zoho-webinar)

