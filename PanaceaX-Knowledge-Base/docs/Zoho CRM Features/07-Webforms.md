# Webforms & Lead Capture

> **Feature ID:** `07-Webforms`  
> **Knowledge Base Articles:** 59  
> **Last Updated:** 2026-05-05

## Overview

Web form creation, A/B testing, consent management, and form analytics

---

## 1. Core Functionality

### 1. Consent Management

Zoho CRM's consent management settings help you get consent from your prospects and customers. We provide a system where you can customize the consent form, include it in your email templates, set consent-related preferences, and most importantly, get assistance in keeping track of consent details. Consent can be applied to records in the Contacts, Leads, Vendors, and custom org modules. It cannot be applied for team modules. Upon enabling GDPR Compliance Settings in Zoho CRM, you can start marking lawful basis for data processing and get the essential consent as the case may be. You will begi
### 2. Data Privacy

A record's details are available in two sections - Info and Timeline. When you switch on GDPR Compliance in your Zoho CRM account, you will be able to view another section, namely Data Privacy . This section has the following details: Data Source Personal Fields Data Processing Bases View Data Source Data Subject information can be pushed into Zoho CRM from multiple sources such as the web-forms, by importing, APIs and third-party integrations. Data Source displays the information about how the record was Created and when it was Last Updated . Along with these information, additional details w
### 3. Including Opt-in Checkbox in Web Forms for Consent

You may already have some Zoho CRM web forms in use that are published in your website. You need to follow the steps given below to add a consent checkbox to those web form. The same steps can also be followed to include consent checkbox in a new form. Step 1 - Create a Consent/Opt-in field in your Zoho CRM account. First, create a checkbox type field that will store the consent information. See Also Create Custom Fields Go to Setup > Customization > Modules and Fields . Click the desired module and choose a layout. From the New Fields Tray on the left, drag and drop the checkbox field type in
### 4. Webform Analytics

Analyse, measure and enhance your webforms based on various metrics in Zoho CRM Help guide: Webform Analytics
### 5. Setting Assignment Rules

A sales success is closely coupled with the everyday activities of the reps, such as - number of follow-ups, promptness in getting back to the customers, offering quick answers to their queries, and responding to the support tickets. All these factors play a crucial role in moving the leads rapidly through the sales funnel, eventually leading to a successful sale closure. An important aspect in achieving the above depends on how well-organized and planned the lead assignment process in an organization is. Most businesses rely on multiple sources to generate leads. With each lead/customer havin
### 6. Webform Analytics

Webforms are the most common tool used by organizations for lead generation. As the lead submits the form their information is captured in CRM from where the reps take it up for the further follow-ups and nurturing processes. Read more about creating webforms . Most of the times, organizations host multiple webpages that help them focus on a wider audience and generate more leads. It is also important to analyze the performance of each webform to understand if they are serving the desired purpose. There are several parameters that can help you determine the performance: Number of visits to the
### 7. Setting up Webforms

Creating a webform involves three steps: Building the form - Drag and drop fields to build a form and format it easily with the WYSIWYG editor. Specifying the form details - Add details such as form name, landing page URL (where the visitor needs to be redirected after the form is submitted) record assignment rule, notification details, etc. Generating the code for the form - Embed the form using various code formats. Codes for some third-party sites (WordPress, Google Sites, Facebook, and Joomla) are readily available. You can build webforms to generate records for the Leads , Contacts , Case
### 8. Pushing Data to Google Ads

Pushing data form Zoho CRM to Google Ads help you understand which clicks led to which offline conversions. You can get a complete picture of the click-to-conversion cycle and accurately analyze your spending. Additionally, you can leverage bid automation features to optimize for offline conversions. Data from Zoho CRM is pushed into three conversion components: Zoho CRM Leads/Contacts - For each lead/contact created in Zoho CRM, a count increases for this component. Conversion Count is set as UniqueConversion . Conversion Category is set as Signup . Zoho CRM Lead Qualification - For each lead


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `WEBFORMS`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Consent Management`
- `Data Privacy`
- `Including Opt-in Checkbox in Web Forms for Consent`
- `Webform Analytics`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/webforms` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Webforms & Lead Capture - Example Implementation
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

- [Leads-Management](../Leads-Management/README.md)
- [Workflow-Automation](../Workflow-Automation/README.md)
- [Email-Tools](../Email-Tools/README.md)
- [Consent-Management](../Consent-Management/README.md)

