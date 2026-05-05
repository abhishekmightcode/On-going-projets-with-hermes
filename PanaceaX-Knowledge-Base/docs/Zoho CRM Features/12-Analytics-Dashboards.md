# Analytics, Reports & Dashboards

> **Feature ID:** `12-Analytics-Dashboards`  
> **Knowledge Base Articles:** 199  
> **Last Updated:** 2026-05-05

## Overview

Reports, charts, dashboards, data analytics, VoC, and BI-style analytics

---

## 1. Core Functionality

### 1. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made o
### 2. Zia Usage Data Mapping of Events

This guide helps you with the mapping of events of your usage data under Zia. Before getting into greater detail, let's quickly revise the important terms. What is mapping of events? Event mapping is a technique for the system to learn usage data, using which the user can activate Predictions , such as churn prediction. Through mapping of events, the system will learn and understand how to interpret usage data for accurate Zia processing. It enables seamless import of usage data from various sources into Zoho CRM, providing accurate insights on customer engagement, retention, and personalized
### 3. Zoho CRM for Google Ads

Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites. By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI). Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to ma
### 4. Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics

1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketplace requires an administrator to initiate the process. The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM. There may be some backend issues that prevent you from integrating advanced analytics into your CRM. In such cases, please feel free to contact the support team, support@zohocrm.com 2. Why am I unabl
### 5. Voice based forecast analysis

As you may already be aware, Forecasts in Zoho CRM help you set and achieve sales targets for your teams by a specific period (by month, by quarter etc). By creating and working with forecasts, you are effectively able to use the knowledge of current sales progress to set and meet future sales goals for your teams. The challenge with the current forecast setup is that, while the system will actively help you monitor sales progress, in the cases of failure to meet the set target, you may not exactly know why your deals are falling out of the pipeline. Or you may not know what is it that you are
### 6. Create category columns in reports

What are category columns? Category columns allow you to organize large data sets into categories. When viewing reports with a wide range of data, it can be challenging to get an overview of the entire dataset. This feature helps you to create user-defined categories to group data into easily digestible information. This enables you to draw context from the vast report values. In Zoho CRM, you can create two types of category columns: Number category columns - To group numerical data into columns Picklist category columns - To group picklist data into columns Let's understand this better with
### 7. Kaizen posts 2024: Widget series

Here is a complete list of Kaizen posts related to Widgets published in 2024 . Sl. No. Title Description 1 How is a Widget used in a Blueprint? Learn how to create widgets and use them in your Zoho CRM account from this post. 2 Geocoding Leads' Addresses in ZOHO CRM Learn how to create a Related List Widget map in Zoho CRM's Lead detail page with lead location display, directions from the current user's location, and showcasing other leads in the same street or city as the current lead. 3 Zoho CRM Widgets using ReactJS Explore how to use ReactJS and other client-side frameworks for Zoho CRM wi
### 8. Managing Web Tabs

