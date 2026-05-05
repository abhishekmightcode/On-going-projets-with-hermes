# Canvas Design Studio

> **Feature ID:** `21-CRM-Canvas-UI`  
> **Knowledge Base Articles:** 18  
> **Last Updated:** 2026-05-05

## Overview

Canvas design studio, homepage customization, record detail pages, mobile customization

---

## 1. Core Functionality

### 1. Support Access for Zoho CRM

Support access is a secure method of granting a developer or tech support agent temporary access to your Zoho CRM account so that they can diagnose and troubleshoot issues. Support team members with certain roles can thereby access your Zoho CRM account and address problems directly. Providing access To provide account access to the Zoho CRM support team, go to Setup[ ]> Security Control > Support Access. Inside the support access page, provide a date. The support team have access to your account until the selected date, starting at the time you activate it. You can provide support access for a minimum of one day. The support team will be able to access the account with admin permissions after you authorize their access, subject to some limitations. A tech support agent will be added to th
### 2. Best Time to Contact Customers

We often hear telecallers asking, "Is this the right time to talk?". Though most of the times our response is not affirmative, have you wondered why is it important for them to know whether it is the right time to contact? Because, oftentimes approaching a customer at an inappropriate time can cost a lot more than just a lost deal, it sometimes sours the customer's experience with your company. Unlike the telecallers, a sales person doesn't get an opportunity to ask the customer if it's the right time to chat with them or send an email. Zia's best time to contact can make their job a lot easier by auto suggesting the suitable time to contact for every customer. Availability Permission Required Available for all the users. How Zia computes the best time? Zia can suggest the best time to con
### 3. Customizing Module View Using the all-new Canvas design suite

Businesses and data are cohesive entities that exist and grow together. The more people you meet and transactions you make, the more information you're going to accumulate in your database—so it's important to keep your growing database clean and accessible. Zoho CRM offers many types of module views so you can organize data based on your requirements. Read this article to learn more about module views. The Canvas view is a dynamic orientation of your records created using our bespoke Canvas builder. You can incorporate different graphic and design elements to your records in module view to suit your brand guidelines and ad hoc accessibility. It offers customization in three layouts— custom list view, tile view, and table view —to sculpt your view according to your data type. Query: Allows
### 4. Saving a Blueprint as a Draft

It so happens that sometimes you are not ready to deploy your final Blueprint into CRM yet, and you need to put some more thought into the process flow. When you publish a Blueprint, you will begin having records entering it - so it's not a good idea to deploy it before it's ready. In this case, you can save a Blueprint as a DRAFT. You can play around with your States and Transitions in the DRAFT version, and once you are satisfied with the final process flow, you can PUBLISH your draft. Note that the draft version is not a testing environment, rather a canvas of sorts, for you to test your process flow. You cannot test the execution of a Blueprint with the draft version - for now, it's only meant for you to play around with the process flow. At a given point in time, you can have one " Pu
### 5. Blueprint: A Glossary of Terms

State State refers to each stage in your business process - that is, all the values of the chosen pick-list field. Drag and drop each State in the canvas on your left to begin drawing your Blueprint. Example States : Picklist Values of the Deal Stage field. Qualification Requirement Gathering Product Demo Legal Review Closed Won Closed Lost Closed Lost to Competition Transition A Transition is a link between two States in a process. It prescribes the conditions required for a record to move from one State to another. Each Transition you configure is displayed as a button on the record's details page. To complete a Transition, click on the Transition button and execute the actions mentioned in the ensuing popup window. On successful completion of the Transition, you will move to the next St
### 6. Kaizen posts 2026: Other Developer Tools

Here is a complete list of Kaizen posts published in 2026, on developer tools other than APIs, SDKs, Functions and Client Scripts. Sl. No. Title Description 1 Making Query-based Custom Related Lists Actionable with Lookups and Links Learn how to enhance query-based custom related lists in Zoho CRM by adding clickable lookup fields and links in serializer for better navigation and usability. 2 Process Large-Scale Migrated Data Using Catalyst Solutions Learn how Catalyst Solutions enable large-scale processing of migrated data in Zoho CRM beyond standard imports. 3 Fetching Employee Data from Microsoft SQL Server into Zoho CRM Using Queries Learn how to connect Zoho CRM Queries to a Microsoft SQL Server database, write a parameterized SELECT query to fetch employee records, and display them 
### 7. Canvas Record Form

