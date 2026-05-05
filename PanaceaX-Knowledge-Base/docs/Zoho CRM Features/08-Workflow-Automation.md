# Workflow & Business Automation

> **Feature ID:** `08-Workflow-Automation`  
> **Knowledge Base Articles:** 163  
> **Last Updated:** 2026-05-05

## Overview

Workflow rules, automation rules, field updates, tasks, and deluge scripting

---

## 1. Core Functionality

### 1. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made o
### 2. Zia for Workflow Rules

You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people. However, keeping track of triggers made through workflow rules to see what works best and what doesn't could be cumbersome. Zia does just that for you. Zia brings AI to your workflow automation processes by detecting anomalies and provide suggestions for your workflow rules. Zia also identifies and prevents you from making mistakes, such as sending multiple email templates to the same customer on the same day. Availability Permission Required Us
### 3. Managing Process

Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple roles. The approval processes created in the web version of Zoho CRM will also appear in the mobile version. Permission Required Users with Manage workflow permission in their profile can access this feature. Check Feature Availability and Limits Records that are waiting for approval can be viewed in the Android app and can then be approved, rejected, or delegated from the My Jobs module or from the r
### 4. FAQs: Developer Hub

How can I fetch the data from the Leads module to my application using an API? You can use the Zoho CRM REST API to retrieve data from the Leads module and other modules. Refer to this document for more details. Is the API key user-specific or organization-specific? The Zoho CRM API key is organization-specific. You can use the same API Key for all users with different ticket IDs (user-specific). What is the format of the xmlData parameter to associate a task or event to CRM records? Use the following sample XML for relating an event with the account and contact respectively. Account <Events><
### 5. Capabilities of Zia in Zoho CRM— A perspective

Zoho CRM harnesses the transformative power of Artificial Intelligence (AI) to revolutionise decision-making across all critical areas of your business, from initial customer interactions to their entire journey. With Zia, AI-powered assistant, Zoho CRM offers valuable insights and suggestions that permeate every aspect of CRM management, including automation, customer engagement, analytics, and data management. Take a look at this video to understand how Zia can help your businesses Zia offers you the AI experience across the breadth of Zoho CRM under six key categories: Data Management Produ
### 6. Introducing Actions in Zoho CRM

Create actions to automate your sales and marketing activities. Help guide Configuring Automatic Actions ​
### 7. Data Privacy

A record's details are available in two sections - Info and Timeline. When you switch on GDPR Compliance in your Zoho CRM account, you will be able to view another section, namely Data Privacy . This section has the following details: Data Source Personal Fields Data Processing Bases View Data Source Data Subject information can be pushed into Zoho CRM from multiple sources such as the web-forms, by importing, APIs and third-party integrations. Data Source displays the information about how the record was Created and when it was Last Updated . Along with these information, additional details w
### 8. Setting Email Notifications

Email Notifications are among the instant and scheduled actions associated with different automations in CRM. They are alerts, notifications, information, or details sent to leads, contacts and users within the organization. When you associate an email notification to an automation, the selected email is automatically sent to the chosen recipients when the configuration criteria is met. Availability Permission Required Users with either Manage Automation or Modules Customization permissions can access this feature.. To set up an email notification Go to Setup[ ] > Automation > Actions > Email


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `WORKFLOW`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Schedule annual notifications for subscription renewals`
- `Zia for Workflow Rules`
- `Managing Process`
- `FAQs: Developer Hub`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/workflow` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Workflow & Business Automation - Example Implementation
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

- [Blueprint-Process-Management](../Blueprint-Process-Management/README.md)
- [Assignment-Rules](../Assignment-Rules/README.md)
- [Approval-Process](../Approval-Process/README.md)
- [Email-Tools](../Email-Tools/README.md)

### This Feature Enables

- **Blueprint-Process-Management** -- shares data model and workflows
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


### Zia for Workflow Rules
**Purpose:** You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people. However, keeping track of triggers made through w

