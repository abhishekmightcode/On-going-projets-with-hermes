# Settings & Configuration

> **Feature ID:** `30-Settings-Configuration`  
> **Knowledge Base Articles:** 32  
> **Last Updated:** 2026-05-05

## Overview

Organization settings, email sharing, macros, global sets, and administrative configuration

---

## 1. Core Functionality

### 1. Adding Team Users

Editions : Standard, Professional, Enterprise, Ultimate, CRM Plus DC : All Pricing : $ 9 / team license / month (if paid yearly ) $ 11 / team license/ month (if paid monthly ) Related profile permission Users with the User Management > Manage Users permission in their profile can purchase and add team users. Team users will have a system-defined Team User profile that is lightly customizable. Required Actions For CRMPlus users, you need to enable the team user option at the bottom from General < Company Settings < Company Details. CRM for everyone allows multiple teams to collaborate quickly a
### 2. Setting up Email Sharing Permissions

Emails exchanged with customers contain important information that may be required for reference by several other teams who are involved in the business process. For example, a contract agreement exchanged with a firm may be required by the legal team to prepare a partnership agreement. Likewise, the negotiation details discussed in email may be required by the payments team to prepare the invoice. There are multiple such instances when a customer's email needs to be accessible to more than one person within the organization. To facilitate easy access of emails, Zoho CRM provides email sharing
### 3. Use macros auto-suggested by Zoho CRM

Zoho CRM takes the usage of macros a notch higher by intelligently auto-suggesting macros that you could create based on your CRM activities. If you have been repeatedly performing the same set of actions over a period time on a bunch of records, Zoho CRM will automatically suggest that you create macros out of the actions. Consider the following scenario, in which the same set of actions are being performed thrice over a period of 10 days. Day 1: You send a Welcome Email template to a set of leads under "Today's Leads" custom view and then update the Lead Status field to Contacted . Day 3: Yo
### 4. FAQs : CRM Onboarding

How do I know which Zoho CRM Edition I am using? You can find out which Zoho CRM edition you are using by clicking the Profile icon on the top right corner of your window. The edition will be displayed next to Subscription. How can I delete my Zoho CRM account? There are multiple stages in deleting a Zoho CRM account. To delete individual users with the CRM account, you can follow these steps to delete them from Zoho CRM: 1. Click Setup > General > Users. 2. Click the user you want to delete. 3. Click the Delete This User button at the bottom of the User Details section. 4. You will see a dial
### 5. FAQs: Record Management

1. What is a record? Information about individual entities such as a person, product, case, or team activities stored in a place is called as a record in Zoho CRM. For example, a school stores information about its students from different classes. Each student is a record in the database that has information about his class, subject, parent's details, fees, etc. In CRM, students can be a module where you store students (records) data that contains information about an individual. 2. What is a 'module' in Zoho CRM? Modules are categories of data in the CRM. Consider he rows and columns of a spr
### 6. Email configuration for Microsoft Graph API

Users can integrate their mailbox with Zoho CRM securely to bring email conversations into the context of customer records. Users of Outlook/ Office 365 email accounts can use our dedicated Graph API integration to get a modern, secure, and future-proof email experience. Microsoft Graph API makes it easy to access data securely from across Microsoft’s cloud ecosystem. Using this option sets you up to access even smarter, faster, and more connected experiences in the future. Learn more about Graph API Note : In addition to Graph API, Outlook/ Office 365 users can use the IMAP and POP options to
### 7. Using and Creating Macros

Macros are a set of actions that can be executed for a group of records in a module. These sets of actions include sending emails, creating tasks, and updating a field in the records with a specified value . You may have a set of actions that you perform on a daily basis or frequently to some records. You can combine all these actions in a single macro and perform them again and again. Take for example, the following two scenarios and how using macros makes the job easier. Scenario 1 - You are a field sales executive and some leads are assigned to you. Your job is to meet the leads and try to
### 8. Working with global sets

