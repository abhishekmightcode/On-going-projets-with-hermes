# Customization & Canvas

> **Feature ID:** `14-Customization-Builder`  
> **Knowledge Base Articles:** 218  
> **Last Updated:** 2026-05-05

## Overview

Custom fields, layouts, Canvas design studio, wizards, conditional layouts

---

## 1. Core Functionality

### 1. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 2. Setting up an Unsubscribe Link

Allow the customers to unsubscribe from your email communications by creating an unsubscribe link and embedding it in the emails or hosting on the webpages. You can use the system defined default link or create a custom link. The default unsubscribe link will be available for all users and that cannot be customized. Availability Permission Required Users with the Unsubscribe Form permission in profile can access this feature. Creating an Unsubscribe Link Two essential things you need to set this up are: Location URL It is the web page where the unsubscribe link will be hosted. You can choose a
### 3. FAQs: Data Administration

How can I delete the existing data in my Zoho CRM account and start with a fresh account? You need to manually delete all the data in your account to start a fresh account. You can also close the existing account and sign up for a new Zoho CRM account with the same email address (Not Recommended). Related Link Deleting the Zoho CRM Account How do I delete attachments to free up storage space? When mails (with attachments) are sent using the email template, the attachment is counted only once for your storage, For example, if you send emails to 100 users, the document attached is not counted on
### 4. Charts

Some of the options mentioned in this document are being released in a phased manner and may only be available to specific users. The Dashboards tab is renamed as Analytics for selected accounts. A chart presents data from various records of a module(s) in a visual or graphical representation for an easy analysis. The data is seemingly comprehensible as users can easily pick out the patterns, trends, etc., which may otherwise be difficult to interpret. For example, you are the Sales Manager for Asia Pacific region and want to compare the number of leads created by the sales representatives in
### 5. Field of Lookup

Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list. While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duratio
### 6. Installing the MS Word Plug-in

System Requirements The basic system requirements to install the Zoho CRM Plug-in for Microsoft Word are below: Hardware x486 with minimum of 256 Mb RAM; minimum 10 Mb disk space Operating System Windows 7, 8, and 10 Software Microsoft Word 2010 / 2013 / 2016 Browser Only Internet Explorer (Version 6 and above) Installation Prerequisites You must have sufficient system privileges to install the Zoho CRM Plug-in for Microsoft Word You must have valid login details to connect to the Zoho CRM server You must close all Microsoft Word documents before installing the Plug-in Install Zoho CRM Plug-in
### 7. Zoho CRM for iPhone - An Overview

Zoho CRM for iPhone is a native application that enables you to access and work with your Online Zoho CRM data from your iPhone. The 3.0 version of the native CRM app is available in iOS 8.0 and above. From you iPhone, you can access data from Leads, Accounts, Contacts, Potentials, Cases, Vendors, Products, Tasks, Pricebooks, Sales orders, etc. Availability Permission Required Administrators need to activate it for users in other profiles. Features Zia Voice - Call or Chat with Zia to get answers for all your questions in Zoho CRM. Spotlight - Spotlight Search lets you see the contact informat
### 8. FAQs: Zoho CRM Integration with Zoho Desk

Why should I integrate Zoho CRM with Zoho Desk? Zoho Desk is a cloud-based help desk application that lets you manage and resolve your customer inquiries, complaints, and doubts along with offering self-help articles to help your customers resolve issues themselves. CRM lets your business acquire customers and make deals with them, but what about after-sales services? If your company is poor at providing after-sales services to your customers, it will directly impact your customer retention. Businesses need to be customer-centric and customers shall be the king, but this can only be achieved i


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `CUSTOMIZATION`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Consent Management`
- `Setting up an Unsubscribe Link`
- `FAQs: Data Administration`
- `Charts`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/customization` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Customization & Canvas - Example Implementation
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
- [CRM-Canvas-UI](../CRM-Canvas-UI/README.md)
- [Validation-Rules](../Validation-Rules/README.md)

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


### Setting up an Unsubscribe Link
**Purpose:** Allow the customers to unsubscribe from your email communications by creating an unsubscribe link and embedding it in the emails or hosting on the webpages. You can use the system defined default link

**Key Points:**
Allow the customers to unsubscribe from your email communications by creating an unsubscribe link and embedding it in the emails or hosting on the webpages.
You can use the system defined default link or create a custom link.
The default unsubscribe link will be available for all users and that cannot be customized.
Availability Permission Required Users with the Unsubscribe Form permission in profile can access this feature.
Creating an Unsubscribe Link Two essential things you need to set this up are: Location URL It is the web page where the unsubscribe link will be hosted.
You can choose a standard page designed by Zoho CRM, that will display the information and the link to unsubscribe as a location URL


### FAQs: Data Administration
**Purpose:** How can I delete the existing data in my Zoho CRM account and start with a fresh account? You need to manually delete all the data in your account to start a fresh account. You can also close the exis

