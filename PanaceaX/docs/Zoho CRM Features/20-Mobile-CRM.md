# Mobile CRM

> **Feature ID:** `20-Mobile-CRM`  
> **Knowledge Base Articles:** 193  
> **Last Updated:** 2026-05-05

## Overview

Mobile app features for iOS, Android, tablet with offline and sync capabilities

---

## 1. Core Functionality

### 1. Managing Process

Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple roles. The approval processes created in the web version of Zoho CRM will also appear in the mobile version. Permission Required Users with Manage workflow permission in their profile can access this feature. Check Feature Availability and Limits Records that are waiting for approval can be viewed in the Android app and can then be approved, rejected, or delegated from the My Jobs module or from the r
### 2. Field of Lookup

Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list. While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duratio
### 3. NaijaSMSPortal for Zoho CRM

NaijaSMSPortal is an SMS provider that offers domestic (region-specific) SMS services to its users. By integrating the NaijaSMSPortal extension with Zoho CRM, you can send individual or bulk SMS messages to your leads and contacts directly from your Zoho CRM account. You can also create SMS templates in Zoho CRM that can be selected while sending SMS to users. Note: User should have an active NaijaSMSPortal account. If you do not have an account, click here to create one. The NaijaSMSPortal is supported only for the Nigeria numbers. The Mobile field of the lead or contact cannot be empty, and
### 4. Configuring SAML-based SSO in CRM portals

This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users. For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview . Prerequisite Glossary Prerequisite Editions: Enterprise and Ultimate Bundles (CRMPlus and Zoho One) Trial: No Developer: No Sandbox: No Mobile: No Permission : Users with the Manage Portals permission (Under Setup permissions > Admin level permissions ) can configure SAML based SSO for their CRM's portal and manage it. Glossary Authentication Authentication is the process of confirming a user's id
### 5. WeChat for Zoho CRM

The WeChat extension for Zoho CRM helps you to connect with the leads in your CRM account via chats. You can send messages right from your CRM to the leads' WeChat account directly. Similarly, any messages from the leads will be received in your Zoho Cliq channel. With this extension, you can access the conversation history anytime from your CRM account. Requirements: WeChat cloud account ( www.mp.weixin.qq.com) WeChat mobile account (mobile app account) Installing the extension To install the extension: Navigate to Setup > Marketplace > All . Click All Extensions , then browse and click WeCha
### 6. Zoho CRM for iPhone - An Overview

Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above. From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc. Availability Permission Required Administrators need to activate it for users in other profiles. Features Zia Voice - Call or Chat with Zia to get answers for all your questions in Zoho CRM. Spotlight - Spotlight Search lets you see the contact informat
### 7. Working with notes in Zoho CRM iOS app 

Notes make it easy to capture your interactions with customers and prospects in CRM. You can add notes to leads, contacts, accounts, deals, activities, and more. These notes are stored as related items under each entry, so all your interaction details stay connected and organized. You can add notes in the following ways: Text notes Voice notes Voice-to-text notes ${accordionSetId_2026_0_20_17_6_53} To add text notes Open the record. Go to Notes under the related list. Tap on the icon Type out the note and apply rich text formatting if needed ( bold, italics, text color, etc.). Tap on the icon
### 8. FAQs: Path Finder

Path Finder in Zoho CRM is an observant tool built to discover and record real-time journeys taken by your customers in your business. With its ability to capture each customer interaction, you can get a comprehensive idea of how your prospects and customers are navigating within your business. Click here to learn more about Path Finder What is the difference between Path Finder and Journey Builder in Zoho CRM? Path Finder and Journey Builder are two subsets of an Experience Center toolkit in Zoho CRM called CommandCenter . While Path Finder will help you discover real-time journeys your custo


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `MOBILE`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Managing Process`
- `Field of Lookup`
- `NaijaSMSPortal for Zoho CRM`
- `Configuring SAML-based SSO in CRM portals`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/mobile` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Mobile CRM - Example Implementation
// Triggered on record creation/update