**Key Points:**
You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people.
However, keeping track of triggers made through workflow rules to see what works best and what doesn't could be cumbersome.
Zia does just that for you.
Zia brings AI to your workflow automation processes by detecting anomalies and provide suggestions for your workflow rules.
Zia also identifies and prevents you from making mistakes, such as sending multiple email templates to the same customer on the same day.
Availability Permission Required Users with manage Automation permission in their profile can access this feature


### Managing Process
**Purpose:** Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple role

**Key Points:**
Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization.
This type of formal approval requires input from multiple roles.
The approval processes created in the web version of Zoho CRM will also appear in the mobile version.
Permission Required Users with Manage workflow permission in their profile can access this feature.
Check Feature Availability and Limits Records that are waiting for approval can be viewed in the Android app and can then be approved, rejected, or delegated from the My Jobs module or from the record detail view of a specific module.
To approve a record Tap the icon in your Zoho CRM app


### FAQs: Developer Hub
**Purpose:** How can I fetch the data from the Leads module to my application using an API? You can use the Zoho CRM REST API to retrieve data from the Leads module and other modules. Refer to this document for mo

**Key Points:**
How can I fetch the data from the Leads module to my application using an API.
You can use the Zoho CRM REST API to retrieve data from the Leads module and other modules.
Refer to this document for more details.
Is the API key user-specific or organization-specific.
The Zoho CRM API key is organization-specific.
You can use the same API Key for all users with different ticket IDs (user-specific)


### Capabilities of Zia in Zoho CRM— A perspective
**Purpose:** Zoho CRM harnesses the transformative power of Artificial Intelligence (AI) to revolutionise decision-making across all critical areas of your business, from initial customer interactions to their ent

**Key Points:**
Zoho CRM harnesses the transformative power of Artificial Intelligence (AI) to revolutionise decision-making across all critical areas of your business, from initial customer interactions to their entire journey.
With Zia, AI-powered assistant, Zoho CRM offers valuable insights and suggestions that permeate every aspect of CRM management, including automation, customer engagement, analytics, and data management.
Take a look at this video to understand how Zia can help your businesses Zia offers you the AI experience across the breadth of Zoho CRM under six key categories: Data Management Productivity Customer Experience Insights and Analytics Intelligent Alerts Customer engagement and retention.
Data Management Zia facilitates data management in Zoho CRM by providing advanced capabilities for organizing, structuring, and optimizing your data.
With Zia, you can easily maintain data integrity, streamline data entry processes, and ensure the accuracy and consistency of your CRM information.
Data enrichment with Zia: An incomplete data set will not help you when you want to reach out to customers and have meaningful conversations with them


### Introducing Actions in Zoho CRM
**Purpose:** Create actions to automate your sales and marketing activities. Help guide Configuring Automatic Actions ​

