# Assignment Rules & Territory Management

> **Feature ID:** `10-Assignment-Rules`  
> **Knowledge Base Articles:** 36  
> **Last Updated:** 2026-05-05

## Overview

Automatic record assignment, territory-based routing, round-robin, and threshold-based assignment

---

## 1. Core Functionality

### 1. Decision Guide for Territory Management

Assumptions This document assumes that you are already aware of the basic concepts of territory management. For an understanding of the feature in Zoho CRM, take a look at the help document - Territory Management Overview . Introduction Territory Management is a system by which customer accounts are grouped based on a defined set of criteria. This makes for easy sharing of customer accounts among sales teams in your company. In Zoho CRM, the territory management feature lets you: Create territories and specify criteria that defines a territory. Build a territory hierarchy in addition to the ro
### 2. Setting Assignment Rules

A sales success is closely coupled with the everyday activities of the reps, such as - number of follow-ups, promptness in getting back to the customers, offering quick answers to their queries, and responding to the support tickets. All these factors play a crucial role in moving the leads rapidly through the sales funnel, eventually leading to a successful sale closure. An important aspect in achieving the above depends on how well-organized and planned the lead assignment process in an organization is. Most businesses rely on multiple sources to generate leads. With each lead/customer havin
### 3. Setting up Webforms

Creating a webform involves three steps: Building the form - Drag and drop fields to build a form and format it easily with the WYSIWYG editor. Specifying the form details - Add details such as form name, landing page URL (where the visitor needs to be redirected after the form is submitted) record assignment rule, notification details, etc. Generating the code for the form - Embed the form using various code formats. Codes for some third-party sites (WordPress, Google Sites, Facebook, and Joomla) are readily available. You can build webforms to generate records for the Leads , Contacts , Case
### 4. Assignment Rules

Assign records to appropriate users using Assignment Rules Help guide Setting up Assignment Rules
### 5. Automation in Team Module

This document will cover the automation-related information for team modules. CRM for everyone opens up module creation to non-admins as mentioned here . This brings the work of customer facing teams into the CRM and gives it context. But teams will soon want to automate repetitive work to make their processes faster and to focus on more important tasks. Teams do not have to rely on org admins for automating their team's work or managing their team's processes. With CRM for everyone, team module admins can do this on their own. This lets teams configure and own their processes fully, while red
### 6. Zia Suggestions for Assignment Rules

Businesses spend a lot of money, time, and effort to bring leads into the sales funnel. Despite those efforts, research shows that about 24% of U.S. companies take about 24 hours on average to make their first move toward a lead—just enough time to turn those onboarded leads cold. There could be any number of reasons for this tardiness, like a shortage of employees, overloaded sales reps, or inefficient process management, but as we examine these causes, we find that the underlying problem is always about record ownership —either the lack of it or inaccuracy in it. Record ownership is an impor
### 7. Managing multiple services in Non-Profit Organizations

Edition: All Paid editions | Industry: NGOs or Non-Profit Organizations | Features: Layouts, Workflow Rules, Blueprint, Assignment Rule, Reports and Dashboards The Requirement Life Drops is an NGO that works towards saving the environment with a focus on water conservation. They have four areas of focus which they call the "four pillars" of their organization. They are: afforestation, water conservation, waste management and awareness camps. Afforestation : Any organization, whether it is an educational institution, a company, or any other establishment, can approach Life Drops to help them pl
### 8. Zoho CRM Webforms for Google Sites

Webforms simplify the process of capturing visitors' or users' information from the website into your CRM system. They are designed to automate importing of data from website into Zoho CRM and to enable non-technical users to design and publish their own webforms. Zoho CRM webforms for Google Sites helps G Suite users to use webforms in Google sites to capture visitor information. Before setting the webform, ensure the following check-list: Create a default Email template to send automated replies to website visitors upon submission of their details. Create an Assignment rule if you wish to as


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `ASSIGNMENT`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Decision Guide for Territory Management`
- `Setting Assignment Rules`
- `Setting up Webforms`
- `Assignment Rules`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/assignment` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Assignment Rules & Territory Management - Example Implementation
// Triggered on record creation/update