Global sets in Zoho CRM help you easily manage picklist values that recur across modules. For an overview of this feature, see Overview of global sets . Where can I find global sets? Users with the requisite permissions in their profiles will be able to access global sets at Setup[ ] > Customization > Modules and Fields > Global Sets . The following features are available in your Global Sets tab: Search : Use this function to search your global sets by name. Create Global Set : Use this button to create a new global set. Global Set master list : Use this to manage all your global sets. You wil


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `SETTINGS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Adding Team Users`
- `Setting up Email Sharing Permissions`
- `Use macros auto-suggested by Zoho CRM`
- `FAQs : CRM Onboarding`

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

- **Security-Admin** -- shares data model and workflows
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

### Adding Team Users
**Purpose:** Editions : Standard, Professional, Enterprise, Ultimate, CRM Plus DC : All Pricing : $ 9 / team license / month (if paid yearly ) $ 11 / team license/ month (if paid monthly ) Related profile permissi

**Key Points:**
Editions : Standard, Professional, Enterprise, Ultimate, CRM Plus DC : All Pricing : $ 9 / team license / month (if paid yearly ) $ 11 / team license/ month (if paid monthly ) Related profile permission Users with the User Management > Manage Users permission in their profile can purchase and add team users.
Team users will have a system-defined Team User profile that is lightly customizable.
Required Actions For CRMPlus users, you need to enable the team user option at the bottom from General < Company Settings < Company Details.
CRM for everyone allows multiple teams to collaborate quickly and effectively while sharing the same context.
Members of non-sales teams may not require the same level of data access and capabilities to complete their tasks in the CRM.
For instance, a sales development rep might need similar access to sales reps, while a legal associate needs less


### Setting up Email Sharing Permissions
**Purpose:** Emails exchanged with customers contain important information that may be required for reference by several other teams who are involved in the business process. For example, a contract agreement exch

**Key Points:**
Emails exchanged with customers contain important information that may be required for reference by several other teams who are involved in the business process.
For example, a contract agreement exchanged with a firm may be required by the legal team to prepare a partnership agreement.
Likewise, the negotiation details discussed in email may be required by the payments team to prepare the invoice.
There are multiple such instances when a customer's email needs to be accessible to more than one person within the organization.
To facilitate easy access of emails, Zoho CRM provides email sharing options.
CRM administrators have the privilege to set email sharing options for individual users or specific roles


### Use macros auto-suggested by Zoho CRM
**Purpose:** Zoho CRM takes the usage of macros a notch higher by intelligently auto-suggesting macros that you could create based on your CRM activities. If you have been repeatedly performing the same set of act

**Key Points:**
Zoho CRM takes the usage of macros a notch higher by intelligently auto-suggesting macros that you could create based on your CRM activities.
If you have been repeatedly performing the same set of actions over a period time on a bunch of records, Zoho CRM will automatically suggest that you create macros out of the actions.
Consider the following scenario, in which the same set of actions are being performed thrice over a period of 10 days.
Day 1: You send a Welcome Email template to a set of leads under "Today's Leads" custom view and then update the Lead Status field to Contacted.
Day 3: You send the same Welcome Email to another set of leads under "Today's Leads" custom view and then update the Lead Status field to Contacted.
Day 8: When you repeat this action for the third consecutive time, that is, after you have sent the Welcome Email this time to a bunch of leads under "Today's Leads" custom view and updated the Lead Status field to Contacted , you will see a popup window suggesting that you create a macro out of this action


### FAQs : CRM Onboarding
**Purpose:** How do I know which Zoho CRM Edition I am using? You can find out which Zoho CRM edition you are using by clicking the Profile icon on the top right corner of your window. The edition will be displaye

**Key Points:**
How do I know which Zoho CRM Edition I am using.
You can find out which Zoho CRM edition you are using by clicking the Profile icon on the top right corner of your window.
The edition will be displayed next to Subscription.
How can I delete my Zoho CRM account.
There are multiple stages in deleting a Zoho CRM account.
To delete individual users with the CRM account, you can follow these steps to delete them from Zoho CRM: 1


### FAQs: Record Management
**Purpose:** 1. What is a record? Information about individual entities such as a person, product, case, or team activities stored in a place is called as a record in Zoho CRM. For example, a school stores informa