if(input.module == "MANAGING PROCESS")
{
    // Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of
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

- [Activities](../Activities/README.md)
- [Leads-Management](../Leads-Management/README.md)
- [Contacts-Management](../Contacts-Management/README.md)
- [Analytics-Dashboards](../Analytics-Dashboards/README.md)

### This Feature Enables

- **Activities** -- shares data model and workflows
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

### Managing Process
**Purpose:** Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple role

**Key Points:**
Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization.
This type of formal approval requires input from multiple roles.
The approval processes created in the web version of Zoho CRM will also appear in the mobile version.
Permission Required Users with Manage workflow permission in their profile can access this feature.
Check Feature Availability and Limits Records that are waiting for approval can be viewed in the Android app and can then be approved, rejected, or delegated from the My Jobs module or from the record detail view of a specific module.
To approve a record Tap the icon in your Zoho CRM app


### Field of Lookup
**Purpose:** Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Stu

**Key Points:**
Overview Lookup fields enable users to associate records between two modules.
Let's say, for example, you have two modules: Students and Courses.
By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list.
While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duration, subjects, course instructor, and so on—you can use the field of lookup module option.
Business scenarios View additional details of a contact in the Deals module Sales associates can view a contact's email address, phone number, referrer, and—alongside the primary lookup field—the contact's name.
They can also view the values in these fields in a report created for the Deals module


### NaijaSMSPortal for Zoho CRM
**Purpose:** NaijaSMSPortal is an SMS provider that offers domestic (region-specific) SMS services to its users. By integrating the NaijaSMSPortal extension with Zoho CRM, you can send individual or bulk SMS messa

**Key Points:**
NaijaSMSPortal is an SMS provider that offers domestic (region-specific) SMS services to its users.
By integrating the NaijaSMSPortal extension with Zoho CRM, you can send individual or bulk SMS messages to your leads and contacts directly from your Zoho CRM account.
You can also create SMS templates in Zoho CRM that can be selected while sending SMS to users.
Note: User should have an active NaijaSMSPortal account.
If you do not have an account, click here to create one.
The NaijaSMSPortal is supported only for the Nigeria numbers


### Configuring SAML-based SSO in CRM portals
**Purpose:** This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users. For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview .

**Key Points:**
This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users.
For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview.
Prerequisite Glossary Prerequisite Editions: Enterprise and Ultimate Bundles (CRMPlus and Zoho One) Trial: No Developer: No Sandbox: No Mobile: No Permission : Users with the Manage Portals permission (Under Setup permissions > Admin level permissions ) can configure SAML based SSO for their CRM's portal and manage it.
Glossary Authentication Authentication is the process of confirming a user's identity before providing access to a system.
This is used to secure the system against impostors.
SAML Security Assertion Markup Language (SAML) is a standard for communication that helps in authentication


### WeChat for Zoho CRM
**Purpose:** The WeChat extension for Zoho CRM helps you to connect with the leads in your CRM account via chats. You can send messages right from your CRM to the leads' WeChat account directly. Similarly, any mes

**Key Points:**
The WeChat extension for Zoho CRM helps you to connect with the leads in your CRM account via chats.
You can send messages right from your CRM to the leads' WeChat account directly.
Similarly, any messages from the leads will be received in your Zoho Cliq channel.
With this extension, you can access the conversation history anytime from your CRM account.
Requirements: WeChat cloud account ( www.
com) WeChat mobile account (mobile app account) Installing the extension To install the extension: Navigate to Setup > Marketplace > All


### Zoho CRM for iPhone - An Overview
**Purpose:** Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above

**Key Points:**
Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone.
0 version of the native CRM app is available in iOS 8.
From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc.
Availability Permission Required Administrators need to activate it for users in other profiles.
Features Zia Voice - Call or Chat with Zia to get answers for all your questions in Zoho CRM.
Spotlight - Spotlight Search lets you see the contact information that you are searching for in a jiffy


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

- [Managing Process](https://help.zoho.com/portal/en/kb/crm/articles/managing-process-in-zoho-crm-android-app)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/naijasmsportal-for-zoho-crm)
- [Configuring SAML-based SSO in CRM portals](https://help.zoho.com/portal/en/kb/crm/articles/configuring-saml-based-sso-in-crm-portals)
- [WeChat for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/wechat-for-zoho-crm-3-8-2021)
- [Zoho CRM for iPhone - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-iphone-an-overview)
- [Working with notes in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/working-with-notes-in-zoho-crm-ios-app)
- [FAQs: Path Finder](https://help.zoho.com/portal/en/kb/crm/articles/faqs-path-finder)
- [Call analytics](https://help.zoho.com/portal/en/kb/crm/articles/call-analytics)
- [Team modules in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/articles/team-modules-in-zoho-crm-ios-app)
- [Installing the CRM Mobile App](https://help.zoho.com/portal/en/kb/crm/articles/installing-crm-mobile-app)
- [Swipe actions in Zoho CRM Android app ](https://help.zoho.com/portal/en/kb/crm/articles/swipe-actions-in-zoho-crm-android-app)
- [Converting Leads](https://help.zoho.com/portal/en/kb/crm/articles/convert-leads)
- [Building a Subform](https://help.zoho.com/portal/en/kb/crm/articles/build-subforms)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/working-with-analytics-in-zoho-crm-android-app)
- [FAQs: Data Enrichment](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-enrichment)
- [Creating Quotes](https://help.zoho.com/portal/en/kb/crm/articles/create-quotes)
- [Customizing the navigation bar in the Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/customizing-the-navigation-bar-in-the-zoho-crm-ios-app)
- [Using and Creating Macros](https://help.zoho.com/portal/en/kb/crm/articles/using-macros)
- [Tags in Zoho CRM for Android](https://help.zoho.com/portal/en/kb/crm/articles/tags-in-zoho-crm-for-android)
- [Using Native App for Tablets](https://help.zoho.com/portal/en/kb/crm/articles/using-native-app-for-tablets)
- [FAQs: CRM Analytics App](https://help.zoho.com/portal/en/kb/crm/articles/faqs-crm-analytics-app)
- [Aircall](https://help.zoho.com/portal/en/kb/crm/articles/integrate-with-aircall)
- [Email Configuration IMAP](https://help.zoho.com/portal/en/kb/crm/articles/email-configuration-imap)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
