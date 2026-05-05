# Zia AI & Intelligence

> **Feature ID:** `13-Zia-AI`  
> **Knowledge Base Articles:** 943  
> **Last Updated:** 2026-05-05

## Overview

Zoho AI features: predictions, recommendations, writing assistant, email intent, sentiment analysis

---

## 1. Core Functionality

### 1. Spotfone

Spotfone is a cloud telephony platform integrated with Zoho PhoneBridge to provide better communication to your customers. Perform all call-related activities right inside your CRM account. Setup integration To set up this integration, Go to Setup > Channels > Telephony. Choose Spotfone from the PhoneBridge Marketplace . Click Integrate . Click Get it now . For configuration steps, click here . Using Spotfone integration Spotfone for Zoho PhoneBridge help you perform all your call related activities directly within your CRM account. Once the set up is done, you can do the following: When you r
### 2. FAQs: Zoho CRM for Google Ads

Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration. However, this does not erase the details fetched from the previous accounts. Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts. Can I configure more than one client account with Zoho CRM? Yes. If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would w
### 3. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made o
### 4. Zia Usage Data Mapping of Events

This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction. Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing. It enables seamless import of usage data from various sources into Zoho CRM, providing accurate insights on customer engagement, retention, and personalized
### 5. Zoho CRM for Google Ads

Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites. By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI). Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to ma
### 6. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 7. Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics

1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketplace requires an administrator to initiate the process. The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM. There may be some backend issues that prevent you from integrating advanced analytics into your CRM. In such cases, please feel free to contact the support team, support@zohocrm.com 2. Why am I unabl
### 8. Voice based forecast analysis

As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams. The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exactly know why your deals are falling out of the pipeline. Or you may not know what is it that you are


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `ZIA`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Spotfone`
- `FAQs: Zoho CRM for Google Ads`
- `Schedule annual notifications for subscription renewals`
- `Zia Usage Data Mapping of Events`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/zia` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Zia AI & Intelligence - Example Implementation
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
- [Forecasts](../Forecasts/README.md)
- [Assignment-Rules](../Assignment-Rules/README.md)

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


### Schedule annual notifications for subscription renewals
**Purpose:** Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.

**Key Points:**
Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.
Every month, they publish new editions of the magazines.
The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team.
The sales agents send reminder emails to the existing customers for annual subscription renewal.
If the subscription is renewed, they are sent the magazines every month.
To be sure that the renewal payment is made on time, they require a process to automatically start sending reminder emails 15 days before the renewal date, and upgrade the subscription status based on the payment


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


### Consent Management
**Purpose:** Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set con

