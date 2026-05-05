# Blueprint & Process Management

> **Feature ID:** `09-Blueprint-Process-Management`  
> **Knowledge Base Articles:** 66  
> **Last Updated:** 2026-05-05

## Overview

Blueprint-driven sales processes, guided selling, process enforcement, and continuous blueprints

---

## 1. Core Functionality

### 1. Kaizen posts 2024: Widget series

Here is a complete list of Kaizen posts related to Widgets published in 2024 . Sl. No. Title Description 1 How is a Widget used in a Blueprint? Learn how to create widgets and use them in your Zoho CRM account from this post. 2 Geocoding Leads' Addresses in ZOHO CRM Learn how to create a Related List Widget map in Zoho CRM's Lead detail page with lead location display, directions from the current user's location, and showcasing other leads in the same street or city as the current lead. 3 Zoho CRM Widgets using ReactJS Explore how to use ReactJS and other client-side frameworks for Zoho CRM wi
### 2. FAQs: Review Process

1. What is the purpose of a review process? A review process allows you to check and validate the values of a field before the record enters the CRM system. For example, responses entered for fields such as qualification, eligibility criteria, GPA, or product quantity can be validated and approved by CRM users before the record is allowed to enter the system. The fields that require review are highlighted and the reviewers can approve or reject the value and choose a reason for rejecting each field. Read more about review process . 2. Who can be a reviewer? A reviewer can be selected from any
### 3. Troubleshooting Sales Pipelines

I created a pipeline and now I cannot update the Stage field in a record. Creating a pipeline does not affect updating stages in the layout. If a map dependency, blueprint, layout rule, or validation rule has been created based on the Stage field, then you won't be able to update the Stage field. How can I map the pipeline and stage during Hubspot (API) migration? By default , the stage and pipeline in HubSpot are automatically mapped to the Stage and Pipeline fields in Zoho CRM and you cannot alter this mapping during API migration. If you need to migrate stages and pipelines in a different f
### 4. Automation in Team Module

This document will cover the automation-related information for team modules. CRM for everyone opens up module creation to non-admins as mentioned here . This brings the work of customer facing teams into the CRM and gives it context. But teams will soon want to automate repetitive work to make their processes faster and to focus on more important tasks. Teams do not have to rely on org admins for automating their team's work or managing their team's processes. With CRM for everyone, team module admins can do this on their own. This lets teams configure and own their processes fully, while red
### 5. Zia Suggestions for Assignment Rules

Businesses spend a lot of money, time, and effort to bring leads into the sales funnel. Despite those efforts, research shows that about 24% of U.S. companies take about 24 hours on average to make their first move toward a lead—just enough time to turn those onboarded leads cold. There could be any number of reasons for this tardiness, like a shortage of employees, overloaded sales reps, or inefficient process management, but as we examine these causes, we find that the underlying problem is always about record ownership —either the lack of it or inaccuracy in it. Record ownership is an impor
### 6. Managing multiple services in Non-Profit Organizations

Edition: All Paid editions | Industry: NGOs or Non-Profit Organizations | Features: Layouts, Workflow Rules, Blueprint, Assignment Rule, Reports and Dashboards The Requirement Life Drops is an NGO that works towards saving the environment with a focus on water conservation. They have four areas of focus which they call the "four pillars" of their organization. They are: afforestation, water conservation, waste management and awareness camps. Afforestation : Any organization, whether it is an educational institution, a company, or any other establishment, can approach Life Drops to help them pl
### 7. Sales process: Closing deals

Edition : Paid editions | Industry : Applicable for all industries | Features : Integrations with Zoho products and built-in features Lead generation and Lead engagement use cases described the methods used to generate, manage, and engage the leads. Eventually, qualified leads are converted to deals. In this use case we will discuss the steps the design team follow from deal creation through to closure: Send the Design Preference Form when a deal is created Schedule a task for the Design Consultant to call the client once the form is submitted Send the calendar link to clients to schedule a si
### 8. Blueprint Vs Journey Builder — Similarities and differences

