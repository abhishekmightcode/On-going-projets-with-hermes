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

---
## UI Screenshots & Image Reference
This feature has **43 KB articles** with **408 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Elements of a kiosk](https://help.zoho.com/portal/en/kb/crm/elements-of-a-kiosk) | 44 | [View Article](https://help.zoho.com/portal/en/kb/crm/elements-of-a-kiosk) |
| 2 | [iOS Specific Features](https://help.zoho.com/portal/en/kb/crm/ios-specific-features) | 27 | [View Article](https://help.zoho.com/portal/en/kb/crm/ios-specific-features) |
| 3 | [FAQs: Kiosk Studio](https://help.zoho.com/portal/en/kb/crm/faqs-kiosk-studio) | 24 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-kiosk-studio) |
| 4 | [Dynamic display in Zoho CRM for Android](https://help.zoho.com/portal/en/kb/crm/dynamic-display-in-zoho-crm-android-app) | 22 | [View Article](https://help.zoho.com/portal/en/kb/crm/dynamic-display-in-zoho-crm-android-app) |
| 5 | [Tags in Zoho CRM for Android](https://help.zoho.com/portal/en/kb/crm/tags-in-zoho-crm-for-android) | 20 | [View Article](https://help.zoho.com/portal/en/kb/crm/tags-in-zoho-crm-for-android) |
| 6 | [Configure Zoho CRM Settings in iPhone](https://help.zoho.com/portal/en/kb/crm/configure-zoho-crm-settings-in-iphone) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/configure-zoho-crm-settings-in-iphone) |
| 7 | [Dynamic display in Zoho CRM for iOS](https://help.zoho.com/portal/en/kb/crm/dynamic-display-in-zoho-crm-for-ios) | 18 | [View Article](https://help.zoho.com/portal/en/kb/crm/dynamic-display-in-zoho-crm-for-ios) |
| 8 | [WhatsApp business messaging in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/whatsapp-business-messaging-in-zoho-crm-ios-app) | 16 | [View Article](https://help.zoho.com/portal/en/kb/crm/whatsapp-business-messaging-in-zoho-crm-ios-app) |
| 9 | [Actions performed on records in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/actions-performed-on-records-in-zoho-crm-ios-app) | 16 | [View Article](https://help.zoho.com/portal/en/kb/crm/actions-performed-on-records-in-zoho-crm-ios-app) |
| 10 | [WhatsApp business messaging in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/whatsapp-business-messaging-in-zoho-crm-android-app) | 15 | [View Article](https://help.zoho.com/portal/en/kb/crm/whatsapp-business-messaging-in-zoho-crm-android-app) |
| 11 | [Working with Kiosk Studio](https://help.zoho.com/portal/en/kb/crm/working-with-kiosks) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-kiosks) |
| 12 | [Zoho CRM App Settings For Android](https://help.zoho.com/portal/en/kb/crm/zoho-crm-app-settings-for-android) | 13 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-crm-app-settings-for-android) |
| 13 | [Platform widgets in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/platform-widgets-in-zoho-crm-ios-app-29-1-2026) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/platform-widgets-in-zoho-crm-ios-app-29-1-2026) |
| 14 | [Wizards in CRM Android app](https://help.zoho.com/portal/en/kb/crm/wizards-in-crm-android-app) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/wizards-in-crm-android-app) |
| 15 | [Record sharing in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/record-sharing-in-zoho-crm-ios-app) | 10 | [View Article](https://help.zoho.com/portal/en/kb/crm/record-sharing-in-zoho-crm-ios-app) |
| 16 | [Teamspace in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/teamspace-in-zoho-crm-for-ios) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/teamspace-in-zoho-crm-for-ios) |
| 17 | [Locate people near you in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/locate-people-near-you-in-the-zoho-crm-android-app) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/locate-people-near-you-in-the-zoho-crm-android-app) |
| 18 | [Collaborate using feeds in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/collaborate-using-feeds-in-zoho-crm-ios-app) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/collaborate-using-feeds-in-zoho-crm-ios-app) |
| 19 | [Mappls map view in Zoho CRM Android app ](https://help.zoho.com/portal/en/kb/crm/mappls-map-view-in-zoho-crm-android-app) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/mappls-map-view-in-zoho-crm-android-app) |
| 20 | [Locate an address using maps in iPhone](https://help.zoho.com/portal/en/kb/crm/locate-an-address-using-maps-in-iphone) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/locate-an-address-using-maps-in-iphone) |
| 21 | [Teamspace in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/teamspace-in-zoho-crm-for-android) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/teamspace-in-zoho-crm-for-android) |
| 22 | [Map view in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/map-view-in-zoho-crm-ios-app) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/map-view-in-zoho-crm-ios-app) |
| 23 | [Searching records in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/searching-records-in-zoho-crm-android) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/searching-records-in-zoho-crm-android) |
| 24 | [ Record sharing in Zoho CRM Android app ](https://help.zoho.com/portal/en/kb/crm/record-sharing-in-zoho-crm-android-app) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/record-sharing-in-zoho-crm-android-app) |
| 25 | [ Searching records in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/searching-records-in-zoho-crm-android-app) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/searching-records-in-zoho-crm-android-app) |
| 26 | [ Working with Zoho surveys in CRM Android app    ](https://help.zoho.com/portal/en/kb/crm/working-with-zoho-surveys-in-crm-android-app) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-zoho-surveys-in-crm-android-app) |
| 27 | [Installing and signing in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/installing-the-app-in-iphone) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/installing-the-app-in-iphone) |
| 28 | [Map settings in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/map-settings-in-zoho-crm-ios-app) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/map-settings-in-zoho-crm-ios-app) |
| 29 | [List view and saved filters in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/list-view-and-saved-filters-in-zoho-crm-ios-app) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/list-view-and-saved-filters-in-zoho-crm-ios-app) |
| 30 | [ Working with Zoho surveys in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/working-with-zoho-surveys-in-crm-ios-app) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-zoho-surveys-in-crm-ios-app) |
| 31 | [List view and saved filters in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/list-view-and-saved-filters-in-crm-android-app) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/list-view-and-saved-filters-in-crm-android-app) |
| 32 | [ Kiosk in Zoho CRM Android app ](https://help.zoho.com/portal/en/kb/crm/kiosk-in-zoho-crm-android-app) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/kiosk-in-zoho-crm-android-app) |
| 33 | [Mappls map view in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/mappls-map-view-in-zoho-crm-ios-app) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/mappls-map-view-in-zoho-crm-ios-app) |
| 34 | [Homescreen quick actions in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/homescreen-quick-actions-in-zoho-crm-ios-app-23-2-2026-1) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/homescreen-quick-actions-in-zoho-crm-ios-app-23-2-2026-1) |
| 35 | [Working with notes in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/working-with-notes-in-zoho-crm-ios-app) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-notes-in-zoho-crm-ios-app) |
| 36 | [Organizing your home page in Zoho CRM Android app](https://help.zoho.com/portal/en/kb/crm/organizing-your-home-page-in-zoho-crm-android-app) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/organizing-your-home-page-in-zoho-crm-android-app) |
| 37 | [Kiosk in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/kiosk-in-zoho-crm-ios-app) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/kiosk-in-zoho-crm-ios-app) |
| 38 | [Switching between organizations in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/switching-between-organizations-in-zoho-crm-ios-app) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/switching-between-organizations-in-zoho-crm-ios-app) |
| 39 | [ Signals in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/signals-in-zoho-crm-ios-app-24-2-2026) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/signals-in-zoho-crm-ios-app-24-2-2026) |
| 40 | [Organizing the homepage in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/organizing-the-homepage-in-zoho-crm-ios-app) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/organizing-the-homepage-in-zoho-crm-ios-app) |
| 41 | [Fetch VoC insights using Kiosk–On demand](https://help.zoho.com/portal/en/kb/crm/fetch-voc-insights-using-kiosk-on-demand) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/fetch-voc-insights-using-kiosk-on-demand) |
| 42 | [FAQs: CRM for iphone](https://help.zoho.com/portal/en/kb/crm/faqs-crm-for-iphone) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-crm-for-iphone) |
| 43 | [FAQs: CRM for Mobile](https://help.zoho.com/portal/en/kb/crm/faqs-crm-for-mobile) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-crm-for-mobile) |

### Sample Image URLs (from top articles)
**[Elements of a kiosk](https://help.zoho.com/portal/en/kb/crm/elements-of-a-kiosk)** — 44 images
- `https://desk.zoho.in/galleryDocuments/edbsncd824102bb0df0bd0ad306447e1190bc105a351635c20fa615e843a949e586b2920892d56efde31d80e8d0531bc00a13331e7b3d5c9cf3674cc978bbe777aa8c?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsncd824102bb0df0bd0ad306447e1190bc15f2d3445a5466ce3b75c0a9e5d587a4327211d596714138e6bf2fab814860f037c6d6f7edb551f126980e3d347a55fe?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsncd824102bb0df0bd0ad306447e1190bcbdf81248ba3285f2d7a1f9f806ccb5f90f4797bf7436e07416f6a859adc82f17bc5bbed7119d29435cbc6b7ad70c917b?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsncd824102bb0df0bd0ad306447e1190bc45b5f00e36ea4eb4947a2d3e2611816c732533d17fb583123e302dfe2aa2f60d5da50228eba6ff539b1572c52a87cfce?inline=true`
[View all 44 images in article →](https://help.zoho.com/portal/en/kb/crm/elements-of-a-kiosk)

**[iOS Specific Features](https://help.zoho.com/portal/en/kb/crm/ios-specific-features)** — 27 images
- `https://www.zohowebstatic.com/sites/default/files/crm/zia.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/zia-call.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/zia-response.jpg`
- `https://www.zohowebstatic.com/sites/default/files/crm/mute-zia.png`
[View all 27 images in article →](https://help.zoho.com/portal/en/kb/crm/ios-specific-features)

**[FAQs: Kiosk Studio](https://help.zoho.com/portal/en/kb/crm/faqs-kiosk-studio)** — 24 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575af5cba1b728bc27ffd6be4dd9e7ae01666346585d7b5972486553b44385ec20bbafd58341a775f12d0ddb0cef9eefd3?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579c393cfd8019f1aca968477d9f1f3e704e7a0cce986ff6e8b486950206d71f217ed356ff764d13975382b488a7d7c0ef?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57bf7ef3152df5f10c0c64ce295ddedfe85b66dc832db46569d89802a1f35234e9f0a791c7fa9784eb91631b8da672f2ad?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5755046ac3d80b47c13a9d60ef3120bb0528a2b9ab14006cb7ee48322efb1841aa6dfcd72c52095ca0d6477ecbdad6ee36?inline=true`
[View all 24 images in article →](https://help.zoho.com/portal/en/kb/crm/faqs-kiosk-studio)

**[Dynamic display in Zoho CRM for Android](https://help.zoho.com/portal/en/kb/crm/dynamic-display-in-zoho-crm-android-app)** — 22 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5740b571054c7ffc0ecbeec36717a8c3edb143db58d6176b6f43cdca7f66c29f468370f02086989300c68eed7834fda6ac?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57832f80719b8eebfb0058b344c5964180ad8ae3aca19d64c71f69de7e362db794a28bdc12f7f24ad8dad68af61e56fb21?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57be92226ea051eed2d85e4e519091f3498dba42aace049dc9446c3ccc527496a3388f0064a8b3cedd2361f7895163326b?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579f5b253266a8e52561d8e6c1eda625346acb49d4efd7135da0293ae8f3b53c329b36c5b5f47be5d3f5757412327d160b?inline=true`
[View all 22 images in article →](https://help.zoho.com/portal/en/kb/crm/dynamic-display-in-zoho-crm-android-app)

**[Tags in Zoho CRM for Android](https://help.zoho.com/portal/en/kb/crm/tags-in-zoho-crm-for-android)** — 20 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5781afb5bd4b7bdaaba1b4201b01bff65699664040782b3e88fd2d41e8865e18566f6badf1dddd619ebfc8098832a3cabb?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d758594ffd3bef358e66bf7361c08c7aa6dc26f463f796068d1974ab0f844652845d251c076fe7f0e38e0d436821d099?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5776af2ec07d67567ed4aeeba9c10f50e0b122e5869e4fae28f184195d3dfd802fd134ddd836d0360347232825e1caeeda?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57777681869976167dd31950ac819114ad69f28507647a0585694738557c84bb5b18cbd653f96101ec7767506dc2d67ca0?inline=true`
[View all 20 images in article →](https://help.zoho.com/portal/en/kb/crm/tags-in-zoho-crm-for-android)