**Key Points:**
Information about individual entities such as a person, product, case, or team activities stored in a place is called as a record in Zoho CRM.
For example, a school stores information about its students from different classes.
Each student is a record in the database that has information about his class, subject, parent's details, fees, etc.
In CRM, students can be a module where you store students (records) data that contains information about an individual.
What is a 'module' in Zoho CRM.
Modules are categories of data in the CRM


### Email configuration for Microsoft Graph API
**Purpose:** Users can integrate their mailbox with Zoho CRM securely to bring email conversations into the context of customer records. Users of Outlook/ Office 365 email accounts can use our dedicated Graph API

**Key Points:**
Users can integrate their mailbox with Zoho CRM securely to bring email conversations into the context of customer records.
Users of Outlook/ Office 365 email accounts can use our dedicated Graph API integration to get a modern, secure, and future-proof email experience.
Microsoft Graph API makes it easy to access data securely from across Microsoft’s cloud ecosystem.
Using this option sets you up to access even smarter, faster, and more connected experiences in the future.
Learn more about Graph API Note : In addition to Graph API, Outlook/ Office 365 users can use the IMAP and POP options to integrate their email accounts.
To learn more, see Email configuration for IMAP and POP3


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

- [Adding Team Users](https://help.zoho.com/portal/en/kb/crm/articles/adding-team-users)
- [Setting up Email Sharing Permissions](https://help.zoho.com/portal/en/kb/crm/articles/setting-up-email-sharing-permissions)
- [Use macros auto-suggested by Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/auto-suggested-macros)
- [FAQs : CRM Onboarding](https://help.zoho.com/portal/en/kb/crm/articles/faqs-crm-onboarding)
- [FAQs: Record Management](https://help.zoho.com/portal/en/kb/crm/articles/faqs-record-management)
- [Email configuration for Microsoft Graph API](https://help.zoho.com/portal/en/kb/crm/articles/email-configuration-for-microsoft-graph-api)
- [Using and Creating Macros](https://help.zoho.com/portal/en/kb/crm/articles/using-macros)
- [Working with global sets](https://help.zoho.com/portal/en/kb/crm/articles/working-with-global-sets)
- [Zia Suggestions for Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/record-owner-suggestion-in-assignment-rule)
- [Set up your Organization Account](https://help.zoho.com/portal/en/kb/crm/articles/get-started-setup-organization-account)
- [Overview of global sets](https://help.zoho.com/portal/en/kb/crm/articles/overview-of-global-sets)
- [FAQs: Business Hours in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/faqs-business-hours-in-zoho-crm)
- [Deleting the Zoho CRM Account](https://help.zoho.com/portal/en/kb/crm/articles/close-zoho-crm-account)
- [FAQs: Modules](https://help.zoho.com/portal/en/kb/crm/articles/faqs-modules)
- [Data Analytics - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/data-analytics-overview)
- [FAQs : Macros](https://help.zoho.com/portal/en/kb/crm/articles/faqs-macros)
- [FAQs:  Zoho User ID, User IDs and Org IDs in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/faqs-zoho-user-id-user-ids-and-org-ids-in-zoho-crm-9-4-2026)
- [Why doesn't Zia analyze my data?](https://help.zoho.com/portal/en/kb/crm/articles/why-doesn-t-zia-analyze-my-data-2-4-2026)
- [Manage Hierarchy Preference](https://help.zoho.com/portal/en/kb/crm/articles/crm-setup-hierarchy-preference)
- [Creating Reporting Hierarchy](https://help.zoho.com/portal/en/kb/crm/articles/create-reporting-hierarchy)
- [Running and Deleting Macros](https://help.zoho.com/portal/en/kb/crm/articles/run-macros)
- [FAQs : Organization settings](https://help.zoho.com/portal/en/kb/crm/articles/faqs-organization-settings)
- [Manage Company Settings](https://help.zoho.com/portal/en/kb/crm/articles/manage-company-details)
- [FAQs: List Views in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/faqs-list-views-in-zoho-crm)
- [Setting up organization details](https://help.zoho.com/portal/en/kb/crm/articles/set-up-org-details)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