Blueprint Vs Journey Builder in Zoho CRM Blueprint and Journey Builder in CRM may have technical similarities in terms of the components of the builder — such as States, Transitions and automated actions. However, since they primarily differ in their purpose and objective, there is ideally no room for confusion in what they set out to accomplish. The confusion, if any, between Blueprint and Journey Builder could arise from the fact that both the solutions have similar building blocks — States, Transitions, and Actions. This is because both the solutions are developed based on the concept of Fi


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `BLUEPRINT`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Kaizen posts 2024: Widget series`
- `FAQs: Review Process`
- `Troubleshooting Sales Pipelines`
- `Automation in Team Module`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/blueprint` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Blueprint & Process Management - Example Implementation
// Triggered on record creation/update

if(input.module == "KAIZEN POSTS 2024: WIDGET SERIES")
{
    // Here is a complete list of Kaizen posts related to Widgets published in 2024 . Sl. No. Title Description 1 How is a Widget used in a Blueprint? Learn
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

- [Deals-Pipeline](../Deals-Pipeline/README.md)
- [Approval-Process](../Approval-Process/README.md)
- [Workflow-Automation](../Workflow-Automation/README.md)
- [Assignment-Rules](../Assignment-Rules/README.md)

### This Feature Enables

- **Deals-Pipeline** -- shares data model and workflows
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

### Kaizen posts 2024: Widget series
**Purpose:** Here is a complete list of Kaizen posts related to Widgets published in 2024 . Sl. No. Title Description 1 How is a Widget used in a Blueprint? Learn how to create widgets and use them in your Zoho CR

**Key Points:**
Here is a complete list of Kaizen posts related to Widgets published in 2024.
Title Description 1 How is a Widget used in a Blueprint.
Learn how to create widgets and use them in your Zoho CRM account from this post.
2 Geocoding Leads' Addresses in ZOHO CRM Learn how to create a Related List Widget map in Zoho CRM's Lead detail page with lead location display, directions from the current user's location, and showcasing other leads in the same street or city as the current lead.
3 Zoho CRM Widgets using ReactJS Explore how to use ReactJS and other client-side frameworks for Zoho CRM widgets.
4 How are Widgets used in Zoho CRM Settings


### FAQs: Review Process
**Purpose:** 1. What is the purpose of a review process? A review process allows you to check and validate the values of a field before the record enters the CRM system. For example, responses entered for fields s

**Key Points:**
What is the purpose of a review process.
A review process allows you to check and validate the values of a field before the record enters the CRM system.
For example, responses entered for fields such as qualification, eligibility criteria, GPA, or product quantity can be validated and approved by CRM users before the record is allowed to enter the system.
The fields that require review are highlighted and the reviewers can approve or reject the value and choose a reason for rejecting each field.
Read more about review process.
A reviewer can be selected from any of the following: a particular role a particular group any CRM user the record owner Read more about selecting reviewers


### Troubleshooting Sales Pipelines
**Purpose:** I created a pipeline and now I cannot update the Stage field in a record. Creating a pipeline does not affect updating stages in the layout. If a map dependency, blueprint, layout rule, or validation

**Key Points:**
I created a pipeline and now I cannot update the Stage field in a record.
Creating a pipeline does not affect updating stages in the layout.
If a map dependency, blueprint, layout rule, or validation rule has been created based on the Stage field, then you won't be able to update the Stage field.
How can I map the pipeline and stage during Hubspot (API) migration.
By default , the stage and pipeline in HubSpot are automatically mapped to the Stage and Pipeline fields in Zoho CRM and you cannot alter this mapping during API migration.
If you need to migrate stages and pipelines in a different format, then you will need to export the data from HubSpot as a spreadsheet and manually importing that data into Zoho CRM, which will allow you to manually map the fields


### Automation in Team Module
**Purpose:** This document will cover the automation-related information for team modules. CRM for everyone opens up module creation to non-admins as mentioned here . This brings the work of customer facing teams

**Key Points:**
This document will cover the automation-related information for team modules.
CRM for everyone opens up module creation to non-admins as mentioned here.
This brings the work of customer facing teams into the CRM and gives it context.
But teams will soon want to automate repetitive work to make their processes faster and to focus on more important tasks.
Teams do not have to rely on org admins for automating their team's work or managing their team's processes.
With CRM for everyone, team module admins can do this on their own


### Zia Suggestions for Assignment Rules
**Purpose:** Businesses spend a lot of money, time, and effort to bring leads into the sales funnel. Despite those efforts, research shows that about 24% of U.S. companies take about 24 hours on average to make th

**Key Points:**
Businesses spend a lot of money, time, and effort to bring leads into the sales funnel.
Despite those efforts, research shows that about 24% of U.
companies take about 24 hours on average to make their first move toward a lead—just enough time to turn those onboarded leads cold.
There could be any number of reasons for this tardiness, like a shortage of employees, overloaded sales reps, or inefficient process management, but as we examine these causes, we find that the underlying problem is always about record ownership —either the lack of it or inaccuracy in it.
Record ownership is an important determinant of successful lead turnover in a business.
That's the first step, in fact


### Managing multiple services in Non-Profit Organizations
**Purpose:** Edition: All Paid editions | Industry: NGOs or Non-Profit Organizations | Features: Layouts, Workflow Rules, Blueprint, Assignment Rule, Reports and Dashboards The Requirement Life Drops is an NGO tha

**Key Points:**
Edition: All Paid editions | Industry: NGOs or Non-Profit Organizations | Features: Layouts, Workflow Rules, Blueprint, Assignment Rule, Reports and Dashboards The Requirement Life Drops is an NGO that works towards saving the environment with a focus on water conservation.
They have four areas of focus which they call the "four pillars" of their organization.
They are: afforestation, water conservation, waste management and awareness camps.
Afforestation : Any organization, whether it is an educational institution, a company, or any other establishment, can approach Life Drops to help them plant trees on their premises.
Water conservation : The NGO also accepts requests from local farmers to help with water body restoration efforts such as reviving rivers and constructing water conservation facilities.
Waste management: As part of corporate social responsibility efforts, organizations may approach Life Drops to help them recycle their waste


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

- [Kaizen posts 2024: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2024)
- [FAQs: Review Process](https://help.zoho.com/portal/en/kb/crm/articles/faqs-review-process)
- [Troubleshooting Sales Pipelines](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-pipelines)
- [Automation in Team Module](https://help.zoho.com/portal/en/kb/crm/articles/automation-in-team-modules)
- [Zia Suggestions for Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/record-owner-suggestion-in-assignment-rule)
- [Managing multiple services in Non-Profit Organizations](https://help.zoho.com/portal/en/kb/crm/articles/managing-multiple-services-in-non-profit-organization)
- [Sales process: Closing deals](https://help.zoho.com/portal/en/kb/crm/articles/sales-process-closing-deals)
- [Blueprint Vs Journey Builder — Similarities and differences](https://help.zoho.com/portal/en/kb/crm/articles/blueprint-and-journey-builder)
- [Executing Blueprints in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/executing-blueprints-in-zoho-crm-android-app)
- [Troubleshooting Blueprint](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-blueprint)
- [Tagging Records in CRM](https://help.zoho.com/portal/en/kb/crm/articles/tagging-records-in-crm)
- [Kaizen posts 2024: Client Script series](https://help.zoho.com/portal/en/kb/crm/articles/client-script-2024)
- [Kaizen posts 2023: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2023)
- [Reorder Approval Processes and Process Rules](https://help.zoho.com/portal/en/kb/crm/articles/reorder-approval-processes)
- [Copy Customization](https://help.zoho.com/portal/en/kb/crm/articles/copy-customization-from-crm)
- [Adding an Approval Process](https://help.zoho.com/portal/en/kb/crm/articles/add-approval-process)
- [Building Journeys Through Journey Builder](https://help.zoho.com/portal/en/kb/crm/articles/journey-builder)
- [Cloning a Blueprint](https://help.zoho.com/portal/en/kb/crm/articles/cloning-blueprint)
- [Create a Continuous Blueprint](https://help.zoho.com/portal/en/kb/crm/articles/create-continuous-blueprint)
- [Assignment threshold in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/assignment-threshold-in-zoho-crm-android-app)
- [Streamlining business processes in a Non-Profit Organization](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-for-non-profit-organizations)
- [Notification SMS integration with Zoho CRM - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/notification-sms-integration-with-zoho-crm)
- [Check Blueprint Usage Reports](https://help.zoho.com/portal/en/kb/crm/articles/blueprint-usage-reports)
- [Designing a Blueprint](https://help.zoho.com/portal/en/kb/crm/articles/design-a-blueprint)
- [FAQs: CommandCenter](https://help.zoho.com/portal/en/kb/crm/articles/faqs-commandcenter)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