Overview Canvas Record Form enriches Zoho CRM by introducing an advanced level of customization for record creation. This integral part of the Canvas design suite enables users to design forms that are not only functionally comprehensive but also visually aligned with their brand identity and operational workflows. It shifts the paradigm from simple data management to creating a more engaging, intuitive CRM experience. This feature facilitates the integration of brand elements and operational nuances directly into CRM forms, making Zoho CRM a more adaptable and visually cohesive tool for businesses. The value of customization The advent of Canvas Record Form addresses the previously rigid nature of record creation within Zoho CRM. Traditional limitations in form design often resulted in a 
### 8. Kaizen posts 2025: Widget series

Here is a complete list of Kaizen posts related to Widgets published in 2025 . Sl. No. Title Description 1 Leverage Settings Widget for Zoho CRM Extensions Learn how to configure a Settings Widget for your Zoho CRM extension to enable key configurations and enhance user experience. 2 Mandating Subform Data for Blueprint Transitions using Widget Explore how to enforce custom subform data from a different module for a blueprint transition. 3 Building a Timer and Worklog Widget (Part 1) Learn how to build a Timer and Worklog Widget to track active work time and log multitasking sessions. 4 Building a Timer and Worklog Widget (Part 2) Learn how to auto sync data from a module to subform using workflow rule and functions in Zoho CRM. 5 Answering Your Questions | Testing and Using REST APIs in W


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `CRM`

**Standard Fields (inherited):**
- `Created_By` (User) — Record creator
- `Modified_By` (User) — Last modifier
- `Created_Time` (DateTime) — Creation timestamp
- `Modified_Time` (DateTime) — Last modification
- `Owner` (User) — Record owner for access control

