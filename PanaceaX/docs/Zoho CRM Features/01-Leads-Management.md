# Leads Management

> **Feature ID:** `01-Leads-Management`  
> **Knowledge Base Articles:** 389  
> **Last Updated:** 2026-05-05

## Overview

Complete lead lifecycle management from capture to conversion

---

## 1. Core Functionality

### 1. FAQs: Zoho CRM for Google Ads

Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration. However, this does not erase the details fetched from the previous accounts. Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts. Can I configure more than one client account with Zoho CRM? Yes. If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would w
### 2. Schedule annual notifications for subscription renewals

Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines. Every month, they publish new editions of the magazines. The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team. The sales agents send reminder emails to the existing customers for annual subscription renewal. If the subscription is renewed, they are sent the magazines every month. To be sure that the renewal payment is made o
### 3. Zoho CRM for Google Ads

Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites. By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI). Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to ma
### 4. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 5. FAQs: Data Administration

How can I delete the existing data in my Zoho CRM account and start with a fresh account? You need to manually delete all the data in your account to start a fresh account. You can also close the existing account and sign up for a new Zoho CRM account with the same email address (Not Recommended). Related Link Deleting the Zoho CRM Account How do I delete attachments to free up storage space? When mails (with attachments) are sent using the email template, the attachment is counted only once for your storage, For example, if you send emails to 100 users, the document attached is not counted on
### 6. Setting up Zoho Writer Add-on

Zoho Writer is an online word processor that allows you to create and share documents online. Using the Zoho Writer Zoho Add-on in Zoho CRM, you can create templates online and use CRM data (Leads, Accounts, Contacts and Potentials) to create mail merge documents such as Forms, Letters, Address Labels, Envelopes etc. on-the-fly. You can use this function without downloading and installing any software. Note With the Zoho Writer Add-on, you can create the mail merge documents using the data from Leads , Accounts , Contacts and Potentials modules only. Availability Permission Required Users with
### 7. Kaizen posts 2024: Widget series

Here is a complete list of Kaizen posts related to Widgets published in 2024 . Sl. No. Title Description 1 How is a Widget used in a Blueprint? Learn how to create widgets and use them in your Zoho CRM account from this post. 2 Geocoding Leads' Addresses in ZOHO CRM Learn how to create a Related List Widget map in Zoho CRM's Lead detail page with lead location display, directions from the current user's location, and showcasing other leads in the same street or city as the current lead. 3 Zoho CRM Widgets using ReactJS Explore how to use ReactJS and other client-side frameworks for Zoho CRM wi
### 8. FAQs: Developer Hub

How can I fetch the data from the Leads module to my application using an API? You can use the Zoho CRM REST API to retrieve data from the Leads module and other modules. Refer to this document for more details. Is the API key user-specific or organization-specific? The Zoho CRM API key is organization-specific. You can use the same API Key for all users with different ticket IDs (user-specific). What is the format of the xmlData parameter to associate a task or event to CRM records? Use the following sample XML for relating an event with the account and contact respectively. Account <Events><


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `LEADS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `FAQs: Zoho CRM for Google Ads`
- `Schedule annual notifications for subscription renewals`
- `Zoho CRM for Google Ads`
- `Consent Management`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/leads` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Leads Management - Example Implementation
// Triggered on record creation/update

