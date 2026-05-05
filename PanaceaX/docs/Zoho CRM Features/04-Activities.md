# Activities & Task Management

> **Feature ID:** `04-Activities`  
> **Knowledge Base Articles:** 734  
> **Last Updated:** 2026-05-05

## Overview

Tasks, calls, meetings, notes, and activity tracking across the CRM

---

## 1. Core Functionality

### 1. Spotfone

Spotfone is a cloud telephony platform integrated with Zoho PhoneBridge to provide better communication to your customers. Perform all call-related activities right inside your CRM account. Setup integration To set up this integration, Go to Setup > Channels > Telephony. Choose Spotfone from the PhoneBridge Marketplace . Click Integrate . Click Get it now . For configuration steps, click here . Using Spotfone integration Spotfone for Zoho PhoneBridge help you perform all your call related activities directly within your CRM account. Once the set up is done, you can do the following: When you r
### 2. FAQs: Zoho CRM for Google Ads

Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration. However, this does not erase the details fetched from the previous accounts. Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts. Can I configure more than one client account with Zoho CRM? Yes. If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would w
### 3. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made o
### 4. Zoho CRM for Google Ads

Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites. By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI). Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to ma
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

**Primary Module:** `ACTIVITIES`

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
- `Zoho CRM for Google Ads`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/activities` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Activities & Task Management - Example Implementation
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
- [Contacts-Management](../Contacts-Management/README.md)
- [Deals-Pipeline](../Deals-Pipeline/README.md)
- [Workflow-Automation](../Workflow-Automation/README.md)
- [Email-Tools](../Email-Tools/README.md)

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


### Zoho CRM for Google Ads
**Purpose:** Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner we

**Key Points:**
Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites.
By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI).
Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to make strategic marketing decisions for your business.
If you use Google Ads to drive potential customers to your website and a customer relationship management system (CRM) to track offline sales made through phone calls, emails, or direct sales, it can be difficult for your business to determine how your online campaign investments lead to offline conversion data stored in Zoho CRM.
With Zoho CRM for Google Ads , you can now import your Google Ads marketing investments into Zoho CRM so you can see which keywords and campaigns are responsible for each offline sale.
Plus, you can also export Zoho CRM sales data into Google Ads so you can better optimize your bids and budgets to yield maximum revenue and profits


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

- [Spotfone](https://help.zoho.com/portal/en/kb/crm/articles/integrate-spotfone)
- [FAQs: Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/faqs-google-adwords)
- [Schedule annual notifications for subscription renewals](https://help.zoho.com/portal/en/kb/crm/articles/automatic-schedule-notifications)
- [Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/google-ads-crm-integration)
- [Importing Contacts from G Suite](https://help.zoho.com/portal/en/kb/crm/articles/import-contacts-g-suite)
- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [FAQs: Calls Module](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-calls-module)
- [Create category columns in reports](https://help.zoho.com/portal/en/kb/crm/articles/create-category-columns-in-reports)
- [Setting up an Unsubscribe Link](https://help.zoho.com/portal/en/kb/crm/articles/set-unsubscribe-link)
- [Kaizen posts 2023: SDK series](https://help.zoho.com/portal/en/kb/crm/articles/sdk-2023)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Setting up Zoho Writer Add-on](https://help.zoho.com/portal/en/kb/crm/articles/zoho-writer-crm-integration)
- [SurveyMonkey](https://help.zoho.com/portal/en/kb/crm/articles/surveymonkey-crm-integration)
- [Kaizen posts 2024: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2024)
- [FAQs: Developer Hub](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-developer-hub)
- [Managing Web Tabs](https://help.zoho.com/portal/en/kb/crm/articles/web-tabs)
- [Capabilities of Zia in Zoho CRM— A perspective](https://help.zoho.com/portal/en/kb/crm/articles/zia-overview)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [Installing the MS Word Plug-in](https://help.zoho.com/portal/en/kb/crm/articles/install-ms-word-plug-in-crm-integration)
- [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/naijasmsportal-for-zoho-crm)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [RingCentral Video](https://help.zoho.com/portal/en/kb/crm/articles/ringcentral-video)
- [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/articles/set-email-notifications)
- [Address Locator for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/address-locator-for-zoho-crm)
- [WeChat for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/wechat-for-zoho-crm-3-8-2021)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
