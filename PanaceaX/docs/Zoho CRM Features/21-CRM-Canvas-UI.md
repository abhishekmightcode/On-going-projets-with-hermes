# Canvas Design Studio

> **Feature ID:** `21-CRM-Canvas-UI`  
> **Knowledge Base Articles:** 36  
> **Last Updated:** 2026-05-05

## Overview

Canvas design studio, homepage customization, record detail pages, mobile customization

---

## 1. Core Functionality

### 1. FAQs : CRM Onboarding

How do I know which Zoho CRM Edition I am using? You can find out which Zoho CRM edition you are using by clicking the Profile icon on the top right corner of your window. The edition will be displayed next to Subscription. How can I delete my Zoho CRM account? There are multiple stages in deleting a Zoho CRM account. To delete individual users with the CRM account, you can follow these steps to delete them from Zoho CRM: 1. Click Setup > General > Users. 2. Click the user you want to delete. 3. Click the Delete This User button at the bottom of the User Details section. 4. You will see a dial
### 2. Support Access for Zoho CRM

Support access is a secure method of granting a developer or tech support agent temporary access to your Zoho CRM account so that they can diagnose and troubleshoot issues. Support team members with certain roles can thereby access your Zoho CRM account and address problems directly. Providing access To provide account access to the Zoho CRM support team, go to Setup[ ]> Security Control > Support Access. Inside the support access page, provide a date. The support team have access to your account until the selected date, starting at the time you activate it. You can provide support access for
### 3. Best Time to Contact Customers

We often hear telecallers asking, "Is this the right time to talk?". Though most of the times our response is not affirmative, have you wondered why is it important for them to know whether it is the right time to contact? Because, oftentimes approaching a customer at an inappropriate time can cost a lot more than just a lost deal, it sometimes sours the customer's experience with your company. Unlike the telecallers, a sales person doesn't get an opportunity to ask the customer if it's the right time to chat with them or send an email. Zia's best time to contact can make their job a lot easie
### 4. Customizing Module View Using the all-new Canvas design suite

Businesses and data are cohesive entities that exist and grow together. The more people you meet and transactions you make, the more information you're going to accumulate in your database—so it's important to keep your growing database clean and accessible. Zoho CRM offers many types of module views so you can organize data based on your requirements. Read this article to learn more about module views. The Canvas view is a dynamic orientation of your records created using our bespoke Canvas builder. You can incorporate different graphic and design elements to your records in module view to su
### 5. Setting up Zoho Cliq Integration

When your manager wants to have a word with you regarding a potential customer and the possibility of winning a deal, you may not always prefer to sit in a conference room and discuss the details. When you want to give a quick update about the latest developments in organizing a user conference, having a meeting might seem best. However, it would take up your valuable time in booking meeting rooms, notifying others, and making the necessary arrangements for the meeting. Zoho CRM and Cliq teams up to give you the option to be where you are and attend these discussions. It would definitely be a
### 6. Organizing your home page in Zoho CRM Android app

Your homepage acts as a progress tracker bringing together all the important details you need, such as meetings, deals, leads, and more. Even though the mobile screen has limited space, you can drill down into each component you have added, such as dashboards, widgets, or custom views, to see more details. Types of homepages supported in the app Classic view This is a system-defined homepage that cannot be customized. In the mobile app, the Classic view includes three components: My Open Tasks My Meetings Today Amount by Stage. “ My Today’s Open Tasks ” component will be supported in the futur
### 7. Kaizen posts 2024: Client Script series

Here is a complete list of Kaizen posts related to Client Scripts published in 2024 . Sl. No. Title Description 1 Customize List Views using Client Script Learn how to customize visibility of list views. 2 Client Script Support for Blueprints Learn how to use Client Script to get non-mandatory pop-up. 3 Third Party Integration using Client Script Learn how to populate value in a field based on the response from third party API. 4 Using Functions in Client Script and Handling Timeouts. Lean how to invoke Functions in Client Script and how to handle Timeouts 5 How to Navigate to Another Page in
### 8. FAQs : Macros

