# Settings & Configuration

> **Feature ID:** `30-Settings-Configuration`  
> **Knowledge Base Articles:** 18  
> **Last Updated:** 2026-05-05

## Overview

Organization settings, email sharing, macros, global sets, and administrative configuration

---

## 1. Core Functionality

### 1. Adding Team Users

Editions : Standard, Professional, Enterprise, Ultimate, CRM Plus DC : All Pricing : $ 9 / team license / month (if paid yearly ) $ 11 / team license/ month (if paid monthly ) Related profile permission Users with the User Management > Manage Users permission in their profile can purchase and add team users. Team users will have a system-defined Team User profile that is lightly customizable. Required Actions For CRMPlus users, you need to enable the team user option at the bottom from General < Company Settings < Company Details. CRM for everyone allows multiple teams to collaborate quickly and effectively while sharing the same context. Members of non-sales teams may not require the same level of data access and capabilities to complete their tasks in the CRM. For instance, a sales devel
### 2. Setting up Email Sharing Permissions

Emails exchanged with customers contain important information that may be required for reference by several other teams who are involved in the business process. For example, a contract agreement exchanged with a firm may be required by the legal team to prepare a partnership agreement. Likewise, the negotiation details discussed in email may be required by the payments team to prepare the invoice. There are multiple such instances when a customer's email needs to be accessible to more than one person within the organization. To facilitate easy access of emails, Zoho CRM provides email sharing options. CRM administrators have the privilege to set email sharing options for individual users or specific roles. They can also give users the option to set their own email sharing permissions. The
### 3. Use macros auto-suggested by Zoho CRM

Zoho CRM takes the usage of macros a notch higher by intelligently auto-suggesting macros that you could create based on your CRM activities. If you have been repeatedly performing the same set of actions over a period time on a bunch of records, Zoho CRM will automatically suggest that you create macros out of the actions. Consider the following scenario, in which the same set of actions are being performed thrice over a period of 10 days. Day 1: You send a Welcome Email template to a set of leads under "Today's Leads" custom view and then update the Lead Status field to Contacted . Day 3: You send the same Welcome Email to another set of leads under "Today's Leads" custom view and then update the Lead Status field to Contacted . Day 8: When you repeat this action for the third consecutiv
### 4. Email configuration for Microsoft Graph API

Users can integrate their mailbox with Zoho CRM securely to bring email conversations into the context of customer records. Users of Outlook/ Office 365 email accounts can use our dedicated Graph API integration to get a modern, secure, and future-proof email experience. Microsoft Graph API makes it easy to access data securely from across Microsoft’s cloud ecosystem. Using this option sets you up to access even smarter, faster, and more connected experiences in the future. Learn more about Graph API Note : In addition to Graph API, Outlook/ Office 365 users can use the IMAP and POP options to integrate their email accounts. To learn more, see Email configuration for IMAP and POP3 . This document will explain how to integrate your inbox using Graph API. Connect your email inbox using Graph
### 5. Using and Creating Macros

Macros are a set of actions that can be executed for a group of records in a module. These sets of actions include sending emails, creating tasks, and updating a field in the records with a specified value . You may have a set of actions that you perform on a daily basis or frequently to some records. You can combine all these actions in a single macro and perform them again and again. Take for example, the following two scenarios and how using macros makes the job easier. Scenario 1 - You are a field sales executive and some leads are assigned to you. Your job is to meet the leads and try to sell them your product. After contacting them, you perform the following set of actions: Send a follow up email. Update the Status field as '1st Follow-up Initiated'. Create a task for the other sales
### 6. Working with global sets

Global sets in Zoho CRM help you easily manage picklist values that recur across modules. For an overview of this feature, see Overview of global sets . Where can I find global sets? Users with the requisite permissions in their profiles will be able to access global sets at Setup[ ] > Customization > Modules and Fields > Global Sets . The following features are available in your Global Sets tab: Search : Use this function to search your global sets by name. Create Global Set : Use this button to create a new global set. Global Set master list : Use this to manage all your global sets. You will also be able to see useful details like the following: Modules in which a global set is being used The user who created a global set The time at which a global set was created The user who last modi
### 7. Zia Suggestions for Assignment Rules

