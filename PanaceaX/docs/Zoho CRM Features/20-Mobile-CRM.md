# Mobile CRM

> **Feature ID:** `20-Mobile-CRM`  
> **Knowledge Base Articles:** 133  
> **Last Updated:** 2026-05-05

## Overview

Mobile app features for iOS, Android, tablet with offline and sync capabilities

---

## 1. Core Functionality

### 1. Managing Process

Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple roles. The approval processes created in the web version of Zoho CRM will also appear in the mobile version. Permission Required Users with Manage workflow permission in their profile can access this feature. Check Feature Availability and Limits Records that are waiting for approval can be viewed in the Android app and can then be approved, rejected, or delegated from the My Jobs module or from the record detail view of a specific module. To approve a record Tap the icon in your Zoho CRM app. Tap My Jobs . Tap on the required record in the list. Tap the record to view its details. Tap Approve . T
### 2. Field of Lookup

Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list. While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duration, subjects, course instructor, and so on—you can use the field of lookup module option. Business scenarios View additional details of a contact in the Deals module Sales associates can view a contact
### 3. NaijaSMSPortal for Zoho CRM

NaijaSMSPortal is an SMS provider that offers domestic (region-specific) SMS services to its users. By integrating the NaijaSMSPortal extension with Zoho CRM, you can send individual or bulk SMS messages to your leads and contacts directly from your Zoho CRM account. You can also create SMS templates in Zoho CRM that can be selected while sending SMS to users. Note: User should have an active NaijaSMSPortal account. If you do not have an account, click here to create one. The NaijaSMSPortal is supported only for the Nigeria numbers. The Mobile field of the lead or contact cannot be empty, and you must provide numbers from the supported region. Please note that the NaijaSMSPortal extension for Zoho CRM is available in US, EU, CN, IN, AU, CA, and JP datacenters. Installing the extension You 
### 4. Configuring SAML-based SSO in CRM portals

This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users. For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview . Prerequisite Glossary Prerequisite Editions: Enterprise and Ultimate Bundles (CRMPlus and Zoho One) Trial: No Developer: No Sandbox: No Mobile: No Permission : Users with the Manage Portals permission (Under Setup permissions > Admin level permissions ) can configure SAML based SSO for their CRM's portal and manage it. Glossary Authentication Authentication is the process of confirming a user's identity before providing access to a system. This is used to secure the system against impostors. SAML Security Assertion Markup Language (SAML) is a standard for communication that helps in authentica
### 5. WeChat for Zoho CRM

The WeChat extension for Zoho CRM helps you to connect with the leads in your CRM account via chats. You can send messages right from your CRM to the leads' WeChat account directly. Similarly, any messages from the leads will be received in your Zoho Cliq channel. With this extension, you can access the conversation history anytime from your CRM account. Requirements: WeChat cloud account ( www.mp.weixin.qq.com) WeChat mobile account (mobile app account) Installing the extension To install the extension: Navigate to Setup > Marketplace > All . Click All Extensions , then browse and click WeChat for Zoho CRM . Click Install Now . Agree to the Terms of Service and click Continue . In Choose Users/Profiles , select one of the following options: Install for admins only Install for all users Ch
### 6. Zoho CRM for iPhone - An Overview

Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above. From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc. Availability Permission Required Administrators need to activate it for users in other profiles. Features Zia Voice - Call or Chat with Zia to get answers for all your questions in Zoho CRM. Spotlight - Spotlight Search lets you see the contact information that you are searching for in a jiffy. Proactive Suggestions - Proactive suggestions let you take the fastest route to make your sale. They allow the frequently used apps to predict the data and h
### 7. FAQs: Path Finder

Path Finder in Zoho CRM is an observant tool built to discover and record real-time journeys taken by your customers in your business. With its ability to capture each customer interaction, you can get a comprehensive idea of how your prospects and customers are navigating within your business. Click here to learn more about Path Finder What is the difference between Path Finder and Journey Builder in Zoho CRM? Path Finder and Journey Builder are two subsets of an Experience Center toolkit in Zoho CRM called CommandCenter . While Path Finder will help you discover real-time journeys your customers are taking in your business, Journey Builder will help you design and template contextual journeys, thereon. Thus, based on Path Finder's findings, you can orchestrate a forward journey for your 
### 8. Call analytics

Call analytics is a VoC dashboard that displays charts on key insights observed in your call correspondences. Importance of call analytics The conventional mode of communication, calls , are versatile and on-demand when it comes to understanding and resolving customer requirements. However, identifying and resolving issues on-the-go, is just one advantage of jumping into a call. Calls are an actual treasure trove that could reveal subtle cues that were not intentionally part of your agenda. Let's look at how call analytics can help your business! Discovering customer interests: Along your lengthy sale pipeline, you will have discussed varying subjects with your prospects and customers. Imagine your prospect has a deal open to buy 5000 laptops. However, in order to find out company's other 


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `MOBILE`

**Standard Fields (inherited):**
- `Created_By` (User) — Record creator
- `Modified_By` (User) — Last modifier
- `Created_Time` (DateTime) — Creation timestamp
- `Modified_Time` (DateTime) — Last modification
- `Owner` (User) — Record owner for access control

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