### This Feature Enables

- **Leads-Management** -- shares data model and workflows
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


### Data Privacy
**Purpose:** A record's details are available in two sections - Info and Timeline. When you switch on GDPR Compliance in your Zoho CRM account, you will be able to view another section, namely Data Privacy . This

**Key Points:**
A record's details are available in two sections - Info and Timeline.
When you switch on GDPR Compliance in your Zoho CRM account, you will be able to view another section, namely Data Privacy.
This section has the following details: Data Source Personal Fields Data Processing Bases View Data Source Data Subject information can be pushed into Zoho CRM from multiple sources such as the web-forms, by importing, APIs and third-party integrations.
Data Source displays the information about how the record was Created and when it was Last Updated.
Along with these information, additional details will also be available as listed in the table below.
Source (Feature) Data Tracking Last Updated Details Source (Feature) Data Tracking Last Updated Details Zoho Finance Suite Portal Name - Google Calendar Sync Calendar, Account Id or Email - Zoho Desk Portal name, Department Portal name, Department Office 365 Calendar Sync Account Id or Email - Zoho Survey Survey Name, Department Survey Name, Department API Service Name Service Name Zoho Projects Tasks/Notes Portal name, Project Name - Custom Functions Service name Service name Zoho Calendar Folder name, Account Id or Email - Social Network Name, created_type - BCC dropbox From Address Not displayed MS Outlook Service name - Mail Parser From Address, Parser Name Not displayed Zoho SalesIQ Portal name, Screen name Portal name, Screen name Email Workflow Workflow Name, Workflow Id


### Including Opt-in Checkbox in Web Forms for Consent
**Purpose:** You may already have some Zoho CRM web forms in use that are published in your website. You need to follow the steps given below to add a consent checkbox to those web form. The same steps can also be

**Key Points:**
You may already have some Zoho CRM web forms in use that are published in your website.
You need to follow the steps given below to add a consent checkbox to those web form.
The same steps can also be followed to include consent checkbox in a new form.
Step 1 - Create a Consent/Opt-in field in your Zoho CRM account.
First, create a checkbox type field that will store the consent information.
See Also Create Custom Fields Go to Setup > Customization > Modules and Fields


### Webform Analytics
**Purpose:** Analyse, measure and enhance your webforms based on various metrics in Zoho CRM Help guide: Webform Analytics

**Key Points:**
Analyse, measure and enhance your webforms based on various metrics in Zoho CRM Help guide: Webform Analytics


### Setting Assignment Rules
**Purpose:** A sales success is closely coupled with the everyday activities of the reps, such as - number of follow-ups, promptness in getting back to the customers, offering quick answers to their queries, and r

**Key Points:**
A sales success is closely coupled with the everyday activities of the reps, such as - number of follow-ups, promptness in getting back to the customers, offering quick answers to their queries, and responding to the support tickets.
All these factors play a crucial role in moving the leads rapidly through the sales funnel, eventually leading to a successful sale closure.
An important aspect in achieving the above depends on how well-organized and planned the lead assignment process in an organization is.
Most businesses rely on multiple sources to generate leads.
With each lead/customer having disparate requirements, it is best to avoid assigning them randomly to the reps.
Instead, they could be assigned to reps who have an expertise with managing leads from a region or a specific product


### Webform Analytics
**Purpose:** Webforms are the most common tool used by organizations for lead generation. As the lead submits the form their information is captured in CRM from where the reps take it up for the further follow-ups