Web tabs help you to open web pages like company-wide announcements, web applications, etc. inside Zoho CRM. All the Zoho CRM users across the organization can view these web tabs. You can also create your own applications using Zoho Creator and access them inside Zoho CRM. By default, the web tabs functionality is available only to the users with Administrator privilege. However, you can also activate this functionality for other users. Availability Permission Required Users with the Modules Customization permission can access this feature. Create web tabs You can create a maximum of 25 tabs,


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `ANALYTICS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

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

- **Forecasts** -- shares data model and workflows
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


### Create category columns in reports
**Purpose:** What are category columns? Category columns allow you to organize large data sets into categories. When viewing reports with a wide range of data, it can be challenging to get an overview of the entir

**Key Points:**
Category columns allow you to organize large data sets into categories.
When viewing reports with a wide range of data, it can be challenging to get an overview of the entire dataset.
This feature helps you to create user-defined categories to group data into easily digestible information.
This enables you to draw context from the vast report values.
In Zoho CRM, you can create two types of category columns: Number category columns - To group numerical data into columns Picklist category columns - To group picklist data into columns Let's understand this better with the following scenario: A delivery manager plans the schedule for parcel deliveries, considering factors such as the size and weight of the parcels.
Knowing the weight and size helps them choose the right shipping option, especially for heavier items


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

- [Schedule annual notifications for subscription renewals](https://help.zoho.com/portal/en/kb/crm/articles/automatic-schedule-notifications)
- [Zia Usage Data Mapping of Events](https://help.zoho.com/portal/en/kb/crm/articles/usage-data-event-mapping)
- [Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/google-ads-crm-integration)
- [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics)
- [Voice based forecast analysis](https://help.zoho.com/portal/en/kb/crm/articles/voice-based-forecast-analysis)
- [Create category columns in reports](https://help.zoho.com/portal/en/kb/crm/articles/create-category-columns-in-reports)
- [Kaizen posts 2024: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2024)
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
- [FAQs: Zoho CRM for Google Apps](https://help.zoho.com/portal/en/kb/crm/articles/faqs-zoho-crm-for-google-apps)
- [Cross sell analytics](https://help.zoho.com/portal/en/kb/crm/articles/cross-sell-analytic)
- [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/articles/webform-analytics)
- [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/working-with-analytics-in-zoho-crm-android-app)
- [Assess the outgoing call quality of the sales agents](https://help.zoho.com/portal/en/kb/crm/articles/assess-call-quality-review-performance)
- [Conduct root-cause analysis in VoC](https://help.zoho.com/portal/en/kb/crm/articles/conduct-root-cause-analysis-in-voc)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **29 KB articles** with **407 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/working-with-analytics-in-zoho-crm-android-app) | 88 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-analytics-in-zoho-crm-android-app) |
| 2 | [Understanding and building reports](https://help.zoho.com/portal/en/kb/crm/understanding-and-building-reports) | 64 | [View Article](https://help.zoho.com/portal/en/kb/crm/understanding-and-building-reports) |
| 3 | [Creating dashboards](https://help.zoho.com/portal/en/kb/crm/create-dashboard) | 37 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-dashboard) |
| 4 | [Zoho CRM Analytics App](https://help.zoho.com/portal/en/kb/crm/zoho-crm-analytics-app) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-crm-analytics-app) |
| 5 | [Zia Recommendation Analytics](https://help.zoho.com/portal/en/kb/crm/zia-recommendation-analytics) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-recommendation-analytics) |
| 6 | [VoC Dashboards in Zoho CRM — A Detailed Study](https://help.zoho.com/portal/en/kb/crm/voc-dashboards-in-zoho-crm-a-study) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/voc-dashboards-in-zoho-crm-a-study) |
| 7 | [Create category columns in reports](https://help.zoho.com/portal/en/kb/crm/create-category-columns-in-reports) | 15 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-category-columns-in-reports) |
| 8 | [Creating Reporting Hierarchy](https://help.zoho.com/portal/en/kb/crm/create-reporting-hierarchy) | 13 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-reporting-hierarchy) |
| 9 | [Segment dashboards](https://help.zoho.com/portal/en/kb/crm/segment-dashboards) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/segment-dashboards) |
| 10 | [Prediction Analytics](https://help.zoho.com/portal/en/kb/crm/prediction-analytics) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/prediction-analytics) |
| 11 | [Create custom dashboards](https://help.zoho.com/portal/en/kb/crm/create-custom-dashboards) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-custom-dashboards) |
| 12 | [Call analytics](https://help.zoho.com/portal/en/kb/crm/call-analytics) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/call-analytics) |
| 13 | [Charts](https://help.zoho.com/portal/en/kb/crm/create-charts) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-charts) |
| 14 | [Summary analyses: A VoC chart for on-the-go insights](https://help.zoho.com/portal/en/kb/crm/summary-analyses-a-voc-chart-for-on-the-go-insight) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/summary-analyses-a-voc-chart-for-on-the-go-insight) |
| 15 | [Using chart views in modules](https://help.zoho.com/portal/en/kb/crm/using-chart-views-in-modules) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/using-chart-views-in-modules) |
| 16 | [Interpreting the reports of Path Finder](https://help.zoho.com/portal/en/kb/crm/interpreting-the-reports-of-path-finder) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/interpreting-the-reports-of-path-finder) |
| 17 | [Visualize hierarchical datasets using treemap charts](https://help.zoho.com/portal/en/kb/crm/visualize-hierarchical-datasets-using-treemap-charts) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/visualize-hierarchical-datasets-using-treemap-charts) |
| 18 | [ Reports module in Zoho CRM Android app ](https://help.zoho.com/portal/en/kb/crm/reports-module-in-zoho-crm-android-app) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/reports-module-in-zoho-crm-android-app) |
| 19 | [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics) |
| 20 | [Sankey Chart](https://help.zoho.com/portal/en/kb/crm/sankey-charts) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/sankey-charts) |
| 21 | [FAQs: Chart View](https://help.zoho.com/portal/en/kb/crm/faqs-chart-view) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-chart-view) |
| 22 | [Compare and contrast competing datasets using butterfly charts](https://help.zoho.com/portal/en/kb/crm/compare-and-contrast-competing-datasets-using-butterfly-charts) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/compare-and-contrast-competing-datasets-using-butterfly-charts) |
| 23 | [Import Usage Data to CRM from Analytics tools](https://help.zoho.com/portal/en/kb/crm/import-usage-data-to-crm-from-analytics-tools) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/import-usage-data-to-crm-from-analytics-tools) |
| 24 | [Zia Dashboard Insights](https://help.zoho.com/portal/en/kb/crm/zia-dashboard-insights) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-dashboard-insights) |
| 25 | [Setting up Advanced CRM Analytics](https://help.zoho.com/portal/en/kb/crm/zoho-analytics-crm-integrations) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-analytics-crm-integrations) |
| 26 | [Cross sell analytics](https://help.zoho.com/portal/en/kb/crm/cross-sell-analytic) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/cross-sell-analytic) |
| 27 | [Scheduling Reports](https://help.zoho.com/portal/en/kb/crm/schedule-reports) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/schedule-reports) |
| 28 | [Editing Criteria Patterns in Reports](https://help.zoho.com/portal/en/kb/crm/editing-criteria-patterns) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/editing-criteria-patterns) |
| 29 | [Setting Advanced CRM Analytics](https://help.zoho.com/portal/en/kb/crm/setting-advanced-crm-analytics-new) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/setting-advanced-crm-analytics-new) |

### Sample Image URLs (from top articles)
**[Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/working-with-analytics-in-zoho-crm-android-app)** — 88 images
- `https://download-accl.zoho.com/webdownload?x-service=writer&amp;event-id=ty6xn88aba3b95213423ca8468a9742351316&amp;x-cli-msg={&quot;imgurl&quot;:&quot;r-ty6xn88aba3b95213423ca8468a9742351316-a75a12f4b8ce42a499b75e75619904d5uzx8ze4ggojl&quot;,&quot;rid&quot;:&quot;ty6xn88aba3b95213423ca8468a9742351316&quot;}`
- `https://download-accl.zoho.com/webdownload?x-service=writer&amp;event-id=ty6xn88aba3b95213423ca8468a9742351316&amp;x-cli-msg={&quot;imgurl&quot;:&quot;905f84867224102032a93c21443a863d46f827e49aba25087d7b0933e9ece85bb4cc0e669ed2a17ef604b2fd60290c26&quot;,&quot;rid&quot;:&quot;ty6xn88aba3b95213423ca8468a9742351316&quot;}`
- `https://download-accl.zoho.com/webdownload?x-service=writer&amp;event-id=ty6xn88aba3b95213423ca8468a9742351316&amp;x-cli-msg={&quot;imgurl&quot;:&quot;4deba3bce1dd11eaacad5d00ed8213d830f0d5a0518b87d94ec3a870c1a3d4767bdf27f39829748537dc7b2a8dd53f5e&quot;,&quot;rid&quot;:&quot;ty6xn88aba3b95213423ca8468a9742351316&quot;}`
- `https://download-accl.zoho.com/webdownload?x-service=writer&amp;event-id=ty6xn88aba3b95213423ca8468a9742351316&amp;x-cli-msg={&quot;imgurl&quot;:&quot;r-ty6xn88aba3b95213423ca8468a9742351316-731483ec9ae743d8b57904cc019676d3ny2n6yc2wyb0&quot;,&quot;rid&quot;:&quot;ty6xn88aba3b95213423ca8468a9742351316&quot;}`
[View all 88 images in article →](https://help.zoho.com/portal/en/kb/crm/working-with-analytics-in-zoho-crm-android-app)

**[Understanding and building reports](https://help.zoho.com/portal/en/kb/crm/understanding-and-building-reports)** — 64 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573760176717d8e1d5d21cada4b98011448f43346c5c0b7622b0a916605e73d208e5ceef684a71986b56a1cb5624aad451?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574f70a23a80d4f908ebadd652e5bb88a1792c9cbbeb4e93a5de5bff48d89f113e3686b7e9627623550d6bccadca9944d3?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579085826cf9c84d12727572260da9787d158ec79de84bfed1490d7cfd9216985276d1d821bebca0ff8d32e2a6ee89d50c?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5758012807f7586fedd313d25339fac7bbcbb16d551466424f18b3d4ab982fda7a37789bde51900ce455961237281e1e61?inline=true`
[View all 64 images in article →](https://help.zoho.com/portal/en/kb/crm/understanding-and-building-reports)

**[Creating dashboards](https://help.zoho.com/portal/en/kb/crm/create-dashboard)** — 37 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ba1a958f9aa1f88b61bfa3ddb3b3f763b3ea01293a805e65c6284f4499c1fa58ffe4db66b168fd4beb7538dc608a8595?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b576b1ca9058c490ed900ad9c0adc7ebc832dc61cb4ca5ddbc63892240b037d0c75b28e98cdb11219ad1564e050d5e0bb74?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57374e50d8a548d293ac35b512f4da2ed6a726a4232bff82f53e5a85fcec8321bc77c18dc1908ec63ef6dbca267776f330?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5777633042566df5ef0f5d85e0274497e65de1acc067cc564727124386d574ab8947791f7b595f82db5e11ff5aabc882ce?inline=true`
[View all 37 images in article →](https://help.zoho.com/portal/en/kb/crm/create-dashboard)

**[Zoho CRM Analytics App](https://help.zoho.com/portal/en/kb/crm/zoho-crm-analytics-app)** — 23 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574b0ce4fd7df6f8467f94c320f946d33d8fc8614ecb8d8ccfbaf22fcc54d086d9b76806a1ef738f6068b9dc8850c25fd3?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e0c8e54257cc00d7b4740ec20c5ed7375e02392928e881dff4d8285a673a948ae65575182e9c52a825ce2303d59bdc12?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573462193bc7c9f5c92f4540ae9427504b6f85913eea0192f0aea16f2095d6b53b64f199abbab79d2db438b56b19ae65d5?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b15a27c58e4ce9f6395c532b4f7ddc2999c01ef0cab5b87fc1e5ac1391e5bcd479a3321cc747bb4bf90cf8619f87f2d3?inline=true`
[View all 23 images in article →](https://help.zoho.com/portal/en/kb/crm/zoho-crm-analytics-app)

**[Zia Recommendation Analytics](https://help.zoho.com/portal/en/kb/crm/zia-recommendation-analytics)** — 18 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ae76804ed203fceed99dce6860bc1b48d7607e78aecf62ecd009165cb55256fa5f788e7deab3a381b699dc37ea690029?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575e5a9224061415a44dab571e9ef9d8cd82fd7a15b448cfc3fd613b2115e25cd97d78cabb9c51c5d5fc2da34381d182a1?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57edb9e597b41a6e51855ac70f6aeed0cba82088bbc5ac189b7d6dfa2d4223055c581bf997414fc1bddba89b3d8ace2060?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ba56971a609713116f2eff8e697ab00afed9fc921fd1a1a253126ecca736bfb7021bab2cabc20f37a80608d92b2ce69d?inline=true`
[View all 18 images in article →](https://help.zoho.com/portal/en/kb/crm/zia-recommendation-analytics)