- **Activities** — shares data model and workflows
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

### Managing Process
**Purpose:** Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple role

**Key Points:**
- Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization.
- This type of formal approval requires input from multiple roles.
- The approval processes created in the web version of Zoho CRM will also appear in the mobile version.
- Permission Required Users with Manage workflow permission in their profile can access this feature.
- Check Feature Availability and Limits Records that are waiting for approval can be viewed in th


### Field of Lookup
**Purpose:** Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Stu

**Key Points:**
- Overview Lookup fields enable users to associate records between two modules.
- Let's say, for example, you have two modules: Students and Courses.
- By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list.
- While the Course type lookup field displays the names of the courses in which a student has ex


### NaijaSMSPortal for Zoho CRM
**Purpose:** NaijaSMSPortal is an SMS provider that offers domestic (region-specific) SMS services to its users. By integrating the NaijaSMSPortal extension with Zoho CRM, you can send individual or bulk SMS messa

**Key Points:**
- NaijaSMSPortal is an SMS provider that offers domestic (region-specific) SMS services to its users.
- By integrating the NaijaSMSPortal extension with Zoho CRM, you can send individual or bulk SMS messages to your leads and contacts directly from your Zoho CRM account.
- You can also create SMS templates in Zoho CRM that can be selected while sending SMS to users.
- Note: User should have an active NaijaSMSPortal account.
- If you do not have an account, click here to create one.
- The NaijaSMSPortal is s


### Configuring SAML-based SSO in CRM portals
**Purpose:** This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users. For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview . 

**Key Points:**
- This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users.
- For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview.
- Prerequisite Glossary Prerequisite Editions: Enterprise and Ultimate Bundles (CRMPlus and Zoho One) Trial: No Developer: No Sandbox: No Mobile: No Permission : Users with the Manage Portals permission (Under Setup permissions > Admin level permissions ) can configure SAML based SSO for their CRM's p


### WeChat for Zoho CRM
**Purpose:** The WeChat extension for Zoho CRM helps you to connect with the leads in your CRM account via chats. You can send messages right from your CRM to the leads' WeChat account directly. Similarly, any mes

**Key Points:**
- The WeChat extension for Zoho CRM helps you to connect with the leads in your CRM account via chats.
- You can send messages right from your CRM to the leads' WeChat account directly.
- Similarly, any messages from the leads will be received in your Zoho Cliq channel.
- With this extension, you can access the conversation history anytime from your CRM account.
- Requirements: WeChat cloud account ( www.
- com) WeChat mobile account (mobile app account) Installing the extension To install the e


### Zoho CRM for iPhone - An Overview
**Purpose:** Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above

**Key Points:**
- Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone.
- 0 version of the native CRM app is available in iOS 8.
- From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc.
- Availability Permission Required Administrators need to activate it for users in other profiles.
- Features Zia Voice - Call or Chat with Zia to get answer


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

- [Managing Process](https://help.zoho.com/portal/en/kb/crm/articles/managing-process-in-zoho-crm-android-app)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/naijasmsportal-for-zoho-crm)
- [Configuring SAML-based SSO in CRM portals](https://help.zoho.com/portal/en/kb/crm/articles/configuring-saml-based-sso-in-crm-portals)
- [WeChat for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/wechat-for-zoho-crm-3-8-2021)
- [Zoho CRM for iPhone - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-iphone-an-overview)
- [FAQs: Path Finder](https://help.zoho.com/portal/en/kb/crm/articles/faqs-path-finder)
- [Call analytics](https://help.zoho.com/portal/en/kb/crm/articles/call-analytics)
- [Team modules in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/articles/team-modules-in-zoho-crm-ios-app)
- [Converting Leads](https://help.zoho.com/portal/en/kb/crm/articles/convert-leads)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [Working with Analytics in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/working-with-analytics-in-zoho-crm-android-app)
- [Creating Quotes](https://help.zoho.com/portal/en/kb/crm/articles/create-quotes)
- [Using and Creating Macros](https://help.zoho.com/portal/en/kb/crm/articles/using-macros)
- [Using Native App for Tablets](https://help.zoho.com/portal/en/kb/crm/articles/using-native-app-for-tablets)
- [Aircall](https://help.zoho.com/portal/en/kb/crm/articles/integrate-with-aircall)
- [Email Configuration IMAP](https://help.zoho.com/portal/en/kb/crm/articles/email-configuration-imap)
- [User details in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/user-details-in-zoho-crm-android-app)
- [FAQs: Page layouts](https://help.zoho.com/portal/en/kb/crm/articles/faqs-page-layouts)
- [Tencent](https://help.zoho.com/portal/en/kb/crm/articles/tencent-crm-integration)
- [Locate people near you in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/locate-people-near-you-in-the-zoho-crm-android-app)
- [Many-to-Many Module Association](https://help.zoho.com/portal/en/kb/crm/articles/linking-modules)
- [Team modules in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/articles/team-modules-in-zoho-crm-android-app)
- [Associate Functions](https://help.zoho.com/portal/en/kb/crm/articles/associate-functions-workflow-rules)
- [ Signals in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/signals-in-zoho-crm-ios-app-24-2-2026)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