**Key Articles:**
- `Support Access for Zoho CRM`
- `Best Time to Contact Customers`
- `Customizing Module View Using the all-new Canvas design suite`
- `Saving a Blueprint as a Draft`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/crm` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Canvas Design Studio - Example Implementation
// Triggered on record creation/update

if(input.module == "SUPPORT ACCESS FOR ZOHO CRM")
{
    // Support access is a secure method of granting a developer or tech support agent temporary access to your Zoho CRM account so that they can diagnose an
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

- [Customization-Builder](../Customization-Builder/README.md)
- [Modules-Data-Model](../Modules-Data-Model/README.md)

### This Feature Enables

- **Customization-Builder** — shares data model and workflows
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

### Support Access for Zoho CRM
**Purpose:** Support access is a secure method of granting a developer or tech support agent temporary access to your Zoho CRM account so that they can diagnose and troubleshoot issues. Support team members with c

**Key Points:**
- Support access is a secure method of granting a developer or tech support agent temporary access to your Zoho CRM account so that they can diagnose and troubleshoot issues.
- Support team members with certain roles can thereby access your Zoho CRM account and address problems directly.
- Providing access To provide account access to the Zoho CRM support team, go to Setup[ ]> Security Control > Support Access.
- Inside the support access page, provide a date.
- The support team have access to your accoun


### Best Time to Contact Customers
**Purpose:** We often hear telecallers asking, "Is this the right time to talk?". Though most of the times our response is not affirmative, have you wondered why is it important for them to know whether it is the 

**Key Points:**
- We often hear telecallers asking, "Is this the right time to talk?".
- Though most of the times our response is not affirmative, have you wondered why is it important for them to know whether it is the right time to contact? Because, oftentimes approaching a customer at an inappropriate time can cost a lot more than just a lost deal, it sometimes sours the customer's experience with your company.
- Unlike the telecallers, a sales person doesn't get an opportunity to ask the customer if it's the righ


### Customizing Module View Using the all-new Canvas design suite
**Purpose:** Businesses and data are cohesive entities that exist and grow together. The more people you meet and transactions you make, the more information you're going to accumulate in your database—so it's imp

**Key Points:**
- Businesses and data are cohesive entities that exist and grow together.
- The more people you meet and transactions you make, the more information you're going to accumulate in your database—so it's important to keep your growing database clean and accessible.
- Zoho CRM offers many types of module views so you can organize data based on your requirements.
- Read this article to learn more about module views.
- The Canvas view is a dynamic orientation of your records created using our bespoke Canvas bui


### Saving a Blueprint as a Draft
**Purpose:** It so happens that sometimes you are not ready to deploy your final Blueprint into CRM yet, and you need to put some more thought into the process flow. When you publish a Blueprint, you will begin ha

**Key Points:**
- It so happens that sometimes you are not ready to deploy your final Blueprint into CRM yet, and you need to put some more thought into the process flow.
- When you publish a Blueprint, you will begin having records entering it - so it's not a good idea to deploy it before it's ready.
- In this case, you can save a Blueprint as a DRAFT.
- You can play around with your States and Transitions in the DRAFT version, and once you are satisfied with the final process flow, you can PUBLISH your draft


### Blueprint: A Glossary of Terms
**Purpose:** State State refers to each stage in your business process - that is, all the values of the chosen pick-list field. Drag and drop each State in the canvas on your left to begin drawing your Blueprint. 

**Key Points:**
- State State refers to each stage in your business process - that is, all the values of the chosen pick-list field.
- Drag and drop each State in the canvas on your left to begin drawing your Blueprint.
- Example States : Picklist Values of the Deal Stage field.
- Qualification Requirement Gathering Product Demo Legal Review Closed Won Closed Lost Closed Lost to Competition Transition A Transition is a link between two States in a process.
- It prescribes the conditions required for a record to move from


### Kaizen posts 2026: Other Developer Tools
**Purpose:** Here is a complete list of Kaizen posts published in 2026, on developer tools other than APIs, SDKs, Functions and Client Scripts. Sl. No. Title Description 1 Making Query-based Custom Related Lists A

**Key Points:**
- Here is a complete list of Kaizen posts published in 2026, on developer tools other than APIs, SDKs, Functions and Client Scripts.
- Title Description 1 Making Query-based Custom Related Lists Actionable with Lookups and Links Learn how to enhance query-based custom related lists in Zoho CRM by adding clickable lookup fields and links in serializer for better navigation and usability.
- 2 Process Large-Scale Migrated Data Using Catalyst Solutions Learn how Catalyst Solutions enable large-sca


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

- [Support Access for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/support-access)
- [Best Time to Contact Customers](https://help.zoho.com/portal/en/kb/crm/articles/using-best-time-to-contact)
- [Customizing Module View Using the all-new Canvas design suite](https://help.zoho.com/portal/en/kb/crm/articles/customizing-module-view-using-the-all-new-canvas-design-suite)
- [Saving a Blueprint as a Draft](https://help.zoho.com/portal/en/kb/crm/articles/save-blueprint)
- [Blueprint: A Glossary of Terms](https://help.zoho.com/portal/en/kb/crm/articles/blueprint-glossary-terms)
- [Kaizen posts 2026: Other Developer Tools](https://help.zoho.com/portal/en/kb/crm/articles/other-developer-tools-2026)
- [Canvas Record Form](https://help.zoho.com/portal/en/kb/crm/articles/canvas-record-form)
- [Kaizen posts 2025: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2025)
- [Color Coding of Picklist Values](https://help.zoho.com/portal/en/kb/crm/articles/color-coding-of-picklist-values)
- [Open Activities Homepage Component](https://help.zoho.com/portal/en/kb/crm/articles/open-activities-homepage-component)
- [Canvas in sandbox](https://help.zoho.com/portal/en/kb/crm/articles/canvas-in-sandbox)
- [Requester roles for coordination between teams](https://help.zoho.com/portal/en/kb/crm/articles/requester-roles-for-coordination-between-teams)
- [Customizing Record Detail Page Using Canvas](https://help.zoho.com/portal/en/kb/crm/articles/customize-record-detail-page-canvas)
- [Customizing mobile record detail page using Canvas](https://help.zoho.com/portal/en/kb/crm/articles/customizing-mobile-record-detail-page-using-canvas)
- [Organizing the homepage in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/articles/organizing-the-homepage-in-zoho-crm-ios-app)
- [Calendar Booking](https://help.zoho.com/portal/en/kb/crm/articles/calendar-booking)
- [Create a Homepage using Home View in Canvas](https://help.zoho.com/portal/en/kb/crm/articles/create-a-homepage-using-home-view-in-canvas)
- [Kaizen posts 2026: Client Script series](https://help.zoho.com/portal/en/kb/crm/articles/client-script-2026)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
