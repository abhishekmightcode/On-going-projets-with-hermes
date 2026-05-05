# Campaigns & Marketing Automation

> **Feature ID:** `06-Campaigns-Marketing`  
> **Knowledge Base Articles:** 186  
> **Last Updated:** 2026-05-05

## Overview

Marketing campaigns, autoresponders, lead nurturing, and campaign tracking

---

## 1. Core Functionality

### 1. FAQs: Zoho CRM for Google Ads

Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration. However, this does not erase the details fetched from the previous accounts. Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts. Can I configure more than one client account with Zoho CRM? Yes. If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would w
### 2. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made o
### 3. Zoho CRM for Google Ads

Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites. By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI). Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to ma
### 4. SurveyMonkey

SurveyMonkey is a survey platform where you can create simple to complex surveys and analyze those valuable responses. This extension helps you bring those surveys and survey responses in your Zoho CRM account and associates them with the CRM contacts. The surveys are added as campaigns and the contacts can be synchronized one-way from SurveyMonkey to Zoho CRM, or two-ways. Additionally, you can send survey to your contacts from Zoho CRM. Note: Please note that the SurveyMonkey extension for Zoho CRM is available in US, EU, CN, IN, AU, CA, and JP data centers. Install SurveyMonkey Installing t
### 5. Introducing Actions in Zoho CRM

Create actions to automate your sales and marketing activities. Help guide Configuring Automatic Actions ​
### 6. What is ABM?

Challenge With the current era of digital marketing, the need to surpass the older forms of marketing is both necessary and a demanding prospect. Understanding this urgency to come up with new strategies of business marketing, expanding companies across the globe had to come up with an answer to this quest for new marketing strategy. Some of the major difficulties that they faced with traditional marketing were: Lack of Personalization : Traditional marketing often involves a one-size-fits-all approach, leading to poor engagement with high-value accounts because their unique needs and pain poi
### 7. Data Privacy

A record's details are available in two sections - Info and Timeline. When you switch on GDPR Compliance in your Zoho CRM account, you will be able to view another section, namely Data Privacy . This section has the following details: Data Source Personal Fields Data Processing Bases View Data Source Data Subject information can be pushed into Zoho CRM from multiple sources such as the web-forms, by importing, APIs and third-party integrations. Data Source displays the information about how the record was Created and when it was Last Updated . Along with these information, additional details w
### 8. Setting Email Notifications

Email Notifications are among the instant and scheduled actions associated with different automations in CRM. They are alerts, notifications, information, or details sent to leads, contacts and users within the organization. When you associate an email notification to an automation, the selected email is automatically sent to the chosen recipients when the configuration criteria is met. Availability Permission Required Users with either Manage Automation or Modules Customization permissions can access this feature.. To set up an email notification Go to Setup[ ] > Automation > Actions > Email


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `CAMPAIGNS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `FAQs: Zoho CRM for Google Ads`
- `Schedule annual notifications for subscription renewals`
- `Zoho CRM for Google Ads`
- `SurveyMonkey`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/campaigns` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Campaigns & Marketing Automation - Example Implementation
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

- [Leads-Management](../Leads-Management/README.md)
- [Webforms](../Webforms/README.md)
- [Workflow-Automation](../Workflow-Automation/README.md)
- [Email-Tools](../Email-Tools/README.md)
- [Analytics-Dashboards](../Analytics-Dashboards/README.md)

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


### Zoho CRM for Google Ads
**Purpose:** Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner we

**Key Points:**
Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites.
By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI).
Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to make strategic marketing decisions for your business.
If you use Google Ads to drive potential customers to your website and a customer relationship management system (CRM) to track offline sales made through phone calls, emails, or direct sales, it can be difficult for your business to determine how your online campaign investments lead to offline conversion data stored in Zoho CRM.
With Zoho CRM for Google Ads , you can now import your Google Ads marketing investments into Zoho CRM so you can see which keywords and campaigns are responsible for each offline sale.
Plus, you can also export Zoho CRM sales data into Google Ads so you can better optimize your bids and budgets to yield maximum revenue and profits


### SurveyMonkey
**Purpose:** SurveyMonkey is a survey platform where you can create simple to complex surveys and analyze those valuable responses. This extension helps you bring those surveys and survey responses in your Zoho CR