**Key Points:**
Zoho CRM's consent management settings help you get consent from your prospects and customers.
We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details.
Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules.
It cannot be applied for team modules.
Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be.
You will begin by marking the records whose data needs to be processed after obtaining consent


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
- [Schedule annual notifications for subscription renewals](https://help.zoho.com/portal/en/kb/crm/articles/automatic-schedule-notifications)
- [Zia Usage Data Mapping of Events](https://help.zoho.com/portal/en/kb/crm/articles/usage-data-event-mapping)
- [Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/google-ads-crm-integration)
- [Consent Management](https://help.zoho.com/portal/en/kb/crm/articles/consent-management)
- [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics)
- [Voice based forecast analysis](https://help.zoho.com/portal/en/kb/crm/articles/voice-based-forecast-analysis)
- [Importing Contacts from G Suite](https://help.zoho.com/portal/en/kb/crm/articles/import-contacts-g-suite)
- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [Zia for Workflow Rules](https://help.zoho.com/portal/en/kb/crm/articles/zia-intelligence-automation)
- [FAQs: Calls Module](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-calls-module)
- [Create category columns in reports](https://help.zoho.com/portal/en/kb/crm/articles/create-category-columns-in-reports)
- [Managing Process](https://help.zoho.com/portal/en/kb/crm/articles/managing-process-in-zoho-crm-android-app)
- [Setting up an Unsubscribe Link](https://help.zoho.com/portal/en/kb/crm/articles/set-unsubscribe-link)
- [Kaizen posts 2023: SDK series](https://help.zoho.com/portal/en/kb/crm/articles/sdk-2023)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Setting up Zoho Writer Add-on](https://help.zoho.com/portal/en/kb/crm/articles/zoho-writer-crm-integration)
- [SurveyMonkey](https://help.zoho.com/portal/en/kb/crm/articles/surveymonkey-crm-integration)
- [Kaizen posts 2024: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2024)
- [FAQs: Developer Hub](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-developer-hub)
- [Managing Web Tabs](https://help.zoho.com/portal/en/kb/crm/articles/web-tabs)
- [Charts](https://help.zoho.com/portal/en/kb/crm/articles/create-charts)
- [Capabilities of Zia in Zoho CRM— A perspective](https://help.zoho.com/portal/en/kb/crm/articles/zia-overview)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **87 KB articles** with **991 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Customizing mobile record detail page using Canvas](https://help.zoho.com/portal/en/kb/crm/customizing-mobile-record-detail-page-using-canvas) | 52 | [View Article](https://help.zoho.com/portal/en/kb/crm/customizing-mobile-record-detail-page-using-canvas) |
| 2 | [Customizing Record Detail Page Using Canvas](https://help.zoho.com/portal/en/kb/crm/customize-record-detail-page-canvas) | 46 | [View Article](https://help.zoho.com/portal/en/kb/crm/customize-record-detail-page-canvas) |
| 3 | [Zia Vision — Intelligent Image Validation](https://help.zoho.com/portal/en/kb/crm/zia-vision) | 45 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-vision) |
| 4 | [Predict customer churn using Zia](https://help.zoho.com/portal/en/kb/crm/predict-customer-churn-using-zia) | 35 | [View Article](https://help.zoho.com/portal/en/kb/crm/predict-customer-churn-using-zia) |
| 5 | [Zoho SalesInbox: Your Sales-Focused Email Client](https://help.zoho.com/portal/en/kb/crm/zoho-salesinbox-your-sales-focused-email-client) | 35 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-salesinbox-your-sales-focused-email-client) |
| 6 | [Zia Strategy Influencer](https://help.zoho.com/portal/en/kb/crm/zia-strategy-influencer) | 33 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-strategy-influencer) |
| 7 | [Response based sentiment analysis](https://help.zoho.com/portal/en/kb/crm/response-based-sentiment-analysis) | 25 | [View Article](https://help.zoho.com/portal/en/kb/crm/response-based-sentiment-analysis) |
| 8 | [Managing Emails](https://help.zoho.com/portal/en/kb/crm/managing-emails-26-4-2026) | 25 | [View Article](https://help.zoho.com/portal/en/kb/crm/managing-emails-26-4-2026) |
| 9 | [Email Insights: An Overview](https://help.zoho.com/portal/en/kb/crm/email-insights-overview) | 24 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-insights-overview) |
| 10 | [Email Parser](https://help.zoho.com/portal/en/kb/crm/email-parser) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-parser) |
| 11 | [Understanding Email Template Builder](https://help.zoho.com/portal/en/kb/crm/template-builder) | 21 | [View Article](https://help.zoho.com/portal/en/kb/crm/template-builder) |
| 12 | [Email Parser 2.0 — What's New and What has Changed](https://help.zoho.com/portal/en/kb/crm/nextegn-email-parser-what-s-new-and-what-has-changed) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/nextegn-email-parser-what-s-new-and-what-has-changed) |
| 13 | [Email Parser (Old) — Data Extraction from Emails](https://help.zoho.com/portal/en/kb/crm/email-parser-old) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-parser-old) |
| 14 | [Configuring Email Compose Setting](https://help.zoho.com/portal/en/kb/crm/configuring-email-compose-setting) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/configuring-email-compose-setting) |
| 15 | [Managing Mail Merge Templates](https://help.zoho.com/portal/en/kb/crm/mail-merge-templates) | 19 | [View Article](https://help.zoho.com/portal/en/kb/crm/mail-merge-templates) |
| 16 | [Compose, Organize and Configure Emails](https://help.zoho.com/portal/en/kb/crm/compose-organize-and-configure-emails) | 19 | [View Article](https://help.zoho.com/portal/en/kb/crm/compose-organize-and-configure-emails) |
| 17 | [Customizing Record's Detail Page](https://help.zoho.com/portal/en/kb/crm/page-level-customization) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/page-level-customization) |
| 18 | [Zoho CRM for Gmail & Inbox](https://help.zoho.com/portal/en/kb/crm/gmail-inbox-crm-integration) | 17 | [View Article](https://help.zoho.com/portal/en/kb/crm/gmail-inbox-crm-integration) |
| 19 | [Email Configuration for IMAP and POP3](https://help.zoho.com/portal/en/kb/crm/email-configuration-for-imap-and-pop3) | 17 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-configuration-for-imap-and-pop3) |
| 20 | [Email Configuration IMAP](https://help.zoho.com/portal/en/kb/crm/email-configuration-imap) | 17 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-configuration-imap) |
| 21 | [Zoho Mail Add-on](https://help.zoho.com/portal/en/kb/crm/configure-pop-account) | 16 | [View Article](https://help.zoho.com/portal/en/kb/crm/configure-pop-account) |
| 22 | [Zia Email Intent](https://help.zoho.com/portal/en/kb/crm/zia-email-intent) | 15 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-email-intent) |
| 23 | [Custom domain mapping for rebranding your CRM](https://help.zoho.com/portal/en/kb/crm/custom-domain-mapping-in-zoho-crm) | 15 | [View Article](https://help.zoho.com/portal/en/kb/crm/custom-domain-mapping-in-zoho-crm) |
| 24 | [Understanding the new record details view in iOS app](https://help.zoho.com/portal/en/kb/crm/understanding-the-new-record-details-view-in-ios-app) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/understanding-the-new-record-details-view-in-ios-app) |
| 25 | [Creating Email Templates](https://help.zoho.com/portal/en/kb/crm/email-templates) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-templates) |
| 26 | [Email Storage as separate entity](https://help.zoho.com/portal/en/kb/crm/email-storage-as-separate-entity) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-storage-as-separate-entity) |
| 27 | [Zia Scores](https://help.zoho.com/portal/en/kb/crm/scoring-rules-zia-scores) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/scoring-rules-zia-scores) |
| 28 | [CommandCenter 1.0 to 2.0: A detailed migration guide](https://help.zoho.com/portal/en/kb/crm/commandcenter-1-0-to-2-0-a-detailed-migration-guide-26-4-2026) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/commandcenter-1-0-to-2-0-a-detailed-migration-guide-26-4-2026) |
| 29 | [Sentiment based profile analysis](https://help.zoho.com/portal/en/kb/crm/sentiment-based-profile-analysis) | 13 | [View Article](https://help.zoho.com/portal/en/kb/crm/sentiment-based-profile-analysis) |
| 30 | [Setting up Email Sharing Permissions](https://help.zoho.com/portal/en/kb/crm/setting-up-email-sharing-permissions) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/setting-up-email-sharing-permissions) |
| 31 | [Zia for Emails — Overview and Key Capabilities](https://help.zoho.com/portal/en/kb/crm/zia-for-emails) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-for-emails) |
| 32 | [Zia Notifications](https://help.zoho.com/portal/en/kb/crm/zia-notifications) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-notifications) |
| 33 | [Zia Presentation](https://help.zoho.com/portal/en/kb/crm/zia-presentation) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-presentation) |
| 34 | [MailChimp](https://help.zoho.com/portal/en/kb/crm/mailchimp-crm-integration) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/mailchimp-crm-integration) |
| 35 | [Zia Field Prediction](https://help.zoho.com/portal/en/kb/crm/zia-s-field-prediction) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-s-field-prediction) |
| 36 | [Zia Recommendation](https://help.zoho.com/portal/en/kb/crm/zia-recommendation) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-recommendation) |
| 37 | [FAQs: Working with Emails](https://help.zoho.com/portal/en/kb/crm/faq-working-with-emails) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/faq-working-with-emails) |
| 38 | [Email Authentication](https://help.zoho.com/portal/en/kb/crm/email-authentication) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-authentication) |
| 39 | [Email Communication: Send and receive mails](https://help.zoho.com/portal/en/kb/crm/email-communication-send-and-receive-mails) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-communication-send-and-receive-mails) |
| 40 | [FAQs: Mass Emails](https://help.zoho.com/portal/en/kb/crm/faqs-mass-emails) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-mass-emails) |
| 41 | [Ask Zia](https://help.zoho.com/portal/en/kb/crm/ask-zia) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/ask-zia) |
| 42 | [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/naijasmsportal-for-zoho-crm) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/naijasmsportal-for-zoho-crm) |
| 43 | [Organization Email Address](https://help.zoho.com/portal/en/kb/crm/organization-email) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/organization-email) |
| 44 | [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/set-email-notifications) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/set-email-notifications) |
| 45 | [Zia Similarity Recommender](https://help.zoho.com/portal/en/kb/crm/zia-similarity-recommender) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-similarity-recommender) |
| 46 | [Zia Record Summary](https://help.zoho.com/portal/en/kb/crm/zia-record-summary) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-record-summary) |
| 47 | [Intelligent character recognition by Zia Vision](https://help.zoho.com/portal/en/kb/crm/intelligent-character-recognition-by-zia-vision) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/intelligent-character-recognition-by-zia-vision) |
| 48 | [Frequently asked questions on Emails in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/frequently-asked-questions-emails-in-zoho-crm) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/frequently-asked-questions-emails-in-zoho-crm) |
| 49 | [Zia Call Intelligence](https://help.zoho.com/portal/en/kb/crm/zia-call-intelligence) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-call-intelligence) |
| 50 | [Timeline in Record Detail Page](https://help.zoho.com/portal/en/kb/crm/timeline-in-record-detail-page) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/timeline-in-record-detail-page) |
| 51 | [Setting up Email Relay](https://help.zoho.com/portal/en/kb/crm/crm-set-up-email-relay) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/crm-set-up-email-relay) |
| 52 | [Setting Email Preferences](https://help.zoho.com/portal/en/kb/crm/setting-email-preferences) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/setting-email-preferences) |
| 53 | [Zia Email Emotion Analysis](https://help.zoho.com/portal/en/kb/crm/zia-email-emotion-analysis) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-email-emotion-analysis) |
| 54 | [Custom AI Studio](https://help.zoho.com/portal/en/kb/crm/custom-ai-studio) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/custom-ai-studio) |
| 55 | [Ask or Chat with Zia](https://help.zoho.com/portal/en/kb/crm/ask-or-chat-with-zia) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/ask-or-chat-with-zia) |
| 56 | [Email Sentiment Analysis](https://help.zoho.com/portal/en/kb/crm/configure-email-sentiment) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/configure-email-sentiment) |
| 57 | [Zia Reminders](https://help.zoho.com/portal/en/kb/crm/using-zia-reminder) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/using-zia-reminder) |
| 58 | [Email Credibility in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/email-credibility-in-zoho-crm) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-credibility-in-zoho-crm) |
| 59 | [Email Views and Email Sentiment](https://help.zoho.com/portal/en/kb/crm/email-views-and-sentiment-salesinbox) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-views-and-sentiment-salesinbox) |
| 60 | [FAQs: Email Configuration](https://help.zoho.com/portal/en/kb/crm/faqs-email-configuration) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-email-configuration) |
| 61 | [Microsoft Sentiment Analysis for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/sentiment-analysis-for-zoho-crm) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/sentiment-analysis-for-zoho-crm) |
| 62 | [Email configuration for Microsoft Graph API](https://help.zoho.com/portal/en/kb/crm/email-configuration-for-microsoft-graph-api) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/email-configuration-for-microsoft-graph-api) |
| 63 | [Zia - Next Best Experience](https://help.zoho.com/portal/en/kb/crm/zia-next-best-experience-new) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-next-best-experience-new) |
| 64 | [Zia Competitor Alert](https://help.zoho.com/portal/en/kb/crm/zia-competitor-alert) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-competitor-alert) |
| 65 | [Sending Mass Emails](https://help.zoho.com/portal/en/kb/crm/sending-mass-emails) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/sending-mass-emails) |
| 66 | [MailMagnet: Centralized  Incoming Email Notification Panel](https://help.zoho.com/portal/en/kb/crm/mailmagnet-centralized-incoming-email-notification-panel) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/mailmagnet-centralized-incoming-email-notification-panel) |
| 67 | [Email bounce management](https://help.zoho.com/portal/en/kb/crm/dealing-with-bounce-warnings) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/dealing-with-bounce-warnings) |
| 68 | [Setting up organization details](https://help.zoho.com/portal/en/kb/crm/set-up-org-details) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/set-up-org-details) |
| 69 | [User details  in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/user-details-in-zoho-crm-ios-app) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/user-details-in-zoho-crm-ios-app) |
| 70 | [Your Guide to Zoho CRM Email Tools](https://help.zoho.com/portal/en/kb/crm/your-guide-to-zoho-crm-email-tools) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/your-guide-to-zoho-crm-email-tools) |
| 71 | [Zia's Smart Prompt - Frequently Asked Questions](https://help.zoho.com/portal/en/kb/crm/zia-s-smart-prompt-frequently-asked-questions-26-4-2026) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-s-smart-prompt-frequently-asked-questions-26-4-2026) |
| 72 | [FAQs: Email Templates](https://help.zoho.com/portal/en/kb/crm/faqs-email-templates) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-email-templates) |
| 73 | [Aircall](https://help.zoho.com/portal/en/kb/crm/integrate-with-aircall) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/integrate-with-aircall) |
| 74 | [Configure Zoho CRM for Gmail Add-on](https://help.zoho.com/portal/en/kb/crm/configure-zoho-crm-for-gmail-add-on) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/configure-zoho-crm-for-gmail-add-on) |
| 75 | [User details in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/user-details-in-zoho-crm-android-app) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/user-details-in-zoho-crm-android-app) |
| 76 | [POP/POP3 Emails Tab](https://help.zoho.com/portal/en/kb/crm/pop-pop3-emails-tab) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/pop-pop3-emails-tab) |
| 77 | [BIMI for email authentication](https://help.zoho.com/portal/en/kb/crm/bimi-for-email-authentication) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/bimi-for-email-authentication) |
| 78 | [Zoho CRM Uptime SLA and Availability  ](https://help.zoho.com/portal/en/kb/crm/zoho-crm-uptime-sla-and-availability) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-crm-uptime-sla-and-availability) |
| 79 | [Why doesn't Zia analyze my data?](https://help.zoho.com/portal/en/kb/crm/why-doesn-t-zia-analyze-my-data-2-4-2026) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/why-doesn-t-zia-analyze-my-data-2-4-2026) |
| 80 | [Troubleshooting Email Templates](https://help.zoho.com/portal/en/kb/crm/troubleshooting-email-templates) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-email-templates) |
| 81 | [Troubleshooting Email Relay](https://help.zoho.com/portal/en/kb/crm/troubleshooting-email-relay) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-email-relay) |
| 82 | [Troubleshooting Email Deliverability](https://help.zoho.com/portal/en/kb/crm/troubleshooting-email-deliverability) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-email-deliverability) |
| 83 | [Emails Deliverability  in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/emails-deliverability-in-zoho-crm) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/emails-deliverability-in-zoho-crm) |
| 84 | [Zia Writing Assistant](https://help.zoho.com/portal/en/kb/crm/zia-writing-assistant) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-writing-assistant) |
| 85 | [Google, Yahoo, and Outlook's Guidelines for Email Security and Delivery](https://help.zoho.com/portal/en/kb/crm/google-yahoo-and-outlook-s-guidelines-for-email-security-and-delivery) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/google-yahoo-and-outlook-s-guidelines-for-email-security-and-delivery) |
| 86 | [Capabilities of Zia in Zoho CRM— A perspective](https://help.zoho.com/portal/en/kb/crm/zia-overview) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-overview) |
| 87 | [Zia note summary](https://help.zoho.com/portal/en/kb/crm/zia-note-summary) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-note-summary) |

### Sample Image URLs (from top articles)
**[Customizing mobile record detail page using Canvas](https://help.zoho.com/portal/en/kb/crm/customizing-mobile-record-detail-page-using-canvas)** — 52 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5723bae0b8a7d1f82a2970bf3e805617cf430623033924a4638692fb710ba35f4b7f3f792469b5545751162c5f33dfb0c1?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5718bb3efbe9f64f98bbfb50be8024e78a4e2cc2721119a8b4ecdaf9a3eb9a743c273b24d7bf9c7c4758c7f83988a5a5db?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e4347fd49cb7da7e2437d31b25efc4012e30fb476ef414e382e0b14f418f59dd8f61369105f37a1b4da965e872e6f457?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsnf023790b3f3a1a85df658c849ae3e26ded311af686af83584b7452b17a9b189ab24829d892dfe15f7fa4fd6b71b80269842aee18e2820b55fbf18cd18a46b0a6?inline=true`
[View all 52 images in article →](https://help.zoho.com/portal/en/kb/crm/customizing-mobile-record-detail-page-using-canvas)

**[Customizing Record Detail Page Using Canvas](https://help.zoho.com/portal/en/kb/crm/customize-record-detail-page-canvas)** — 46 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571f78761c7554acaf69e7f032c438e395e3b0fa74f78116a16dbe74442bad0282cc2850f0b196c0fd0e5e4ae67fae0899?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d1679cc027a6225f52af6a70fd2a81bb77f78ec6b0362a71fc4d7de660c7e96601f4b65218938363a691315ce46bfc5f?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57cb648deab6e348f2413261c702027c9852898ece6d31443b36c7944163cf2cfa49c636fac6a2faa62dccb2cffa867b78?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5765a6c2d732ece3cd071ca0dc3cc943504ba377ef20dbabed8a6bd300be1c9d6ab1c8312dbf09a7a03c46550891ee2195?inline=true`
[View all 46 images in article →](https://help.zoho.com/portal/en/kb/crm/customize-record-detail-page-canvas)

**[Zia Vision — Intelligent Image Validation](https://help.zoho.com/portal/en/kb/crm/zia-vision)** — 45 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b7a157a9cf7cf4db019242d3ffd02171f99e7bb6b43a66dcd5881636bace36c809b5fd818d2a0b0fc134c85bb76a2cea?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57289c4a165dc8b527baf7c6c5dc6694358056f1ad2b78756769a8f5a29281e7e65dd6aff460efb542cf972734271c111b?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5757a2cffce433bedcba8f6253144099614e17c39761a7a72c0b9ed3c4c16f14e40b34a4e892567977a366e29c047267b9?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57a0d430dbac2339b3e3b55952ad8822a186ba212d300ae5723e66bbb6ec81ddc07c861ed03af236483d8c1fd46137e60f?inline=true`
[View all 45 images in article →](https://help.zoho.com/portal/en/kb/crm/zia-vision)

**[Predict customer churn using Zia](https://help.zoho.com/portal/en/kb/crm/predict-customer-churn-using-zia)** — 35 images
- `https://img.zohostatic.com/zde/static/images/quote.png`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57877b940f4b805424b31e6694839b5c1cf05e5f40326c9875e3c9a3fe3cfd58b0adc124ab1b3320143bee14650e7841ce?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e53dcbe31a397441eca0a9101bd9ebb6416c2595b8b77eab1a38c42546e90024934dafd1243c7ef628941b61402e1ef7?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b79eede1a95ab40f0e0378b66734e6ff3b37fa89fb582f302f8af9001140fbe2220607ca7e95dc9ce04758371474babd?inline=true`
[View all 35 images in article →](https://help.zoho.com/portal/en/kb/crm/predict-customer-churn-using-zia)

**[Zoho SalesInbox: Your Sales-Focused Email Client](https://help.zoho.com/portal/en/kb/crm/zoho-salesinbox-your-sales-focused-email-client)** — 35 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573aa854e7a1df0129f805db8d295c51e755cd7aa9a76f7ce8e04b3008eccc227ed958312ef76a2f952a7fb0fb75f4b692?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57be18d97572e90c8f8d73c7adec5d1e5d1bdcd486980757d6c34b05b70d7c0c38eede0470c7fb9902d9d4d1bd83d21ff8?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5758016b65d1a4e26b2a06a46930e5436ee4b96d940ecea68eb99cbc551442bdf370d6c448c8c8561ae4cd87c75c423cec?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b01e51bae84e31fd155614e80740fbf03a81c681dd882d15184a0aa719100663fd33bad51cfeba3a2f28b758d2288004?inline=true`
[View all 35 images in article →](https://help.zoho.com/portal/en/kb/crm/zoho-salesinbox-your-sales-focused-email-client)