What are macros? Macros are a set of actions that can be executed for a group of records in a module. These sets of actions include sending emails, creating tasks, and updating a field in the records with a specified value. You may have a set of actions that you perform on a daily basis or frequently for some records. You can combine all of these actions into a single macro and perform them again and again. Suppose you are required to call up a fresh set of leads everyday. Once you are done with the call, you need to send them a standard email and update the lead status to "Contacted". After t


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `CRM`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `FAQs : CRM Onboarding`
- `Support Access for Zoho CRM`
- `Best Time to Contact Customers`
- `Customizing Module View Using the all-new Canvas design suite`

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

if(input.module == "FAQS : CRM ONBOARDING")
{
    // How do I know which Zoho CRM Edition I am using? You can find out which Zoho CRM edition you are using by clicking the Profile icon on the top right c
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

- **Customization-Builder** -- shares data model and workflows
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

### FAQs : CRM Onboarding
**Purpose:** How do I know which Zoho CRM Edition I am using? You can find out which Zoho CRM edition you are using by clicking the Profile icon on the top right corner of your window. The edition will be displaye

**Key Points:**
How do I know which Zoho CRM Edition I am using.
You can find out which Zoho CRM edition you are using by clicking the Profile icon on the top right corner of your window.
The edition will be displayed next to Subscription.
How can I delete my Zoho CRM account.
There are multiple stages in deleting a Zoho CRM account.
To delete individual users with the CRM account, you can follow these steps to delete them from Zoho CRM: 1


### Support Access for Zoho CRM
**Purpose:** Support access is a secure method of granting a developer or tech support agent temporary access to your Zoho CRM account so that they can diagnose and troubleshoot issues. Support team members with c

**Key Points:**
Support access is a secure method of granting a developer or tech support agent temporary access to your Zoho CRM account so that they can diagnose and troubleshoot issues.
Support team members with certain roles can thereby access your Zoho CRM account and address problems directly.
Providing access To provide account access to the Zoho CRM support team, go to Setup[ ]> Security Control > Support Access.
Inside the support access page, provide a date.
The support team have access to your account until the selected date, starting at the time you activate it.
You can provide support access for a minimum of one day


### Best Time to Contact Customers
**Purpose:** We often hear telecallers asking, "Is this the right time to talk?". Though most of the times our response is not affirmative, have you wondered why is it important for them to know whether it is the

**Key Points:**
We often hear telecallers asking, "Is this the right time to talk.
Though most of the times our response is not affirmative, have you wondered why is it important for them to know whether it is the right time to contact.
Because, oftentimes approaching a customer at an inappropriate time can cost a lot more than just a lost deal, it sometimes sours the customer's experience with your company.
Unlike the telecallers, a sales person doesn't get an opportunity to ask the customer if it's the right time to chat with them or send an email.
Zia's best time to contact can make their job a lot easier by auto suggesting the suitable time to contact for every customer.
Availability Permission Required Available for all the users


### Customizing Module View Using the all-new Canvas design suite
**Purpose:** Businesses and data are cohesive entities that exist and grow together. The more people you meet and transactions you make, the more information you're going to accumulate in your database—so it's imp

**Key Points:**
Businesses and data are cohesive entities that exist and grow together.
The more people you meet and transactions you make, the more information you're going to accumulate in your database—so it's important to keep your growing database clean and accessible.
Zoho CRM offers many types of module views so you can organize data based on your requirements.
Read this article to learn more about module views.
The Canvas view is a dynamic orientation of your records created using our bespoke Canvas builder.
You can incorporate different graphic and design elements to your records in module view to suit your brand guidelines and ad hoc accessibility


### Setting up Zoho Cliq Integration
**Purpose:** When your manager wants to have a word with you regarding a potential customer and the possibility of winning a deal, you may not always prefer to sit in a conference room and discuss the details. Whe

**Key Points:**
When your manager wants to have a word with you regarding a potential customer and the possibility of winning a deal, you may not always prefer to sit in a conference room and discuss the details.
When you want to give a quick update about the latest developments in organizing a user conference, having a meeting might seem best.
However, it would take up your valuable time in booking meeting rooms, notifying others, and making the necessary arrangements for the meeting.
Zoho CRM and Cliq teams up to give you the option to be where you are and attend these discussions.
It would definitely be a time saver.
So the next time you want to get an update on a deal, you need not send an email or book a meeting room


### Organizing your home page in Zoho CRM Android app
**Purpose:** Your homepage acts as a progress tracker bringing together all the important details you need, such as meetings, deals, leads, and more. Even though the mobile screen has limited space, you can drill

**Key Points:**
Your homepage acts as a progress tracker bringing together all the important details you need, such as meetings, deals, leads, and more.
Even though the mobile screen has limited space, you can drill down into each component you have added, such as dashboards, widgets, or custom views, to see more details.
Types of homepages supported in the app Classic view This is a system-defined homepage that cannot be customized.
In the mobile app, the Classic view includes three components: My Open Tasks My Meetings Today Amount by Stage.
“ My Today’s Open Tasks ” component will be supported in the future updates.
User's home page This is a personalized homepage where you can access the components you’ve added in Zoho CRM web


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

- [FAQs : CRM Onboarding](https://help.zoho.com/portal/en/kb/crm/articles/faqs-crm-onboarding)
- [Support Access for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/support-access)
- [Best Time to Contact Customers](https://help.zoho.com/portal/en/kb/crm/articles/using-best-time-to-contact)
- [Customizing Module View Using the all-new Canvas design suite](https://help.zoho.com/portal/en/kb/crm/articles/customizing-module-view-using-the-all-new-canvas-design-suite)
- [Setting up Zoho Cliq Integration](https://help.zoho.com/portal/en/kb/crm/articles/zoho-cliq-crm-integration)
- [Organizing your home page in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/organizing-your-home-page-in-zoho-crm-android-app)
- [Kaizen posts 2024: Client Script series](https://help.zoho.com/portal/en/kb/crm/articles/client-script-2024)
- [FAQs : Macros](https://help.zoho.com/portal/en/kb/crm/articles/faqs-macros)
- [FAQs: Users settings](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-users-settings)
- [Saving a Blueprint as a Draft](https://help.zoho.com/portal/en/kb/crm/articles/save-blueprint)
- [Blueprint: A Glossary of Terms](https://help.zoho.com/portal/en/kb/crm/articles/blueprint-glossary-terms)
- [Kaizen posts 2026: Other Developer Tools](https://help.zoho.com/portal/en/kb/crm/articles/other-developer-tools-2026)
- [Customizing Home Tab](https://help.zoho.com/portal/en/kb/crm/articles/customize-home-tab)
- [FAQ: Grid View in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/faq-grid-view-in-zoho-crm)
- [Working with Zoho Desk Integration](https://help.zoho.com/portal/en/kb/crm/articles/zoho-desk-crm-integration)
- [Transitioning to the Improved Zoho CRM for Everyone Interface](https://help.zoho.com/portal/en/kb/crm/articles/transitioning-to-the-improved-zoho-crm-for-everyone-interface)
- [Kaizen posts 2025: Queries series](https://help.zoho.com/portal/en/kb/crm/articles/kaizen-posts-2025-queries-series)
- [Canvas Record Form](https://help.zoho.com/portal/en/kb/crm/articles/canvas-record-form)
- [Kaizen posts 2025: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2025)
- [Color Coding of Picklist Values](https://help.zoho.com/portal/en/kb/crm/articles/color-coding-of-picklist-values)
- [Kiosk Studio - An overview](https://help.zoho.com/portal/en/kb/crm/articles/kiosk-an-overview)
- [Open Activities Homepage Component](https://help.zoho.com/portal/en/kb/crm/articles/open-activities-homepage-component)
- [Channels: an Overview](https://help.zoho.com/portal/en/kb/crm/articles/channels-overview)
- [Canvas in sandbox](https://help.zoho.com/portal/en/kb/crm/articles/canvas-in-sandbox)
- [Requester roles for coordination between teams](https://help.zoho.com/portal/en/kb/crm/articles/requester-roles-for-coordination-between-teams)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