**Key Points:**
SurveyMonkey is a survey platform where you can create simple to complex surveys and analyze those valuable responses.
This extension helps you bring those surveys and survey responses in your Zoho CRM account and associates them with the CRM contacts.
The surveys are added as campaigns and the contacts can be synchronized one-way from SurveyMonkey to Zoho CRM, or two-ways.
Additionally, you can send survey to your contacts from Zoho CRM.
Note: Please note that the SurveyMonkey extension for Zoho CRM is available in US, EU, CN, IN, AU, CA, and JP data centers.
Install SurveyMonkey Installing the extension and authenticating it with your SurveyMonkey login credentials is the first step


### Introducing Actions in Zoho CRM
**Purpose:** Create actions to automate your sales and marketing activities. Help guide Configuring Automatic Actions ​

**Key Points:**
Create actions to automate your sales and marketing activities.
Help guide Configuring Automatic Actions ​


### What is ABM?
**Purpose:** Challenge With the current era of digital marketing, the need to surpass the older forms of marketing is both necessary and a demanding prospect. Understanding this urgency to come up with new strateg

**Key Points:**
Challenge With the current era of digital marketing, the need to surpass the older forms of marketing is both necessary and a demanding prospect.
Understanding this urgency to come up with new strategies of business marketing, expanding companies across the globe had to come up with an answer to this quest for new marketing strategy.
Some of the major difficulties that they faced with traditional marketing were: Lack of Personalization : Traditional marketing often involves a one-size-fits-all approach, leading to poor engagement with high-value accounts because their unique needs and pain points aren't addressed.
Inefficient Resource Allocation : Without a clear focus on target accounts, resources are often spread thin across a broad audience, resulting in wasted time and budget.
Misaligned Sales and Marketing : Discrepancies between sales and marketing teams can lead to conflicting strategies and a failure to prioritize high-value accounts effectively.
Difficulty in Measuring ROI : Traditional marketing metrics may not accurately reflect the impact on key accounts, making it challenging to demonstrate the value of marketing efforts


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
- [Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/google-ads-crm-integration)
- [SurveyMonkey](https://help.zoho.com/portal/en/kb/crm/articles/surveymonkey-crm-integration)
- [Introducing Actions in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/actions-an-introduction)
- [What is ABM?](https://help.zoho.com/portal/en/kb/crm/articles/what-is-abm)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/articles/set-email-notifications)
- [Address Locator for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/address-locator-for-zoho-crm)
- [Survey Comparison](https://help.zoho.com/portal/en/kb/crm/articles/survey-comparison)
- [Zoho Survey Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-survey-crm-integration)
- [FAQs: Review Process](https://help.zoho.com/portal/en/kb/crm/articles/faqs-review-process)
- [Setting Field Updates](https://help.zoho.com/portal/en/kb/crm/articles/field-updates)
- [FAQs: Zoho CRM for Google Apps](https://help.zoho.com/portal/en/kb/crm/articles/faqs-zoho-crm-for-google-apps)
- [Common COQL Errors](https://help.zoho.com/portal/en/kb/crm/articles/troubleshoot-coql)
- [Integrating Zoho Campaigns with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/zoho-campaigns-crm-integration)
- [Booking appointments for services](https://help.zoho.com/portal/en/kb/crm/articles/booking-appointments-for-services)
- [FAQs: Record Management](https://help.zoho.com/portal/en/kb/crm/articles/faqs-record-management)
- [Facebook Adverts Manager](https://help.zoho.com/portal/en/kb/crm/articles/facebook-advert-manager-crm-integration)
- [An overview of user management in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/an-overview-of-user-management-in-zoho-crm)
- [FAQs: Data Enrichment](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-enrichment)
- [Using and Creating Macros](https://help.zoho.com/portal/en/kb/crm/articles/using-macros)
- [Automation in Team Module](https://help.zoho.com/portal/en/kb/crm/articles/automation-in-team-modules)
- [Setting up Advanced CRM Analytics](https://help.zoho.com/portal/en/kb/crm/articles/zoho-analytics-crm-integrations)
- [Segmentation Analysis](https://help.zoho.com/portal/en/kb/crm/articles/segmentation-analysis)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **5 KB articles** with **55 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Integrating Zoho Campaigns with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/zoho-campaigns-crm-integration) | 19 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-campaigns-crm-integration) |
| 2 | [Campaign Monitor for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/campaign-monitor-for-zoho-crm) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/campaign-monitor-for-zoho-crm) |
| 3 | [Creating Campaigns](https://help.zoho.com/portal/en/kb/crm/create-campaigns) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-campaigns) |
| 4 | [Troubleshooting Zoho Campaigns integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/troubleshooting-campaigns-integration-for-zoho-crm) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-campaigns-integration-for-zoho-crm) |
| 5 | [Marketing Attribution](https://help.zoho.com/portal/en/kb/crm/marketing-attribution) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/marketing-attribution) |

### Sample Image URLs (from top articles)
**[Integrating Zoho Campaigns with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/zoho-campaigns-crm-integration)** — 19 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ad6d2d074c2e99997fa8577efcc34ac3247f04ce8baf7328dd29e75e665cd2ad7b6a539b3849b69ddf82eb05b62bd5b3?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57433db69d51b0a994a60708dbae88194bf3747441d530e673ae4f88cce17cc36120a823e8be92a18b839cb74a67dd082a?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b578729291a3608153906ad5c8221ed6f61e4be76bc4e6dc7931ce7a5a530b11a1c6ee5ec5186f7f03c1df4df5eeeafaa66?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57715811b48b2ff026afd4a9fae734f28c8a18c75a924d8443851b45a99859703bdcaf7cea8d8799fabb19a7a87e2bc509?inline=true`
[View all 19 images in article →](https://help.zoho.com/portal/en/kb/crm/zoho-campaigns-crm-integration)

**[Campaign Monitor for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/campaign-monitor-for-zoho-crm)** — 10 images
- `https://static.zohocdn.com/zoho-desk-editor/static/images/file.png`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573fd0cd6a96167c8989000a62adbd5faf816e75bdac341f9d020a7a17b13332881811d758886456ec462fdbb0a4ddb9be?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573dba07262723ed09d64da2b0688d09438291f20f9342053261d2134db48b91ebe3b0a26eeebf89f822e6341b81c80459?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574e3d47225138c5fcbe0f15c1a60a105438bc291ac03ab57b31ce05b59835b67b3465187b079e4981d426b1ecdb7b56e2?inline=true`
[View all 10 images in article →](https://help.zoho.com/portal/en/kb/crm/campaign-monitor-for-zoho-crm)

**[Creating Campaigns](https://help.zoho.com/portal/en/kb/crm/create-campaigns)** — 10 images
- `https://www.zohowebstatic.com/sites/default/files/crm/campaign-lead-filter.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/filter-lead-2.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/new-lead2.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/quick-create-lead-campaign.jpg`
[View all 10 images in article →](https://help.zoho.com/portal/en/kb/crm/create-campaigns)

**[Troubleshooting Zoho Campaigns integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/troubleshooting-campaigns-integration-for-zoho-crm)** — 8 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575eacc90bc8f6acf488cb1aff3d2aa1961aca453b8218ce57176691cce13e06223032693dc77b661b4ff99bdd0c84b011?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5756def0e96d451fe408a92cf52990f9c77a7f669f50021c634d9fe8a19703d65418b050c264dcbbeb0d1452d652f3e4a0?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b572df8f7d12fbad77eaab308f9b740a2f86f8a05d3f158f182e31b11f82ec03320a476f6b77b2e92b494ec5dcbac560dbe?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5766a4b9dd9f05f36d4c1cb1b4a60baec0e7eff0a34c7bfda249d631815f0e360176be742401f5e7b6ed03615d62678366?inline=true`
[View all 8 images in article →](https://help.zoho.com/portal/en/kb/crm/troubleshooting-campaigns-integration-for-zoho-crm)

**[Marketing Attribution](https://help.zoho.com/portal/en/kb/crm/marketing-attribution)** — 8 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575a6fb3c4c59309f45418ad43fbae8237b6b07a31adc3447ccdb1dc75cfcb0f7594d9314275894b0b0cf0514212718842?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d19f5fd83dd072a3db22900013113d9ff2a54463062ff35a3fd5fa70a1e76d50351265824fea2a7ca11b64671d1b7894?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57bc468e5aed61b6686e92de2411141e1563487eced486b49db460c519635eaf520c44cece3de5c319b08e8056caa52963?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d5074225f555b7b7615b7f7bcb9f02bf9730e983239f3739decb4992b1f64a847decca3cb0240db93d22396348d9f371?inline=true`
[View all 8 images in article →](https://help.zoho.com/portal/en/kb/crm/marketing-attribution)