Businesses spend a lot of money, time, and effort to bring leads into the sales funnel. Despite those efforts, research shows that about 24% of U.S. companies take about 24 hours on average to make their first move toward a lead—just enough time to turn those onboarded leads cold. There could be any number of reasons for this tardiness, like a shortage of employees, overloaded sales reps, or inefficient process management, but as we examine these causes, we find that the underlying problem is always about record ownership —either the lack of it or inaccuracy in it. Record ownership is an important determinant of successful lead turnover in a business. That's the first step, in fact. To whom is a lead assigned? Is that record relevant to the sales rep's territory? Does it match the rep's sk
### 8. Set up your Organization Account

As an administrator your first step towards implementing Zoho CRM for your organization will involve entering details in the personal settings and defining the organization details, which will be visible to all users across the departments. You will also need to define the email settings in your CRM account and configure Motivator to keep your team members motivated by giving timely rewards and perks. Personal Settings First, personalize your CRM account by changing language and time zone. Then, you can set other personal preferences like date format, time format, number format, and so on. You can also set up accessibility controls to make the CRM experience work for you. Organization Settings Company details: Add your company details such as the company name for all your business communic


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `SETTINGS`

**Standard Fields (inherited):**
- `Created_By` (User) — Record creator
- `Modified_By` (User) — Last modifier
- `Created_Time` (DateTime) — Creation timestamp
- `Modified_Time` (DateTime) — Last modification
- `Owner` (User) — Record owner for access control