**Key Points:**
How can I delete the existing data in my Zoho CRM account and start with a fresh account.
You need to manually delete all the data in your account to start a fresh account.
You can also close the existing account and sign up for a new Zoho CRM account with the same email address (Not Recommended).
Related Link Deleting the Zoho CRM Account How do I delete attachments to free up storage space.
When mails (with attachments) are sent using the email template, the attachment is counted only once for your storage, For example, if you send emails to 100 users, the document attached is not counted on your storage 100 times.
Only the document(s) attached to the template are considered for storage


### Charts
**Purpose:** Some of the options mentioned in this document are being released in a phased manner and may only be available to specific users. The Dashboards tab is renamed as Analytics for selected accounts. A ch

**Key Points:**
Some of the options mentioned in this document are being released in a phased manner and may only be available to specific users.
The Dashboards tab is renamed as Analytics for selected accounts.
A chart presents data from various records of a module(s) in a visual or graphical representation for an easy analysis.
The data is seemingly comprehensible as users can easily pick out the patterns, trends, etc.
, which may otherwise be difficult to interpret.
For example, you are the Sales Manager for Asia Pacific region and want to compare the number of leads created by the sales representatives in the previous year


### Field of Lookup
**Purpose:** Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Stu

**Key Points:**
Overview Lookup fields enable users to associate records between two modules.
Let's say, for example, you have two modules: Students and Courses.
By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list.
While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duration, subjects, course instructor, and so on—you can use the field of lookup module option.
Business scenarios View additional details of a contact in the Deals module Sales associates can view a contact's email address, phone number, referrer, and—alongside the primary lookup field—the contact's name.
They can also view the values in these fields in a report created for the Deals module


### Installing the MS Word Plug-in
**Purpose:** System Requirements The basic system requirements to install the Zoho CRM Plug-in for Microsoft Word are below: Hardware x486 with minimum of 256 Mb RAM; minimum 10 Mb disk space Operating System Wind

**Key Points:**
System Requirements The basic system requirements to install the Zoho CRM Plug-in for Microsoft Word are below: Hardware x486 with minimum of 256 Mb RAM; minimum 10 Mb disk space Operating System Windows 7, 8, and 10 Software Microsoft Word 2010 / 2013 / 2016 Browser Only Internet Explorer (Version 6 and above) Installation Prerequisites You must have sufficient system privileges to install the Zoho CRM Plug-in for Microsoft Word You must have valid login details to connect to the Zoho CRM server You must close all Microsoft Word documents before installing the Plug-in Install Zoho CRM Plug-in for Microsoft Word Installing Zoho CRM Plug-in for Microsoft Word allows you to create mail merge templates based on the CRM data source.
To install the Zoho CRM Plug-in Log in to Zoho CRM with your Username and Password.
Go to Setup > Marketplace > All > Plug-in for Microsoft Word.
In the Zoho CRM Plug-in for Microsoft Word page, click Download Now.
Save/Run the Adventnet_ZohoCRM_Word_Plugin.
exe In the Install Shield Wizard, click Next to start the installation process


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
- [Setting up an Unsubscribe Link](https://help.zoho.com/portal/en/kb/crm/articles/set-unsubscribe-link)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Charts](https://help.zoho.com/portal/en/kb/crm/articles/create-charts)
- [Field of Lookup](https://help.zoho.com/portal/en/kb/crm/articles/field-of-lookup)
- [Installing the MS Word Plug-in](https://help.zoho.com/portal/en/kb/crm/articles/install-ms-word-plug-in-crm-integration)
- [Zoho CRM for iPhone - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-iphone-an-overview)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [Including Opt-in Checkbox in Web Forms for Consent](https://help.zoho.com/portal/en/kb/crm/articles/opt-in-checkbox)
- [Lead Queue for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/lead-queue-for-zoho-crm)
- [SharePoint for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/sharepoint-for-zoho-crm)
- [HubSpot for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/hubspot-for-zoho-crm)
- [FAQs: Working with Emails](https://help.zoho.com/portal/en/kb/crm/articles/faq-working-with-emails)
- [Converting Leads](https://help.zoho.com/portal/en/kb/crm/articles/convert-leads)
- [Requesting Data Backup](https://help.zoho.com/portal/en/kb/crm/articles/requesting-data-backup)
- [Integrating Zoho Campaigns with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/zoho-campaigns-crm-integration)
- [Booking appointments for services](https://help.zoho.com/portal/en/kb/crm/articles/booking-appointments-for-services)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [FAQs: Data Enrichment](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-enrichment)
- [Troubleshooting Sales Pipelines](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-pipelines)
- [Associate a contact with multiple companies or accounts](https://help.zoho.com/portal/en/kb/crm/articles/associate-a-contact-with-multiple-companies-or-accounts)
- [Customizing the navigation bar in the Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/customizing-the-navigation-bar-in-the-zoho-crm-ios-app)
- [Building Formula Fields](https://help.zoho.com/portal/en/kb/crm/articles/build-formula-fields)
- [Frequently Asked Questions on CRM for Everyone](https://help.zoho.com/portal/en/kb/crm/articles/frequently-asked-questions-on-crm-for-everyone)
- [FAQs: Page layouts](https://help.zoho.com/portal/en/kb/crm/articles/faqs-page-layouts)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