**Key Points:**
Webforms are the most common tool used by organizations for lead generation.
As the lead submits the form their information is captured in CRM from where the reps take it up for the further follow-ups and nurturing processes.
Read more about creating webforms.
Most of the times, organizations host multiple webpages that help them focus on a wider audience and generate more leads.
It is also important to analyze the performance of each webform to understand if they are serving the desired purpose.
There are several parameters that can help you determine the performance: Number of visits to the webforms Number of submissions Percentage of fields that are usually filled in the form Whether the leads have any deals associated with them The best part is that, all these insights are made available to you for each web page where you are tracking the form inside CRM


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
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy)
- [Including Opt-in Checkbox in Web Forms for Consent](https://help.zoho.com/portal/en/kb/crm/articles/opt-in-checkbox)
- [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/articles/webform-analytics-2-7-2021)
- [Setting Assignment Rules](https://help.zoho.com/portal/en/kb/crm/articles/set-assignment-rules)
- [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/articles/webform-analytics)
- [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/articles/set-up-web-forms)
- [Pushing Data to Google Ads](https://help.zoho.com/portal/en/kb/crm/articles/push-data-to-google-ads)
- [Zoho CRM Webforms for Google Sites](https://help.zoho.com/portal/en/kb/crm/articles/web-forms-google-sites)
- [Awaiting Records](https://help.zoho.com/portal/en/kb/crm/articles/approve-records)
- [Data Subject Rights](https://help.zoho.com/portal/en/kb/crm/articles/data-subject-rights)
- [Creating Leads](https://help.zoho.com/portal/en/kb/crm/articles/create-leads)
- [Tagging Records in CRM](https://help.zoho.com/portal/en/kb/crm/articles/tagging-records-in-crm)
- [Auto-response rules for webforms](https://help.zoho.com/portal/en/kb/crm/articles/web-form-auto-response-rule)
- [Working with Zoho Forms Integration](https://help.zoho.com/portal/en/kb/crm/articles/zoho-forms-crm-integration)
- [Troubleshooting Zoho Campaigns integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-campaigns-integration-for-zoho-crm)
- [Marketing Automation - An Overview](https://help.zoho.com/portal/en/kb/crm/articles/marketing-automation)
- [FAQs: GDPR Compliance](https://help.zoho.com/portal/en/kb/crm/articles/faqs-on-gdpr)
- [Editing Criteria Patterns in Reports](https://help.zoho.com/portal/en/kb/crm/articles/editing-criteria-patterns)
- [Email Parser — Overview](https://help.zoho.com/portal/en/kb/crm/articles/nextegn-email-parser-overview)
- [Creating Custom Tabs](https://help.zoho.com/portal/en/kb/crm/articles/custom-tabs-creator-crm-integration)
- [Data Privacy](https://help.zoho.com/portal/en/kb/crm/articles/data-privacy-in-zoho-crm-android-app)
- [GDPR Compliance](https://help.zoho.com/portal/en/kb/crm/articles/gdpr-compliance)
- [FAQs on Page Layouts](https://help.zoho.com/portal/en/kb/crm/articles/page-layout-faq)
- [Send automatic notifications to the third-party providers](https://help.zoho.com/portal/en/kb/crm/articles/workflow-webhook-scenario)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **6 KB articles** with **102 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Webform Analytics](https://help.zoho.com/portal/en/kb/crm/webform-analytics) | 32 | [View Article](https://help.zoho.com/portal/en/kb/crm/webform-analytics) |
| 2 | [Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/set-up-web-forms) | 23 | [View Article](https://help.zoho.com/portal/en/kb/crm/set-up-web-forms) |
| 3 | [Webform A/B Testing](https://help.zoho.com/portal/en/kb/crm/webform-ab-testing) | 22 | [View Article](https://help.zoho.com/portal/en/kb/crm/webform-ab-testing) |
| 4 | [FAQs: Webforms](https://help.zoho.com/portal/en/kb/crm/faqs-webforms) | 14 | [View Article](https://help.zoho.com/portal/en/kb/crm/faqs-webforms) |
| 5 | [Auto-response rules for webforms](https://help.zoho.com/portal/en/kb/crm/web-form-auto-response-rule) | 8 | [View Article](https://help.zoho.com/portal/en/kb/crm/web-form-auto-response-rule) |
| 6 | [Including Opt-in Checkbox in Web Forms for Consent](https://help.zoho.com/portal/en/kb/crm/opt-in-checkbox) | 3 | [View Article](https://help.zoho.com/portal/en/kb/crm/opt-in-checkbox) |

### Sample Image URLs (from top articles)
**[Webform Analytics](https://help.zoho.com/portal/en/kb/crm/webform-analytics)** — 32 images
- `https://desk.zoho.in/galleryDocuments/edbsn9214836d08309dddcd341dd5cc1d4eedf09f5ebe711587a3014a0626c14cd9aff4b51fe4bfae29ee3650b7734547615ee79078307c388f3d637ecc811ca9fb03?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn9214836d08309dddcd341dd5cc1d4eed86db6d3e28616b88988bc79ff0c19d3596259eb9102abb91a06554259769c1a30e350f74a13361ddddbd048b807f5b52?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn9214836d08309dddcd341dd5cc1d4eed39414a66f898a808292a0c4df4ecdaf3cb7902a313dbe800dc103e11d0c1034f7b09154f78b4b3b50c1fd9a81a63a4b4?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsn9214836d08309dddcd341dd5cc1d4eed448119f43e743ce1d4d0b0eb0c006f0afb1275bb4b283da59e8cb1fa6e9840609263deac3d8b1ed630f372876dabc82b?inline=true`
[View all 32 images in article →](https://help.zoho.com/portal/en/kb/crm/webform-analytics)

**[Setting up Webforms](https://help.zoho.com/portal/en/kb/crm/set-up-web-forms)** — 23 images
- `https://desk.zoho.in/galleryDocuments/edbsna63cb8738e51b37a0da094736865778be1c8d6930ab94f8eeb723da63c0aabe4b42ab5a2aee04a94d24362c4d7b3587e8c7ce11878e13d7cbd5ace1ccbee8d50?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b573e255007423282b39e5583b86007b274d93f44c0ae05249ce51b9c5f23b288f321f2844b31decebf63a9848ddbe64052?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsna63cb8738e51b37a0da094736865778b8dc7ed79cae61a0c147079fa7cd05a8a2ac706b36388e111053d4f4873d1e1b857e94f1131c590b2d1ee00adcd469b51?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsna63cb8738e51b37a0da094736865778bb5f5029e970dc373ce56ae7c50d6c185e803ba9a6624b6f6512a594e85b98f3cbc106ebd3e6fb7484daab132c0af9ce1?inline=true`
[View all 23 images in article →](https://help.zoho.com/portal/en/kb/crm/set-up-web-forms)

**[Webform A/B Testing](https://help.zoho.com/portal/en/kb/crm/webform-ab-testing)** — 22 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b576a14d1c5dbf159ba1cc90d33d7a63bd36f80528dd5ec30c470b739172982a96fe9402dc1d36bdd1cbd9409e084b4d3b7?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5767ea357ac049f0fa6204f52c35179c56cfd435dbb3483b3dfd26a43ce1a4e310469018073fe5f0a8f4447b804530ea70?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5768f1ee30feaea03cea14f8290e2e9cffbb3dfeb9ccac6f4f038a8bba7fff90badd4eddab53500b5717e880615914d444?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5742948e912a78fe9a0e50a9a01e3526d72e2fb712c3218be6655fc79e61326bc009b8b5f497adb424ecce29408104099e?inline=true`
[View all 22 images in article →](https://help.zoho.com/portal/en/kb/crm/webform-ab-testing)

**[FAQs: Webforms](https://help.zoho.com/portal/en/kb/crm/faqs-webforms)** — 14 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b576f00601d152e0f82145cf8e57f8a06cbb06ea99771258dfa91ff40ec50c719b5c1151ccd305fcf2950de59cc8cf67993?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5758ef23a560d837e3a37e9a879ba8e7c6903c9159af36efee5a6ad108fed96667356265cb09bd6ecfb1c762f6d682fcf2?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5707514463d06814638fa60c6e109028e0dd3b09c1a611b6046337f27a4e54507782a80208df431c0ac011c0a69883b360?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57a56c97bd9abf730fa4315152961a95ed183a32de75e7ecac4d90f6335a9f942e3ef0d52b35a76b49938235c9074ae261?inline=true`
[View all 14 images in article →](https://help.zoho.com/portal/en/kb/crm/faqs-webforms)

**[Auto-response rules for webforms](https://help.zoho.com/portal/en/kb/crm/web-form-auto-response-rule)** — 8 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b577452010edbba36486e72120fde12e105d564b36559552ede53f2acf382f1965c8e8a3cbfe0294067a68fc3039cfec60e?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5742bde8de07498592216501030dcdf40b2262393eaea581524762ec495fb60f593b69132eee9b637de1083bb8dcf831f5?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57cca4cdfb96f89b5856d9cdb5203ba951425c5e3d04caf8700dea293d00907b72efec8531f4096b8c50f68867f99659f0?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b5705fa34710518845b338e4391d730e8fac49f5750618e0a3ec2c719642104641709506511d035c4ed5e1ef0a0d99cc526?inline=true`
[View all 8 images in article →](https://help.zoho.com/portal/en/kb/crm/web-form-auto-response-rule)