if(input.module == "FAQS: ZOHO CRM FOR GOOGLE ADS")
{
    // Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of clien
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

- [Contacts-Management](../Contacts-Management/README.md)
- [Deals-Pipeline](../Deals-Pipeline/README.md)
- [Activities](../Activities/README.md)
- [Assignment-Rules](../Assignment-Rules/README.md)
- [Workflow-Automation](../Workflow-Automation/README.md)
- [Scoring-Rules](../Scoring-Rules/README.md)

### This Feature Enables

- **Contacts-Management** -- shares data model and workflows
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

### FAQs: Zoho CRM for Google Ads
**Purpose:** Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM? Yes. You can choose a different set of client accounts that you want to be tracked inside Zoho

**Key Points:**
Can I choose another list of client accounts at a later point after Google Ads integration with Zoho CRM.
You can choose a different set of client accounts that you want to be tracked inside Zoho CRM at any point after integration.
However, this does not erase the details fetched from the previous accounts.
Zoho CRM will simply stop tracking the previous accounts and start tracking the new client accounts.
Can I configure more than one client account with Zoho CRM.
If the Google Ads account being integrated is an MCC account, you can select any or all client accounts that you would want to be tracked inside Zoho CRM


### Schedule annual notifications for subscription renewals
**Purpose:** Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.

**Key Points:**
Edition: Enterprise | Industry: Media and Publishing | Feature: Workflow Rule Scenario The Zylker Weekly is one of the leading international publishers of Travel and Tourism and Hospitality magazines.
Every month, they publish new editions of the magazines.
The interested readers can subscribe to their annual subscription package by sending an email request to their marketing team.
The sales agents send reminder emails to the existing customers for annual subscription renewal.
If the subscription is renewed, they are sent the magazines every month.
To be sure that the renewal payment is made on time, they require a process to automatically start sending reminder emails 15 days before the renewal date, and upgrade the subscription status based on the payment


### Zoho CRM for Google Ads
**Purpose:** Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner we

**Key Points:**
Google Ads is a powerful online advertising program designed to help you reach new customers and increase sales for your business through ads on Google Search and across Google's network of partner websites.
By helping you drive more traffic to your site from visitors who are likely to be interested in what your business has to offer, Google Ads helps you capture more qualified leads for a better return on your online marketing investment (ROI).
Google Ads' flexible online marketing platform includes comprehensive analytics and reporting tools, giving you easy access to the data you need to make strategic marketing decisions for your business.
If you use Google Ads to drive potential customers to your website and a customer relationship management system (CRM) to track offline sales made through phone calls, emails, or direct sales, it can be difficult for your business to determine how your online campaign investments lead to offline conversion data stored in Zoho CRM.
With Zoho CRM for Google Ads , you can now import your Google Ads marketing investments into Zoho CRM so you can see which keywords and campaigns are responsible for each offline sale.
Plus, you can also export Zoho CRM sales data into Google Ads so you can better optimize your bids and budgets to yield maximum revenue and profits


### Consent Management
**Purpose:** Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set con

**Key Points:**
Zoho CRM's consent management settings help you get consent from your prospects and customers.
We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details.
Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules.
It cannot be applied for team modules.
Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be.
You will begin by marking the records whose data needs to be processed after obtaining consent


### FAQs: Data Administration
**Purpose:** How can I delete the existing data in my Zoho CRM account and start with a fresh account? You need to manually delete all the data in your account to start a fresh account. You can also close the exis

**Key Points:**
How can I delete the existing data in my Zoho CRM account and start with a fresh account.
You need to manually delete all the data in your account to start a fresh account.
You can also close the existing account and sign up for a new Zoho CRM account with the same email address (Not Recommended).
Related Link Deleting the Zoho CRM Account How do I delete attachments to free up storage space.
When mails (with attachments) are sent using the email template, the attachment is counted only once for your storage, For example, if you send emails to 100 users, the document attached is not counted on your storage 100 times.
Only the document(s) attached to the template are considered for storage


### Setting up Zoho Writer Add-on
**Purpose:** Zoho Writer is an online word processor that allows you to create and share documents online. Using the Zoho Writer Zoho Add-on in Zoho CRM, you can create templates online and use CRM data (Leads, Ac

**Key Points:**
Zoho Writer is an online word processor that allows you to create and share documents online.
Using the Zoho Writer Zoho Add-on in Zoho CRM, you can create templates online and use CRM data (Leads, Accounts, Contacts and Potentials) to create mail merge documents such as Forms, Letters, Address Labels, Envelopes etc.
You can use this function without downloading and installing any software.
Note With the Zoho Writer Add-on, you can create the mail merge documents using the data from Leads , Accounts , Contacts and Potentials modules only.
Availability Permission Required Users with the Zoho Writer Add-on permission in their profile.
Benefits Requires no installation as you can create templates online using Zoho Writer


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

- [FAQs: Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/faqs-google-adwords)
- [Schedule annual notifications for subscription renewals](https://help.zoho.com/portal/en/kb/crm/articles/automatic-schedule-notifications)
- [Zoho CRM for Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/google-ads-crm-integration)
- [Consent Management](https://help.zoho.com/portal/en/kb/crm/articles/consent-management)
- [FAQs: Data Administration](https://help.zoho.com/portal/en/kb/crm/articles/faqs-data-administration)
- [Setting up Zoho Writer Add-on](https://help.zoho.com/portal/en/kb/crm/articles/zoho-writer-crm-integration)
- [Kaizen posts 2024: Widget series](https://help.zoho.com/portal/en/kb/crm/articles/widgets-2024)
- [FAQs: Developer Hub](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-developer-hub)
- [Managing Web Tabs](https://help.zoho.com/portal/en/kb/crm/articles/web-tabs)
- [Charts](https://help.zoho.com/portal/en/kb/crm/articles/create-charts)
- [What is ABM?](https://help.zoho.com/portal/en/kb/crm/articles/what-is-abm)
- [NaijaSMSPortal for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/naijasmsportal-for-zoho-crm)
- [Setting Email Notifications](https://help.zoho.com/portal/en/kb/crm/articles/set-email-notifications)
- [Address Locator for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/address-locator-for-zoho-crm)
- [WeChat for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/wechat-for-zoho-crm-3-8-2021)
- [Zoho CRM for iPhone - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-iphone-an-overview)
- [FAQs: Zoho CRM Integration with Zoho Desk](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-integration-zoho-desk)
- [Lead Queue for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/lead-queue-for-zoho-crm)
- [SharePoint for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/sharepoint-for-zoho-crm)
- [Zoho Survey Integration - Overview](https://help.zoho.com/portal/en/kb/crm/articles/zoho-survey-crm-integration)
- [Working with notes in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/working-with-notes-in-zoho-crm-ios-app)
- [Setting Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/set-assignment-rules)
- [Understanding and building reports](https://help.zoho.com/portal/en/kb/crm/articles/understanding-and-building-reports)
- [Team modules in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/articles/team-modules-in-zoho-crm-ios-app)
- [Installing the CRM Mobile App](https://help.zoho.com/portal/en/kb/crm/articles/installing-crm-mobile-app)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **9 KB articles** with **45 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Converting Leads](https://help.zoho.com/portal/en/kb/crm/convert-leads) | 22 | [View Article](https://help.zoho.com/portal/en/kb/crm/convert-leads) |
| 2 | [Associating lead referrals to the respective contacts](https://help.zoho.com/portal/en/kb/crm/create-lead-from-contact-using) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-lead-from-contact-using) |
| 3 | [Creating Leads](https://help.zoho.com/portal/en/kb/crm/create-leads) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-leads) |
| 4 | [FAQs: Leads Management](https://help.zoho.com/portal/en/kb/crm/faqs-on-leads-management) | 5 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-on-leads-management) |
| 5 | [Lead Queue for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/lead-queue-for-zoho-crm) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/lead-queue-for-zoho-crm) |
| 6 | [Create a system-defined, guided sales process for a step-by-step lead conversion](https://help.zoho.com/portal/en/kb/crm/create-system-defined-sales-process-for-a-step-by-step-lead-conversion) | 2 | [View Article](https://help.zoho.com/portal/en/kb/crm/create-system-defined-sales-process-for-a-step-by-step-lead-conversion) |
| 7 | [Sales process: Lead generation](https://help.zoho.com/portal/en/kb/crm/sales-process-lead-generation) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/sales-process-lead-generation) |
| 8 | [Converting leads in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/converting-leads-in-zoho-crm-ios-app) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/converting-leads-in-zoho-crm-ios-app) |
| 9 | [Working With Leads](https://help.zoho.com/portal/en/kb/crm/leads-26-4-2026) | 1 | [View Article](https://help.zoho.com/portal/en/kb/crm/leads-26-4-2026) |

### Sample Image URLs (from top articles)
**[Converting Leads](https://help.zoho.com/portal/en/kb/crm/convert-leads)** — 22 images
- `https://www.zoho.com/crm/help/img/lead-conversion.png`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ba9570e069d0066bc1b10ba5b521f4f798648f7d04eb7cb2ee0af5d83bd3de247fc7020c03f7d1fbd4cbef2bdd972084?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573608f392f7ede4d8c744d14115a00c9fcef38555057110488e229d8871ac3951af41b9755c7684482524f75243c5bd69?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e430a9b13da0d5ca3a70f30722096d13f11541c72e84aedd07c1dbe2f7088fbf7dbb3564825e958c04e0a7fc7cef562f?inline=true`
[View all 22 images in article →](https://help.zoho.com/portal/en/kb/crm/convert-leads)

**[Associating lead referrals to the respective contacts](https://help.zoho.com/portal/en/kb/crm/create-lead-from-contact-using)** — 5 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b577c6d8f78a87cadf7ea2584f39add58be5d218f4324b50ebbcdeab3a89aefecd5ddb0a611e1b61fd5105f80a753122140?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571aefedea729185d6bc9bb38c3f4bb0d1a92d7ee40f41d7d11c98329cf6b698fb1461ba4bf0551cd4a0c9c646bfbfc070?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575042029e450c929a5d564b070615fc5fea5fe2ab989f8c5296466f5e2f09c732e09fd65f1df3b163de005542e09495af?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b575bc6aa2acca256b956b99c6e7af93339ce9e476e0111ee160cfc53dfcdf8b6f18d71d643909479260ce690ee6ec9ab87?inline=true`
[View all 5 images in article →](https://help.zoho.com/portal/en/kb/crm/create-lead-from-contact-using)

**[Creating Leads](https://help.zoho.com/portal/en/kb/crm/create-leads)** — 5 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d1685a3f4bcaca4a9e2a3ec861654a28ce1ecc1e0a6a95ff885fdb0076d083f0ed92fdfeaf9b7d05ccf023f35deca7ec?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ed945de4498f564df801050abda231a94898933bff35bee7a3ee577313c2e0499bd24a542c51210b7f9c566e4360e4ca?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57b99ccfa215eb9aee3650c29598ffae9199b32fabb456c9e3c4098174e707f2f4cb1d6ac974867a2d2f04f92682054312?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5748c5c7edb90e0827b87f064de712d7864fd5c66e007536439604d541dff17fbce3e43d88311b92ad91f6a634a18f76e8?inline=true`
[View all 5 images in article →](https://help.zoho.com/portal/en/kb/crm/create-leads)

**[FAQs: Leads Management](https://help.zoho.com/portal/en/kb/crm/faqs-on-leads-management)** — 5 images
- `http://support.zoho.com/ImageDisplay?downloadType=uploadedFile&amp;fileName=lead%2Bconversion.png&amp;blockId=48d0a45894056572c1ae46021c0c75a360713b36d96b65a5&amp;zgId=b54d79c69095249d&amp;mode=view`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57cc7d074b50fbea340049e48246a2614eed96584e57097e60d476aa8ac3e311e4abb4891f9b40f741fd794f34f5f5de15?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57c65e37745989b680c1942541e9cfd6bcdad1d759520d7ef6a8ae8ce916261d9c9f575d158aaa653136f0688f25b6dc22?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57c81f7aa10500516b411ae0e249d635117b36002679496cd3d5ebe490f94a6b06a1a20aa0f0fb33ae49a0cecedc41e1e9?inline=true`
[View all 5 images in article →](https://help.zoho.com/portal/en/kb/crm/faqs-on-leads-management)

**[Lead Queue for Zoho CRM](https://help.zoho.com/portal/en/kb/crm/lead-queue-for-zoho-crm)** — 3 images
- `https://www.zohowebstatic.com/sites/default/files/lead-queue-install.png`
- `https://www.zohowebstatic.com/sites/default/files/Leadqueue-create.png`
- `https://www.zohowebstatic.com/sites/default/files/Leadqueue-options.png`
[View all 3 images in article →](https://help.zoho.com/portal/en/kb/crm/lead-queue-for-zoho-crm)

