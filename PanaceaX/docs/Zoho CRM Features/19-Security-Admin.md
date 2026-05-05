# Security, Roles & Administration

> **Feature ID:** `19-Security-Admin`  
> **Knowledge Base Articles:** 465  
> **Last Updated:** 2026-05-05

## Overview

User management, roles, profiles, data sharing, security controls, GDPR, HIPAA compliance

---

## 1. Core Functionality

### 1. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 2. Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics

1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketplace requires an administrator to initiate the process. The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM. There may be some backend issues that prevent you from integrating advanced analytics into your CRM. In such cases, please feel free to contact the support team, support@zohocrm.com 2. Why am I unabl
### 3. Importing Contacts from G Suite

The Import Contacts feature helps you import contacts from G Suite to Zoho CRM. It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google account, every time you want to import. The imported contacts from G Suite will be assigned to you and shared with Zoho CRM users as per your organization's hierarchy. We recommend that you import business contacts only. Standard Field Mapping Zoho CRM Field Google Apps Field First Name - Last Name Name Email Email Phone Phone - Address - Website Birthday Birthday Description Notes To import contacts
### 4. Setting up Zoho Creator Integration

Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account. You should have a Zoho Creator account with any edition. If you do not have a Zoho Creator account, please create an account from Zoho Create. An account with the Free Edition will be automatically created. After which you can proceed with integrating it with Zoho CRM. Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for t
### 5. Zia for Workflow Rules

You automate several sales followup activities using workflow rules to save time and efforts, which in turn increase the productivity of sales people. However, keeping track of triggers made through workflow rules to see what works best and what doesn't could be cumbersome. Zia does just that for you. Zia brings AI to your workflow automation processes by detecting anomalies and provide suggestions for your workflow rules. Zia also identifies and prevents you from making mistakes, such as sending multiple email templates to the same customer on the same day. Availability Permission Required Us
### 6. Managing Process

Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple roles. The approval processes created in the web version of Zoho CRM will also appear in the mobile version. Permission Required Users with Manage workflow permission in their profile can access this feature. Check Feature Availability and Limits Records that are waiting for approval can be viewed in the Android app and can then be approved, rejected, or delegated from the My Jobs module or from the r
### 7. Setting up an Unsubscribe Link

Allow the customers to unsubscribe from your email communications by creating an unsubscribe link and embedding it in the emails or hosting on the webpages. You can use the system defined default link or create a custom link. The default unsubscribe link will be available for all users and that cannot be customized. Availability Permission Required Users with the Unsubscribe Form permission in profile can access this feature. Creating an Unsubscribe Link Two essential things you need to set this up are: Location URL It is the web page where the unsubscribe link will be hosted. You can choose a
### 8. FAQs: Data Administration

How can I delete the existing data in my Zoho CRM account and start with a fresh account? You need to manually delete all the data in your account to start a fresh account. You can also close the existing account and sign up for a new Zoho CRM account with the same email address (Not Recommended). Related Link Deleting the Zoho CRM Account How do I delete attachments to free up storage space? When mails (with attachments) are sent using the email template, the attachment is counted only once for your storage, For example, if you send emails to 100 users, the document attached is not counted on


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `SECURITY`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Consent Management`
- `Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics`
- `Importing Contacts from G Suite`
- `Setting up Zoho Creator Integration`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/security` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Security, Roles & Administration - Example Implementation
// Triggered on record creation/update