**Key Points:**
Create actions to automate your sales and marketing activities.
Help guide Configuring Automatic Actions ​


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
- [Zia for Workflow Rules](https://help.zoho.com/portal/en/kb/crm/articles/zia-intelligence-automation)
- [Managing Process](https://help.zoho.com/portal/en/kb/crm/articles/managing-process-in-zoho-crm-android-app)
- [FAQs: Developer Hub](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-developer-hub)
- [Capabilities of Zia in Zoho CRM— A perspective](https://help.zoho.com/portal/en/kb/crm/articles/zia-overview)
- [Introducing Actions in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/actions-an-introduction)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/articles/set-email-notifications)
- [Workflow for Appointments](https://help.zoho.com/portal/en/kb/crm/articles/workflow-rules-for-appointments)
- [Actions - Tasks](https://help.zoho.com/portal/en/kb/crm/articles/actions-tasks)
- [Setting Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/set-assignment-rules)
- [Acting on VoC insights](https://help.zoho.com/portal/en/kb/crm/articles/acting-on-voc-insights)
- [Setting Field Updates](https://help.zoho.com/portal/en/kb/crm/articles/field-updates)
- [Trello](https://help.zoho.com/portal/en/kb/crm/articles/trello)
- [Assess the outgoing call quality of the sales agents](https://help.zoho.com/portal/en/kb/crm/articles/assess-call-quality-review-performance)
- [Custom AI Studio](https://help.zoho.com/portal/en/kb/crm/articles/custom-ai-studio)
- [Social integration in sandbox](https://help.zoho.com/portal/en/kb/crm/articles/social-integration-in-sandbox)
- [Automation in Team Module](https://help.zoho.com/portal/en/kb/crm/articles/automation-in-team-modules)
- [Support Access for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/support-access)
- [Aircall](https://help.zoho.com/portal/en/kb/crm/articles/integrate-with-aircall)
- [Zia Suggestions for Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/record-owner-suggestion-in-assignment-rule)
- [Workflow Suggestions by Zia](https://help.zoho.com/portal/en/kb/crm/articles/workflow-suggestions)
- [FAQs: Page layouts](https://help.zoho.com/portal/en/kb/crm/articles/faqs-page-layouts)
- [Managing multiple services in Non-Profit Organizations](https://help.zoho.com/portal/en/kb/crm/articles/managing-multiple-services-in-non-profit-organization)
- [Pushing Data to Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/push-data-to-google-ads)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **40 KB articles** with **352 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Working with Validation Rules](https://help.zoho.com/portal/en/kb/crm/create-validation-rules) | 31 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-validation-rules) |
| 2 | [Configuring Workflow Rules](https://help.zoho.com/portal/en/kb/crm/configuring-workflow-rules) | 28 | [View Article](https://help.zoho.com/portal/en/kb/crm/configuring-workflow-rules) |
| 3 | [FAQs: Approval Process](https://help.zoho.com/portal/en/kb/crm/faqs-on-approval-process) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-on-approval-process) |
| 4 | [Connected Workflows](https://help.zoho.com/portal/en/kb/crm/connected-workflows) | 21 | [View Article](https://help.zoho.com/portal/en/kb/crm/connected-workflows) |
| 5 | [Sales Force Automation (SFA) in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/sales-force-automation-sfa-in-zoho-crm) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/sales-force-automation-sfa-in-zoho-crm) |
| 6 | [FAQs: Workflow Rules](https://help.zoho.com/portal/en/kb/crm/faqs-workflow) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-workflow) |
| 7 | [CPQ Rule Execution: Product Configurator](https://help.zoho.com/portal/en/kb/crm/cpq-rule-execution-product-configurator) | 16 | [View Article](https://help.zoho.com/portal/en/kb/crm/cpq-rule-execution-product-configurator) |
| 8 | [Zia Suggestions for Assignment Rules](https://help.zoho.com/portal/en/kb/crm/record-owner-suggestion-in-assignment-rule) | 15 | [View Article](https://help.zoho.com/portal/en/kb/crm/record-owner-suggestion-in-assignment-rule) |
| 9 | [Workflow Report](https://help.zoho.com/portal/en/kb/crm/workflow-report) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/workflow-report) |
| 10 | [Adding an Approval Process](https://help.zoho.com/portal/en/kb/crm/add-approval-process) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/add-approval-process) |
| 11 | [Scoring Rules](https://help.zoho.com/portal/en/kb/crm/multiple-scoring-rule) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/multiple-scoring-rule) |
| 12 | [Setting up Data Sharing Rules](https://help.zoho.com/portal/en/kb/crm/data-sharing-rules) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/data-sharing-rules) |
| 13 | [Workflow for Emails](https://help.zoho.com/portal/en/kb/crm/workflow-for-emails) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/workflow-for-emails) |
| 14 | [Workflow Scenarios](https://help.zoho.com/portal/en/kb/crm/workflow-scenarios) | 11 | [View Article](https://help.zoho.com/portal/en/kb/crm/workflow-scenarios) |
| 15 | [Workflow for Calls](https://help.zoho.com/portal/en/kb/crm/workflow-rules-calls) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/workflow-rules-calls) |
| 16 | [Working on records in approval process](https://help.zoho.com/portal/en/kb/crm/working-on-records-in-approval-process) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-on-records-in-approval-process) |
| 17 | [FAQs: Case Escalation Rules](https://help.zoho.com/portal/en/kb/crm/faqs-case-escalation-rules) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-case-escalation-rules) |
| 18 | [Associating Actions for Approval or Rejection](https://help.zoho.com/portal/en/kb/crm/actions-approval-rejection) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/actions-approval-rejection) |
| 19 | [Approving or Rejecting from the Approval Tab](https://help.zoho.com/portal/en/kb/crm/approval-tab) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/approval-tab) |
| 20 | [Reorder Approval Processes and Process Rules](https://help.zoho.com/portal/en/kb/crm/reorder-approval-processes) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/reorder-approval-processes) |
| 21 | [FAQ: Approval Process](https://help.zoho.com/portal/en/kb/crm/faq-approval-process) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/faq-approval-process) |
| 22 | [Setting Case Escalation Rules](https://help.zoho.com/portal/en/kb/crm/set-case-escalation-rules) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/set-case-escalation-rules) |
| 23 | [Workflow Suggestions by Zia](https://help.zoho.com/portal/en/kb/crm/workflow-suggestions) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/workflow-suggestions) |
| 24 | [Automation in Team Module](https://help.zoho.com/portal/en/kb/crm/automation-in-team-modules) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/automation-in-team-modules) |
| 25 | [Creating Schedules in Automation](https://help.zoho.com/portal/en/kb/crm/custom-schedules) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/custom-schedules) |
| 26 | [Converting Records Using Workflow Rules](https://help.zoho.com/portal/en/kb/crm/convert-records-using-workflow-rule) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/convert-records-using-workflow-rule) |
| 27 | [Troubleshooting Workflows](https://help.zoho.com/portal/en/kb/crm/troubleshooting-workflows) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/troubleshooting-workflows) |
| 28 | [FAQs: Workflow for Emails](https://help.zoho.com/portal/en/kb/crm/faqs-workflow-for-emails) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-workflow-for-emails) |
| 29 | [What is the key difference between workflow rule for the Calls module and adding Call as an action in a workflow rule?](https://help.zoho.com/portal/en/kb/crm/what-is-the-key-difference-between-workflow-rule-for-the-calls-module-and-adding-call-as-an-action-in-a-workflow-rule) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/what-is-the-key-difference-between-workflow-rule-for-the-calls-module-and-adding-call-as-an-action-in-a-workflow-rule) |
| 30 | [FAQs: Validation Rules](https://help.zoho.com/portal/en/kb/crm/faqs-validation-rules) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-validation-rules) |
| 31 | [Zia for Workflow Rules](https://help.zoho.com/portal/en/kb/crm/zia-intelligence-automation) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/zia-intelligence-automation) |
| 32 | [Creating Validation Rules Using Functions](https://help.zoho.com/portal/en/kb/crm/create-validation-rules-using-functions) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-validation-rules-using-functions) |
| 33 | [Sales Force Automation - The Concept](https://help.zoho.com/portal/en/kb/crm/sales-force-automation-the-concept) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/sales-force-automation-the-concept) |
| 34 | [Workflow for Social (Facebook and Twitter)](https://help.zoho.com/portal/en/kb/crm/workflow-for-social) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/workflow-for-social) |
| 35 | [View Approval History](https://help.zoho.com/portal/en/kb/crm/view-approval-history) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/view-approval-history) |
| 36 | [Workflow for Appointments](https://help.zoho.com/portal/en/kb/crm/workflow-rules-for-appointments) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/workflow-rules-for-appointments) |
| 37 | [Adding Layouts Rules](https://help.zoho.com/portal/en/kb/crm/create-conditional-layouts) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-conditional-layouts) |
| 38 | [Approval processes in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/approval-processes-in-zoho-crm-ios-app) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/approval-processes-in-zoho-crm-ios-app) |
| 39 | [Setting Assignment Rules](https://help.zoho.com/portal/en/kb/crm/set-assignment-rules) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/set-assignment-rules) |
| 40 | [FAQs: Sales Force Automation](https://help.zoho.com/portal/en/kb/crm/faqs-sales-force-automation) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-sales-force-automation) |

### Sample Image URLs (from top articles)
**[Working with Validation Rules](https://help.zoho.com/portal/en/kb/crm/create-validation-rules)** — 31 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57c45457395e9329dc9abc1430c945726555f3cd723b10c030fefd4bf004dc179b47faa64a406ef20830d45fa85a5084ab?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5750218c76a9aa90741066602b45dc885a790ef728eb37609804087fdde240d8da5d95f88bb7f717a95383ee0c84dd9479?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574ade50e671ba7a85480517f01959eda910e435763668b9d1148b74009465fba4f0b47bbd7ef0c17afeb7b98343169756?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57288b201dc2396471185230a620c79731348768f00110796245d8b5bf705f50bdac8b9ef416c7453132df047ce59a1056?inline=true`
[View all 31 images in article →](https://help.zoho.com/portal/en/kb/crm/create-validation-rules)

**[Configuring Workflow Rules](https://help.zoho.com/portal/en/kb/crm/configuring-workflow-rules)** — 28 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57113877aeead67a0c8ad82d0d25846bd5fa5c94234d24df6097e43c024820d48060a0d73f4e9387b19ac9725e53118e6b?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b577eaa14476f84078076910e4ee379cdbedc097d5664ef6874dedfde6133e3ce87ff87f4c91e05657ef49f73dd29acf1a0?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b578001679551897055d7b3400aad2babbd6e0e785375b9fe1ba08d0951c336138feb6d576feaf31f6522f6f2e068deab67?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f6a2a339f02814fbf46188e97955f71d2e1b1b94f9e12380485ca3507dcdf96abcce3e72f74ae8fe978b830bdbf897ca?inline=true`
[View all 28 images in article →](https://help.zoho.com/portal/en/kb/crm/configuring-workflow-rules)

**[FAQs: Approval Process](https://help.zoho.com/portal/en/kb/crm/faqs-on-approval-process)** — 23 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e9f1043518512bc248f6fd49977f30b9fec7fe534293a478d57a209ffd9cba879d2061e13b6b702a120064d47279ec3b?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574de8d3fee46a047b09e9036ef5a4245c14106328fc1054a23b3bfa2b89992485449c3718625d2c5bb960258a26719ba0?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57809398d20b9eafd94f3f109467f59d74f770b0e5631a61537c132db78d4378ee99746d07815fe3b76e28a20433272de5?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574834ad2c4a2d61870a23a06a1516ad847046d6d872e0bf86b1b78f7680c1f02b0ea79999d9816a9f042d3d7c8600f01d?inline=true`
[View all 23 images in article →](https://help.zoho.com/portal/en/kb/crm/faqs-on-approval-process)

**[Connected Workflows](https://help.zoho.com/portal/en/kb/crm/connected-workflows)** — 21 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b572e15d6001430b19b74bf819907f1162e6555378df220f22d169753ba6799847a8a03077054ab160b49b703431ae023df?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b570e0a3230db7ce8758f55c9b92c209c05aa0cd835afefe0dfe36f32d58043acca062a872b77c72acfa8f0aba63abd9b33?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b570f7e76d7da2bb2b280552d227f30e0def91b8533cdb209ed4a7cec21dc72f95db04990c6106893e6b8e3d392cbe329f6?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579b7d2ffaa21742f3e5933c1773214ecf06c0486253e99e8d48d68254ccb3e2ab13801055b92cf19fee5d6fb278e93d30?inline=true`
[View all 21 images in article →](https://help.zoho.com/portal/en/kb/crm/connected-workflows)

**[Sales Force Automation (SFA) in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/sales-force-automation-sfa-in-zoho-crm)** — 20 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b576b0327de694edd767c4369bc8e675a80dc42719c01de30029fd2cebfa4b0f556cff48426802cf9e11304fcdb1797b8f6?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57409725c201041f663456bae404d29a5a82c83fb6f368eba7dbb1912fb8ee3c503ab63c566d180ce58658e74f3a2b6e2f?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5795c1eff203ee2a52be28ce571f658097cb4b945128eb5c75102a13b917698679927a7aec87adeaa4a737eff0b7b1b80c?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5711d0a953836d681523071a9d2c9d95a822c8e135cd104b33315c4829b3e63b25b9a33a7aedd26a50e0dac3961866d6ac?inline=true`
[View all 20 images in article →](https://help.zoho.com/portal/en/kb/crm/sales-force-automation-sfa-in-zoho-crm)