**Key Articles:**
- `Adding Team Users`
- `Setting up Email Sharing Permissions`
- `Use macros auto-suggested by Zoho CRM`
- `Email configuration for Microsoft Graph API`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/settings` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Settings & Configuration - Example Implementation
// Triggered on record creation/update

if(input.module == "ADDING TEAM USERS")
{
    // Editions : Standard, Professional, Enterprise, Ultimate, CRM Plus DC : All Pricing : $ 9 / team license / month (if paid yearly ) $ 11 / team license/
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

- [Security-Admin](../Security-Admin/README.md)
- [Email-Tools](../Email-Tools/README.md)
- [Workflow-Automation](../Workflow-Automation/README.md)

### This Feature Enables

- **Security-Admin** — shares data model and workflows
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

### Adding Team Users
**Purpose:** Editions : Standard, Professional, Enterprise, Ultimate, CRM Plus DC : All Pricing : $ 9 / team license / month (if paid yearly ) $ 11 / team license/ month (if paid monthly ) Related profile permissi

**Key Points:**
- Editions : Standard, Professional, Enterprise, Ultimate, CRM Plus DC : All Pricing : $ 9 / team license / month (if paid yearly ) $ 11 / team license/ month (if paid monthly ) Related profile permission Users with the User Management > Manage Users permission in their profile can purchase and add team users.
- Team users will have a system-defined Team User profile that is lightly customizable.
- Required Actions For CRMPlus users, you need to enable the team user option at the bottom from General <


### Setting up Email Sharing Permissions
**Purpose:** Emails exchanged with customers contain important information that may be required for reference by several other teams who are involved in the business process. For example, a contract agreement exch

**Key Points:**
- Emails exchanged with customers contain important information that may be required for reference by several other teams who are involved in the business process.
- For example, a contract agreement exchanged with a firm may be required by the legal team to prepare a partnership agreement.
- Likewise, the negotiation details discussed in email may be required by the payments team to prepare the invoice.
- There are multiple such instances when a customer's email needs to be accessible to more than one


### Use macros auto-suggested by Zoho CRM
**Purpose:** Zoho CRM takes the usage of macros a notch higher by intelligently auto-suggesting macros that you could create based on your CRM activities. If you have been repeatedly performing the same set of act

**Key Points:**
- Zoho CRM takes the usage of macros a notch higher by intelligently auto-suggesting macros that you could create based on your CRM activities.
- If you have been repeatedly performing the same set of actions over a period time on a bunch of records, Zoho CRM will automatically suggest that you create macros out of the actions.
- Consider the following scenario, in which the same set of actions are being performed thrice over a period of 10 days.
- Day 1: You send a Welcome Email template to a set of le


### Email configuration for Microsoft Graph API
**Purpose:** Users can integrate their mailbox with Zoho CRM securely to bring email conversations into the context of customer records. Users of Outlook/ Office 365 email accounts can use our dedicated Graph API 

**Key Points:**
- Users can integrate their mailbox with Zoho CRM securely to bring email conversations into the context of customer records.
- Users of Outlook/ Office 365 email accounts can use our dedicated Graph API integration to get a modern, secure, and future-proof email experience.
- Microsoft Graph API makes it easy to access data securely from across Microsoft’s cloud ecosystem.
- Using this option sets you up to access even smarter, faster, and more connected experiences in the future.
- Learn more about Grap


### Using and Creating Macros
**Purpose:** Macros are a set of actions that can be executed for a group of records in a module. These sets of actions include sending emails, creating tasks, and updating a field in the records with a specified 

**Key Points:**
- Macros are a set of actions that can be executed for a group of records in a module.
- These sets of actions include sending emails, creating tasks, and updating a field in the records with a specified value.
- You may have a set of actions that you perform on a daily basis or frequently to some records.
- You can combine all these actions in a single macro and perform them again and again.
- Take for example, the following two scenarios and how using macros makes the job easier.
- Scenario 1 - You are a


### Working with global sets
**Purpose:** Global sets in Zoho CRM help you easily manage picklist values that recur across modules. For an overview of this feature, see Overview of global sets . Where can I find global sets? Users with the re

**Key Points:**
- Global sets in Zoho CRM help you easily manage picklist values that recur across modules.
- For an overview of this feature, see Overview of global sets.
- Where can I find global sets? Users with the requisite permissions in their profiles will be able to access global sets at Setup[ ] > Customization > Modules and Fields > Global Sets.
- The following features are available in your Global Sets tab: Search : Use this function to search your global sets by name.
- Create Global Set : Use this button t


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

- [Adding Team Users](https://help.zoho.com/portal/en/kb/crm/articles/adding-team-users)
- [Setting up Email Sharing Permissions](https://help.zoho.com/portal/en/kb/crm/articles/setting-up-email-sharing-permissions)
- [Use macros auto-suggested by Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/auto-suggested-macros)
- [Email configuration for Microsoft Graph API](https://help.zoho.com/portal/en/kb/crm/articles/email-configuration-for-microsoft-graph-api)
- [Using and Creating Macros](https://help.zoho.com/portal/en/kb/crm/articles/using-macros)
- [Working with global sets](https://help.zoho.com/portal/en/kb/crm/articles/working-with-global-sets)
- [Zia Suggestions for Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/record-owner-suggestion-in-assignment-rule)
- [Set up your Organization Account](https://help.zoho.com/portal/en/kb/crm/articles/get-started-setup-organization-account)
- [Overview of global sets](https://help.zoho.com/portal/en/kb/crm/articles/overview-of-global-sets)
- [FAQs:  Zoho User ID, User IDs and Org IDs in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/faqs-zoho-user-id-user-ids-and-org-ids-in-zoho-crm-9-4-2026)
- [Running and Deleting Macros](https://help.zoho.com/portal/en/kb/crm/articles/run-macros)
- [Manage Company Settings](https://help.zoho.com/portal/en/kb/crm/articles/manage-company-details)
- [Setting up organization details](https://help.zoho.com/portal/en/kb/crm/articles/set-up-org-details)
- [Layout Rule Exceptions](https://help.zoho.com/portal/en/kb/crm/articles/layout-rule-exception)
- [Manage Business Hours](https://help.zoho.com/portal/en/kb/crm/articles/business-hours)
- [Search Records](https://help.zoho.com/portal/en/kb/crm/articles/search-records)
- [How to use Zoho CRM's knowledge base](https://help.zoho.com/portal/en/kb/crm/articles/how-to-use-zoho-crm-s-knowledge-base)
- [Setting Email Preferences](https://help.zoho.com/portal/en/kb/crm/articles/setting-email-preferences)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