if(input.module == "CONSENT MANAGEMENT")
{
    // Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent
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

- [Modules-Data-Model](../Modules-Data-Model/README.md)
- [Data-Tools](../Data-Tools/README.md)
- [Settings-Configuration](../Settings-Configuration/README.md)

### This Feature Enables

- **Modules-Data-Model** -- shares data model and workflows
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

### Consent Management
**Purpose:** Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set con

**Key Points:**
Zoho CRM's consent management settings help you get consent from your prospects and customers.
We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details.
Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules.
It cannot be applied for team modules.
Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be.
You will begin by marking the records whose data needs to be processed after obtaining consent


### Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics
**Purpose:** 1. Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM? Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM. The integration of apps from the marketp

**Key Points:**
Why am I unable to integrate Zoho Advanced Analytics with Zoho CRM.
Make sure that you have admin privilege before integrating Zoho Analytics with Zoho CRM.
The integration of apps from the marketplace requires an administrator to initiate the process.
The fields must be mapped properly to set up the integration, as incorrect field mapping won't let you integrate advanced analytics in your CRM.
There may be some backend issues that prevent you from integrating advanced analytics into your CRM.
In such cases, please feel free to contact the support team, support@zohocrm


### Importing Contacts from G Suite
**Purpose:** The Import Contacts feature helps you import contacts from G Suite to Zoho CRM. It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google acc

**Key Points:**
The Import Contacts feature helps you import contacts from G Suite to Zoho CRM.
It gives you the advantage of accessing your Google contacts from Zoho CRM, without having to sign in to your Google account, every time you want to import.
The imported contacts from G Suite will be assigned to you and shared with Zoho CRM users as per your organization's hierarchy.
We recommend that you import business contacts only.
Standard Field Mapping Zoho CRM Field Google Apps Field First Name - Last Name Name Email Email Phone Phone - Address - Website Birthday Birthday Description Notes To import contacts from G Suite, follow these steps: In G Suite , click on (the Apps icon).
You will be redirected to Zoho CRM


### Setting up Zoho Creator Integration
**Purpose:** Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Z

**Key Points:**
Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account.
You should have a Zoho Creator account with any edition.
If you do not have a Zoho Creator account, please create an account from Zoho Create.
An account with the Free Edition will be automatically created.
After which you can proceed with integrating it with Zoho CRM.
Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for testing


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

- [Consent Management](https://help.zoho.com/portal/en/kb/crm/articles/consent-management)
- [Troubleshooting integration of Zoho CRM with Zoho Advanced Analytics](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-integration-of-zoho-crm-with-zoho-advanced-analytics)
- [Importing Contacts from G Suite](https://help.zoho.com/portal/en/kb/crm/articles/import-contacts-g-suite)
- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [Zia for Workflow Rules](https://help.zoho.com/portal/en/kb/crm/articles/zia-intelligence-automation)
- [Managing Process](https://help.zoho.com/portal/en/kb/crm/articles/managing-process-in-zoho-crm-android-app)
- [Setting up an Unsubscribe Link](https://help.zoho.com/portal/en/kb/crm/articles/set-unsubscribe-link)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Setting up Zoho Writer Add-on](https://help.zoho.com/portal/en/kb/crm/articles/zoho-writer-crm-integration)
- [SurveyMonkey](https://help.zoho.com/portal/en/kb/crm/articles/surveymonkey-crm-integration)
- [Managing Web Tabs](https://help.zoho.com/portal/en/kb/crm/articles/web-tabs)
- [Capabilities of Zia in Zoho CRM— A perspective](https://help.zoho.com/portal/en/kb/crm/articles/zia-overview)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/naijasmsportal-for-zoho-crm)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [Decision Guide for Territory Management](https://help.zoho.com/portal/en/kb/crm/articles/territory-decision-management)
- [RingCentral Video](https://help.zoho.com/portal/en/kb/crm/articles/ringcentral-video)
- [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/articles/set-email-notifications)
- [Address Locator for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/address-locator-for-zoho-crm)
- [Configuring SAML-based SSO in CRM portals](https://help.zoho.com/portal/en/kb/crm/articles/configuring-saml-based-sso-in-crm-portals)
- [WeChat for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/wechat-for-zoho-crm-3-8-2021)
- [Zoho CRM for iPhone - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-iphone-an-overview)
- [Adding Team Users](https://help.zoho.com/portal/en/kb/crm/articles/adding-team-users)
- [Lead Queue for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/lead-queue-for-zoho-crm)
- [SharePoint for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/sharepoint-for-zoho-crm)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **11 KB articles** with **84 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Microsoft Exchange - Administrator Guide](https://help.zoho.com/portal/en/kb/crm/microsoft-exchange-administrator-guide) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/microsoft-exchange-administrator-guide) |
| 2 | [Privacy and security settings in the Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/privacy-and-security-settings-in-the-zoho-crm-ios-app) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/privacy-and-security-settings-in-the-zoho-crm-ios-app) |
| 3 | [Requester roles for coordination between teams](https://help.zoho.com/portal/en/kb/crm/requester-roles-for-coordination-between-teams) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/requester-roles-for-coordination-between-teams) |
| 4 | [Admin Tools  for Configuration Management](https://help.zoho.com/portal/en/kb/crm/working-with-admin-tools) | 9 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-admin-tools) |
| 5 | [Managing Roles](https://help.zoho.com/portal/en/kb/crm/role-management-introduction) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/role-management-introduction) |
| 6 | [Security controls in Zoho CRM: An overview](https://help.zoho.com/portal/en/kb/crm/security-controls-in-zoho-crm-an-overview-26-4-2026) | 6 | [View Article](https://help.zoho.com/portal/en/kb/crm/security-controls-in-zoho-crm-an-overview-26-4-2026) |
| 7 | [Managing Profile Permissions](https://help.zoho.com/portal/en/kb/crm/manage-profile-permissions) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/manage-profile-permissions) |
| 8 | [FAQ: Requester Roles in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/faq-requester-roles-in-zoho-crm) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/faq-requester-roles-in-zoho-crm) |
| 9 | [FAQs: Roles and Profiles](https://help.zoho.com/portal/en/kb/crm/faqs-roles-and-profiles) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-roles-and-profiles) |
| 10 | [How Zoho CRM Administration and Configuration Works for Sales Operations](https://help.zoho.com/portal/en/kb/crm/how-zoho-crm-administration-and-configuration-works-for-sales-operations) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/how-zoho-crm-administration-and-configuration-works-for-sales-operations) |
| 11 | [Zoho CRM and Security: A partnership that forms the bedrock of our operations ](https://help.zoho.com/portal/en/kb/crm/zoho-crm-and-security-a-partnership-that-forms-the-bedrock-of-our-operations) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/zoho-crm-and-security-a-partnership-that-forms-the-bedrock-of-our-operations) |

### Sample Image URLs (from top articles)
**[Microsoft Exchange - Administrator Guide](https://help.zoho.com/portal/en/kb/crm/microsoft-exchange-administrator-guide)** — 23 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ca302664d4c90b6e8f058a38902d57457ec78b5ddbe3add411057485e0e66c856ddd24b92cf011e9a4ec95b0bc0831a0?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f41b74e6c0aab18c8a5adca3ff1fbe075c706bc32830140b1c3e9516bc7091043f8d7009075685f67b21d631d4cad329?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d984423a3b109110bd22cecf4846cdf99e7f213da624a0c2e1f80232d53f8f0b68a84c8251e7424e2c62f73cd7c0bc82?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579a1feeba4744c62e91e943a9e6b95a56148f990de8f137bacf5780c7974186f9082587175d7d42b0f6ba5098b9dba1ce?inline=true`
[View all 23 images in article →](https://help.zoho.com/portal/en/kb/crm/microsoft-exchange-administrator-guide)

**[Privacy and security settings in the Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/privacy-and-security-settings-in-the-zoho-crm-ios-app)** — 12 images
- `https://desk.zoho.in/galleryDocuments/edbsn85f57436a088765ca37a2706066c3a942522f4a5498e98deca59b65793367cc853b940d89c1d7dfc692bbdd9afa481547c32a6755c4a47a9481dd53aecc4ecfb?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn85f57436a088765ca37a2706066c3a9422f417d8030e88ce1918504842fec9c6fa24d7392e29955231290fa5bc0d317237d6c3a7625a504830acdd89afa37c37?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn85f57436a088765ca37a2706066c3a940e32f8bb087dba1581e1a4816b7d996d2e466bef7cc60a8544d1b5be63347d43f09fa587cdd477c58dd678e21b1b02cd?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn85f57436a088765ca37a2706066c3a94e4e66fde670037dab615bdedfcb80e189c96b3684f844fa56e63be5e7e5c311c12f66a29d81c66ed8bccedd7cd6c238a?inline=true`
[View all 12 images in article →](https://help.zoho.com/portal/en/kb/crm/privacy-and-security-settings-in-the-zoho-crm-ios-app)

**[Requester roles for coordination between teams](https://help.zoho.com/portal/en/kb/crm/requester-roles-for-coordination-between-teams)** — 12 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57bf13adb15acc19ef048ceb61d969bb6be414e18e209a0c3a998b6a1264392d888688df7be66c7b714186dc0edb607a06?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5761d56c2192736d58cef311eaa5e9ded46599a44c6a9868a09e4b3d1160e84fc1dff6ca53d5e9674682543b30c5a8b950?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b723ed7ca637d278f6b660de31431cc9c392ce2ac752f6d43bc771c3b35d1405021a641ea84ed1fa6f1791bce16034f1?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5784983048f61e326e6b978a59d0f2d11b8ee101b028cff4680f038d2b904b49d2c8a332a15f730fb10b4e9740c4edafb5?inline=true`
[View all 12 images in article →](https://help.zoho.com/portal/en/kb/crm/requester-roles-for-coordination-between-teams)

**[Admin Tools  for Configuration Management](https://help.zoho.com/portal/en/kb/crm/working-with-admin-tools)** — 9 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574e3f4f64fc20ea58cea903eb303411d661b1fde8e6f75aed5019aa9fb14c5453570e2e8a9e5af7c729a11ec7c346f222?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e1a7250ba89fcf2a811d088a76aa8bde243cf7591beca962671f45ae2617406f54fdee7ab2f523680e4b282344885608?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573d3f2a62d3e8b9a95ffa5bf012249a885812a072ffb832893fd1170bf9043d8bd41ce4af209c630aa2d15d9a17b14b86?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f4b355aebea5e77c40b8344bab288ef4760677fa1e1007d2cbb68eede563a7329614b75e5e8443c3478d16c05aa581bf?inline=true`
[View all 9 images in article →](https://help.zoho.com/portal/en/kb/crm/working-with-admin-tools)

**[Managing Roles](https://help.zoho.com/portal/en/kb/crm/role-management-introduction)** — 8 images
- `https://desklite.zoho.com/DocsDisplay?zgId=674238021&amp;mode=inline&amp;blockId=bcoqzcfbc6adb279f42a284faa09b2ac5c152`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571a589c1b91ae3d0ede1ee67319bd019cbc858151df76664414f00f6b4366b76538a5068cbb280253c7ffbbca5af9fab5?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5734a95d9b676cbd01c4e20c2ae8a1b2b16d93b39f42e5195714b8e3ae028558b4557626ca7a7134ebb3515425d5ba613c?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b576773dd3c40662a7c1b0b24e700321c5d2cd3a572dd427439861ed6933809f9be410cc20f43db54e6f320f14813c0e4b0?inline=true`
[View all 8 images in article →](https://help.zoho.com/portal/en/kb/crm/role-management-introduction)

