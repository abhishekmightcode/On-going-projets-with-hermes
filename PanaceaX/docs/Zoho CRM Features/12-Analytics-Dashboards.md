# Analytics, Reports & Dashboards

> **Feature ID:** `12-Analytics-Dashboards`  
> **Knowledge Base Articles:** 139  
> **Last Updated:** 2026-05-05

## Overview

Reports, charts, dashboards, data analytics, VoC, and BI-style analytics

---

## 1. Core Functionality

### 1. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made on time, they require a process to automatically start sending reminder emails 15 days before the renewal date, and upgrade the subscription status based on the payment. The following process chart exp
### 2. Zia Usage Data Mapping of Events

This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction. Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing. It enables seamless import of usage data from various sources into Zoho CRM, providing accurate insights on customer engagement, retention, and personalized service delivery. What is Usage Data? All businesses need transactional data as a base to study user purchase behavior on metrics like customer details, date and time, payment methods, discounts, and 
### 3. Zoho CRM for Google Ads

Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites. By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI). Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to make strategic marketing decisions for your business. If you use Google Ads to drive potential customers to your website and a customer relationship management system (CRM) to track offline sales made t
### 4. Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics

1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketplace requires an administrator to initiate the process. The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM. There may be some backend issues that prevent you from integrating advanced analytics into your CRM. In such cases, please feel free to contact the support team, support@zohocrm.com 2. Why am I unable to deactivate the Zoho Advanced Analytics integration with CRM? Only users with admin-level permissions or users with the admin profile are allowed to integrate or deactivate integrations. Please ch
### 5. Voice based forecast analysis

As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams. The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exactly know why your deals are falling out of the pipeline. Or you may not know what is it that you are doing well, that is giving you winning deals, for that matter. Knowledge of this winning/losing pattern will help you set better goals and also meet them better. This is where VoC enters the picture.
### 6. Create category columns in reports

What are category columns? Category columns allow you to organize large data sets into categories. When viewing reports with a wide range of data, it can be challenging to get an overview of the entire dataset. This feature helps you to create user-defined categories to group data into easily digestible information. This enables you to draw context from the vast report values. In Zoho CRM, you can create two types of category columns: Number category columns - To group numerical data into columns Picklist category columns - To group picklist data into columns Let's understand this better with the following scenario: A delivery manager plans the schedule for parcel deliveries, considering factors such as the size and weight of the parcels. Knowing the weight and size helps them choose the r
### 7. Managing Web Tabs

Web tabs help you to open web pages like company-wide announcements, web applications, etc. inside Zoho CRM. All the Zoho CRM users across the organization can view these web tabs. You can also create your own applications using Zoho Creator and access them inside Zoho CRM. By default, the web tabs functionality is available only to the users with Administrator privilege. However, you can also activate this functionality for other users. Availability Permission Required Users with the Modules Customization permission can access this feature. Create web tabs You can create a maximum of 25 tabs, each with a unique name. To create web tabs Go to Setup > Customization > Modules and Fields > Web Tabs . In the Web Tabs page, click + New Tab . Enter the name of the web tab in Tab Name box. Select
### 8. Charts

Some of the options mentioned in this document are being released in a phased manner and may only be available to specific users. The Dashboards tab is renamed as Analytics for selected accounts. A chart presents data from various records of a module(s) in a visual or graphical representation for an easy analysis. The data is seemingly comprehensible as users can easily pick out the patterns, trends, etc., which may otherwise be difficult to interpret. For example, you are the Sales Manager for Asia Pacific region and want to compare the number of leads created by the sales representatives in the previous year. You can easily achieve this by creating charts in your dashboard and compare the number of leads created by different sales reps. In Zoho CRM charts, you can: Create different types


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `ANALYTICS`

**Standard Fields (inherited):**
- `Created_By` (User) — Record creator
- `Modified_By` (User) — Last modifier
- `Created_Time` (DateTime) — Creation timestamp
- `Modified_Time` (DateTime) — Last modification
- `Owner` (User) — Record owner for access control

**Key Articles:**
- `Schedule annual notifications for subscription renewals`
- `Zia Usage Data Mapping of Events`
- `Zoho CRM for Google Ads`
- `Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/analytics` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Analytics, Reports & Dashboards - Example Implementation
// Triggered on record creation/update

if(input.module == "SCHEDULE ANNUAL NOTIFICATIONS FOR SUBSCRIPTION RENEWALS")
{
    // Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publisher
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

- [Forecasts](../Forecasts/README.md)
- [Zia-AI](../Zia-AI/README.md)
- [Deals-Pipeline](../Deals-Pipeline/README.md)
- [Campaigns-Marketing](../Campaigns-Marketing/README.md)

### This Feature Enables

- **Forecasts** — shares data model and workflows
- **Analytics** — generates reports based on this module's data
- **Automation** — triggers workflows based on record changes
- **Mobile** — fully accessible via Zoho CRM mobile apps

### Interaction Patterns

| Pattern | Description |
|---------|-------------|
| Parent-Child | Module can have sub-modules (subforms) |
| Lookup | References records from other modules |
| Related List | Shows associated records from other modules |
| Workflow Trigger | Changes in this module trigger automation |

---

## 4. Standalone Functions

### Schedule annual notifications for subscription renewals
**Purpose:** Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.

**Key Points:**
- Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.
- Every month, they publish new editions of the magazines.
- The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team.
- The sales agents send reminder emails to the existing customers for annual subscription renewal


### Zia Usage Data Mapping of Events
**Purpose:** This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is 

**Key Points:**
- This guide helps you with the mapping of events of your usage data under Zia.
- Before getting into greater detail, let's quickly revise the important terms.
- What is mapping of events? Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction.
- Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing.
- It enables seamless import of usage data from various sou


### Zoho CRM for Google Ads
**Purpose:** Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner we

**Key Points:**
- Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites.
- By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI).
- Google Ads' flexible online marketing platform inc


### Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics
**Purpose:** 1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketp

**Key Points:**
- Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM.
- The integration of apps from the marketplace requires an administrator to initiate the process.
- The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM.
- There may be some backend issues that prevent you from integrating advanced analytics into your CRM


### Voice based forecast analysis
**Purpose:** As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you ar

**Key Points:**
- As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc).
- By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams.
- The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exac


### Create category columns in reports
**Purpose:** What are category columns? Category columns allow you to organize large data sets into categories. When viewing reports with a wide range of data, it can be challenging to get an overview of the entir

**Key Points:**
- What are category columns? Category columns allow you to organize large data sets into categories.
- When viewing reports with a wide range of data, it can be challenging to get an overview of the entire dataset.
- This feature helps you to create user-defined categories to group data into easily digestible information.
- This enables you to draw context from the vast report values.
- In Zoho CRM, you can create two types of category columns: Number category columns - To group numerical data into column


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

**EdTech / Schools** — Student inquiry management, enrollment pipeline, course tracking
**Solar / Renewable Energy** — Site assessment pipeline, proposal workflow, project milestones
**Healthcare** — Patient inquiry, appointment scheduling, treatment plan tracking
**Real Estate** — Property inquiry to closing, viewing scheduling, document management
**BFSI** — Loan application processing, policy enrollment, compliance workflows
**Manufacturing** — Inquiry to order pipeline, production scheduling, quality checks
**Retail** — Order processing, customer onboarding, post-purchase engagement
**Hospitality** — Booking inquiry to confirmation, event planning, preference tracking

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
  └── Roles (Sales Rep, Manager, Admin)
        └── Profiles (Standard, Limited, Read-Only)
              └── Field-Level Permissions (Visible, Editable, Hidden)
                    └── Record-Level Access (Owner, Assigned, All)
```

### Scalability

- **Horizontal:** Multi-node deployment for high availability
- **Vertical:** Increased compute for batch processing
- **Sharding:** Data partitioned by organization (multi-tenant)
- **CDN:** Static assets served via edge network

---

## Article Sources

- [Schedule annual notifications for subscription renewals](https://help.zoho.com/portal/en/kb/crm/articles/automatic-schedule-notifications)
- [Zia Usage Data Mapping of Events](https://help.zoho.com/portal/en/kb/crm/articles/usage-data-event-mapping)
- [Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/google-ads-crm-integration)
- [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics)
- [Voice based forecast analysis](https://help.zoho.com/portal/en/kb/crm/articles/voice-based-forecast-analysis)
- [Create category columns in reports](https://help.zoho.com/portal/en/kb/crm/articles/create-category-columns-in-reports)
- [Managing Web Tabs](https://help.zoho.com/portal/en/kb/crm/articles/web-tabs)
- [Charts](https://help.zoho.com/portal/en/kb/crm/articles/create-charts)
- [Capabilities of Zia in Zoho CRM— A perspective](https://help.zoho.com/portal/en/kb/crm/articles/zia-overview)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [Decision Guide for Territory Management](https://help.zoho.com/portal/en/kb/crm/articles/territory-decision-management)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [Survey Comparison](https://help.zoho.com/portal/en/kb/crm/articles/survey-comparison)
- [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/articles/webform-analytics-2-7-2021)
- [Understanding and building reports](https://help.zoho.com/portal/en/kb/crm/articles/understanding-and-building-reports)
- [Call analytics](https://help.zoho.com/portal/en/kb/crm/articles/call-analytics)
- [Using Zoho Finance Suite Integration](https://help.zoho.com/portal/en/kb/crm/articles/use-zoho-finance-suite-crm-integration)
- [Acting on VoC insights](https://help.zoho.com/portal/en/kb/crm/articles/acting-on-voc-insights)
- [Cross sell analytics](https://help.zoho.com/portal/en/kb/crm/articles/cross-sell-analytic)
- [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/articles/webform-analytics)
- [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/working-with-analytics-in-zoho-crm-android-app)
- [Assess the outgoing call quality of the sales agents](https://help.zoho.com/portal/en/kb/crm/articles/assess-call-quality-review-performance)
- [Conduct root-cause analysis in VoC](https://help.zoho.com/portal/en/kb/crm/articles/conduct-root-cause-analysis-in-voc)
- [Response based sentiment analysis](https://help.zoho.com/portal/en/kb/crm/articles/response-based-sentiment-analysis)
- [Setting up Advanced CRM Analytics](https://help.zoho.com/portal/en/kb/crm/articles/zoho-analytics-crm-integrations)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