if(input.module == "DECISION GUIDE FOR TERRITORY MANAGEMENT")
{
    // Assumptions This document assumes that you are already aware of the basic concepts of territory management. For an understanding of the feature in Zoh
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
- [Zia-AI](../Zia-AI/README.md)

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

### Decision Guide for Territory Management
**Purpose:** Assumptions This document assumes that you are already aware of the basic concepts of territory management. For an understanding of the feature in Zoho CRM, take a look at the help document - Territor

**Key Points:**
Assumptions This document assumes that you are already aware of the basic concepts of territory management.
For an understanding of the feature in Zoho CRM, take a look at the help document - Territory Management Overview.
Introduction Territory Management is a system by which customer accounts are grouped based on a defined set of criteria.
This makes for easy sharing of customer accounts among sales teams in your company.
In Zoho CRM, the territory management feature lets you: Create territories and specify criteria that defines a territory.
Build a territory hierarchy in addition to the role hierarchy in your account


### Setting Assignment Rules
**Purpose:** A sales success is closely coupled with the everyday activities of the reps, such as - number of follow-ups, promptness in getting back to the customers, offering quick answers to their queries, and r

**Key Points:**
A sales success is closely coupled with the everyday activities of the reps, such as - number of follow-ups, promptness in getting back to the customers, offering quick answers to their queries, and responding to the support tickets.
All these factors play a crucial role in moving the leads rapidly through the sales funnel, eventually leading to a successful sale closure.
An important aspect in achieving the above depends on how well-organized and planned the lead assignment process in an organization is.
Most businesses rely on multiple sources to generate leads.
With each lead/customer having disparate requirements, it is best to avoid assigning them randomly to the reps.
Instead, they could be assigned to reps who have an expertise with managing leads from a region or a specific product


### Setting up Webforms
**Purpose:** Creating a webform involves three steps: Building the form - Drag and drop fields to build a form and format it easily with the WYSIWYG editor. Specifying the form details - Add details such as form n

**Key Points:**
Creating a webform involves three steps: Building the form - Drag and drop fields to build a form and format it easily with the WYSIWYG editor.
Specifying the form details - Add details such as form name, landing page URL (where the visitor needs to be redirected after the form is submitted) record assignment rule, notification details, etc.
Generating the code for the form - Embed the form using various code formats.
Codes for some third-party sites (WordPress, Google Sites, Facebook, and Joomla) are readily available.
You can build webforms to generate records for the Leads , Contacts , Cases and any other Custom modules.
While building a webform, the following elements are available in the form: Option Description Add fields Drag and drop the fields that are required in the form


### Assignment Rules
**Purpose:** Assign records to appropriate users using Assignment Rules Help guide Setting up Assignment Rules

**Key Points:**
Assign records to appropriate users using Assignment Rules Help guide Setting up Assignment Rules


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

- [Decision Guide for Territory Management](https://help.zoho.com/portal/en/kb/crm/articles/territory-decision-management)
- [Setting Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/set-assignment-rules)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/assignment-rules-2-7-2021)
- [Automation in Team Module](https://help.zoho.com/portal/en/kb/crm/articles/automation-in-team-modules)
- [Zia Suggestions for Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/record-owner-suggestion-in-assignment-rule)
- [Managing multiple services in Non-Profit Organizations](https://help.zoho.com/portal/en/kb/crm/articles/managing-multiple-services-in-non-profit-organization)
- [Zoho CRM Webforms for Google Sites](https://help.zoho.com/portal/en/kb/crm/articles/web-forms-google-sites)
- [Automatically assign leads from a particular source to selected reps](https://help.zoho.com/portal/en/kb/crm/articles/lead-assignment-based-on-lead-source)
- [Troubleshooting Blueprint](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-blueprint)
- [FAQs : Sales Forecasting](https://help.zoho.com/portal/en/kb/crm/articles/faqs-sales-forecasting)
- [FAQs: Tagging](https://help.zoho.com/portal/en/kb/crm/articles/faqs-tagging)
- [Using the MS Outlook Plug-in (Windows)](https://help.zoho.com/portal/en/kb/crm/articles/using-the-ms-outlook-plug-in-windows)
- [Assigning Record Owner](https://help.zoho.com/portal/en/kb/crm/articles/assigning-record-owner)
- [Assigning Territories](https://help.zoho.com/portal/en/kb/crm/articles/assign-territories)
- [Sales process: Lead engagement](https://help.zoho.com/portal/en/kb/crm/articles/sales-process-lead-engagement)
- [Create a system-defined, guided sales process for a step-by-step lead conversion](https://help.zoho.com/portal/en/kb/crm/articles/create-system-defined-sales-process-for-a-step-by-step-lead-conversion)
- [Territory Management - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/territory-management)
- [Digital Employees: Behavior and Scope](https://help.zoho.com/portal/en/kb/crm/articles/digital-employees-behavior-and-scope)
- [Kaizen posts 2023: API series](https://help.zoho.com/portal/en/kb/crm/articles/api-2023)
- [Webforms - An Introduction](https://help.zoho.com/portal/en/kb/crm/articles/web-forms-introduction)
- [FAQs: Import](https://help.zoho.com/portal/en/kb/crm/articles/faqs-import)
- [Automate your Business Process](https://help.zoho.com/portal/en/kb/crm/articles/get-started-automate-business-process)
- [Using Territories](https://help.zoho.com/portal/en/kb/crm/articles/use-territories)
- [Working With Leads](https://help.zoho.com/portal/en/kb/crm/articles/leads-26-4-2026)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **8 KB articles** with **48 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [FAQs: Assignment](https://help.zoho.com/portal/en/kb/crm/faqs-assignment) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-assignment) |
| 2 | [Assignment Threshold](https://help.zoho.com/portal/en/kb/crm/assignment-threshold) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/assignment-threshold) |
| 3 | [Assigning Record Owner](https://help.zoho.com/portal/en/kb/crm/assigning-record-owner) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/assigning-record-owner) |
| 4 | [Decision Guide for Territory Management](https://help.zoho.com/portal/en/kb/crm/territory-decision-management) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/territory-decision-management) |
| 5 | [Assignment Threshold in Zoho CRM iOS](https://help.zoho.com/portal/en/kb/crm/assignment-threshold-in-zoho-crm-ios) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/assignment-threshold-in-zoho-crm-ios) |
| 6 | [Assignment threshold in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/assignment-threshold-in-zoho-crm-android-app) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/assignment-threshold-in-zoho-crm-android-app) |
| 7 | [Assigning Territories](https://help.zoho.com/portal/en/kb/crm/assign-territories) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/assign-territories) |
| 8 | [Territory Management - An Overview](https://help.zoho.com/portal/en/kb/crm/territory-management) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/territory-management) |

### Sample Image URLs (from top articles)
**[FAQs: Assignment](https://help.zoho.com/portal/en/kb/crm/faqs-assignment)** — 14 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575842f6a351fd51b658ce3c065e4b76a53c13b661e6b2e32dd1b11288c592f67a17c8c7d22cf961cf42e9e8df74355677?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b576da7958d3618ccb2b7619561b77b67c888ff1b24b7df7e995b26085099e60de7e2b4dee379c5c9732591c07826bcee3e?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579f441529f3cda40f4f91f6c9334e4c9d652c0aad7fcc899e2fcfaac654c814b3f27af9331d615189a34a0de682f2089a?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574751fe1b73343e465b22f248a656be5ce0943c63ff88a49716684ad0174bae20fecc63572013a69ddc5d19f11409235e?inline=true`
[View all 14 images in article →](https://help.zoho.com/portal/en/kb/crm/faqs-assignment)

**[Assignment Threshold](https://help.zoho.com/portal/en/kb/crm/assignment-threshold)** — 9 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574a5e629d8e7600415bfe7ac94fedd9e4b55b65782def65746c8c148eb1e128d36eaff74998227529dbfeed245705f28b?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57edf0df16dc8e9e65048f67626800e8c4fe7cef25352d3d06c86f3ea20d1bab153e6718eb6d788bf47e82c98f0041cb53?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f902383093875a3e35335297e0abfebdb57ac54ae00ceb0605c2f7188da8cc22c97aed75288657edba0f0b1da91b08a0?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f089d691127a61c0a8a2273976049f6fcf13c87ada51d34d70c163aff27120b53bde964a27fdd507066ecde304ad659f?inline=true`
[View all 9 images in article →](https://help.zoho.com/portal/en/kb/crm/assignment-threshold)

**[Assigning Record Owner](https://help.zoho.com/portal/en/kb/crm/assigning-record-owner)** — 6 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57676e8e7e07c8b665db83e1564e1ef5ba9efb55db00f66961c69ab49912ba21d55ed012676e1ad2c68963b5c66d94ac27?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57670bc7d23fbfcee6f2ba8c53df7121427f9e651151ce485c502878ab8c90a7cc1c41c180b38615fc4051784eafe2b9db?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574cd1a6504664e7654998d640ff2dbf882213c627994270b88fd9bf15eec2365e7015ade669d3acff2603bf5b1fe7a23a?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571826c1ed739df0d69d55e24dcab71645d7146d6e9517abf4d888df0f85800f5353f8b668e3bab2d4f861d2dcbc17ad15?inline=true`
[View all 6 images in article →](https://help.zoho.com/portal/en/kb/crm/assigning-record-owner)

**[Decision Guide for Territory Management](https://help.zoho.com/portal/en/kb/crm/territory-decision-management)** — 5 images
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqz8f65ab5590a848178acef6764df8e901`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqze121b1bd9c5d4e38b40be35e892d72d0`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqz098d74bdc38041e297acf1040a4faf83`
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqzcb5221a124434ee1ad36143d1903d5cd`
[View all 5 images in article →](https://help.zoho.com/portal/en/kb/crm/territory-decision-management)

**[Assignment Threshold in Zoho CRM iOS](https://help.zoho.com/portal/en/kb/crm/assignment-threshold-in-zoho-crm-ios)** — 5 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5730e7525d7e44f4498cae6e2ee5992ed30f702b4dcdd61b2d52fa44e26df2c951f2b27a29cc7c03fc642d9b857f0bc8cd?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b572aa4741348fd83c74421480a35b2a040db7460a2a147c4687e5cdbd22481192b24134e564aa1d8d31c62d4b958f8ea12?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5751d1f49c77e4c411b242424b753e7ce4e68ba4d611a930de87d7d51fc182769aff41541874b53f329a2f4314c506bef8?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57dd5c96d5d212eef2a5fdb6695e4ededfa6fd98a8fcc2b29231ac9212ddc3097812854f2cfb5977d1e24c67c293cf257e?inline=true`
[View all 5 images in article →](https://help.zoho.com/portal/en/kb/crm/assignment-threshold-in-zoho-crm-ios)

