# Sandbox Environments

> **Feature ID:** `23-Sandbox`  
> **Knowledge Base Articles:** 27  
> **Last Updated:** 2026-05-05

## Overview

Sandbox environments for testing customizations, integrations, and configurations before production

---

## 1. Core Functionality

### 1. Setting up Zoho Creator Integration

Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account. You should have a Zoho Creator account with any edition. If you do not have a Zoho Creator account, please create an account from Zoho Create. An account with the Free Edition will be automatically created. After which you can proceed with integrating it with Zoho CRM. Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for t
### 2. Configuring SAML-based SSO in CRM portals

This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users. For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview . Prerequisite Glossary Prerequisite Editions: Enterprise and Ultimate Bundles (CRMPlus and Zoho One) Trial: No Developer: No Sandbox: No Mobile: No Permission : Users with the Manage Portals permission (Under Setup permissions > Admin level permissions ) can configure SAML based SSO for their CRM's portal and manage it. Glossary Authentication Authentication is the process of confirming a user's id
### 3. An overview of user management in Zoho CRM

A CRM user is an individual who transforms rich customer data into timely and well-informed actions. CRM users can include members from sales, marketing, customer success, legal, and other teams who rely on customer or deal context to do their jobs well. In Zoho CRM, you can purchase user licenses and invite, remove, activate, or deactivate such users per your changing needs. Types of CRM users There are two kinds of users in Zoho CRM: Regular users are those who are given broad or selective access to CRM data and capabilities. This access depends on their assigned profiles, which are fully cu
### 4. Troubleshooting Sales Pipelines

I created a pipeline and now I cannot update the Stage field in a record. Creating a pipeline does not affect updating stages in the layout. If a map dependency, blueprint, layout rule, or validation rule has been created based on the Stage field, then you won't be able to update the Stage field. How can I map the pipeline and stage during Hubspot (API) migration? By default , the stage and pipeline in HubSpot are automatically mapped to the Stage and Pipeline fields in Zoho CRM and you cannot alter this mapping during API migration. If you need to migrate stages and pipelines in a different f
### 5. Social integration in sandbox

Social media platforms like Twitter and Facebook have become vital for understanding and engaging customers. Zoho CRM allows you to monitor and engage with these platforms from within your CRM. This is possible because of the Zoho Social integration (available through the Social tab). You can test your Zoho Social integration in a sandbox before using it in your production environment. This allows you to simulate the effects of the integration on your CRM system and on your internal processes. Once you've tested the integration to a satisfactory level, you can confidently deploy it to the prod
### 6. FAQs: Zoho CRM Integration with Zoho Projects

How is the integration between Zoho CRM and Zoho Projects helpful? The integration between Zoho CRM and Zoho Projects works as a bridge between sales data and team collaboration data—all in one place. Since you can associate projects directly with customers, you can plan and manage your tasks more efficiently and make better business decisions, as you can associate projects directly with customers. Integrating business and sales data with production data improves the quality of work, and thereby the overall revenue and growth of your business, as well as your clients. Every project involves mu
### 7. Use Cases for Validation Rules Using Functions

Make detailed description mandatory if specific terms are entered in the field Zylker Tech manufactures electronic assemblies and similar other products. Their manufactured items are outsourced for quality check to a third-party service provider. The assessment results are shared with the production managers through the assessment and evaluation report. Often times it has happened that important fields in the form are either left blank or the description given is unclear. This lack of information results in to-and-fro communication that causes delay in further processing and also poses problem
### 8. Desk integration in sandbox

This feature is being enabled in a phased manner. It may not be available in your account. Please follow this post for the latest updates. All customer-facing teams need access to a holistic and up-to-date profile of each customer in order to provide personalized experiences at scale. The sales and customer support teams are no different, and they often have to collaborate over solving tickets and identifying pain points. In the Zoho suite of products, the sales teams primarily use Zoho CRM while the customer support teams work in Zoho Desk. These two tools are often integrated so that both te


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `SANDBOX`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Setting up Zoho Creator Integration`
- `Configuring SAML-based SSO in CRM portals`
- `An overview of user management in Zoho CRM`
- `Troubleshooting Sales Pipelines`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/sandbox` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Sandbox Environments - Example Implementation
// Triggered on record creation/update

if(input.module == "SETTING UP ZOHO CREATOR INTEGRATION")
{
    // Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage
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
- [Workflow-Automation](../Workflow-Automation/README.md)
- [Integrations](../Integrations/README.md)

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

### Setting up Zoho Creator Integration
**Purpose:** Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Z

**Key Points:**
Prerequisite Before activating, please make sure that you meet the required criteria mentioned below: You should have Manage Extensibility and Manage Module Customization permissions enabled in your Zoho CRM account.
You should have a Zoho Creator account with any edition.
If you do not have a Zoho Creator account, please create an account from Zoho Create.
An account with the Free Edition will be automatically created.
After which you can proceed with integrating it with Zoho CRM.
Environment Support : Like CRM Sandbox, Creator now supports Development, Stage, or Production Environments for testing


### Configuring SAML-based SSO in CRM portals
**Purpose:** This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users. For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview .

**Key Points:**
This document will provide instructions on how to enable SAML-based SSO for your CRM's portal users.
For an overview of SAML-based SSO, see SAML based Single Sign On (SSO) in CRM portals - Overview.
Prerequisite Glossary Prerequisite Editions: Enterprise and Ultimate Bundles (CRMPlus and Zoho One) Trial: No Developer: No Sandbox: No Mobile: No Permission : Users with the Manage Portals permission (Under Setup permissions > Admin level permissions ) can configure SAML based SSO for their CRM's portal and manage it.
Glossary Authentication Authentication is the process of confirming a user's identity before providing access to a system.
This is used to secure the system against impostors.
SAML Security Assertion Markup Language (SAML) is a standard for communication that helps in authentication


### An overview of user management in Zoho CRM
**Purpose:** A CRM user is an individual who transforms rich customer data into timely and well-informed actions. CRM users can include members from sales, marketing, customer success, legal, and other teams who r

**Key Points:**
A CRM user is an individual who transforms rich customer data into timely and well-informed actions.
CRM users can include members from sales, marketing, customer success, legal, and other teams who rely on customer or deal context to do their jobs well.
In Zoho CRM, you can purchase user licenses and invite, remove, activate, or deactivate such users per your changing needs.
Types of CRM users There are two kinds of users in Zoho CRM: Regular users are those who are given broad or selective access to CRM data and capabilities.
This access depends on their assigned profiles, which are fully customizable.
The prime example of a regular user is a sales representative who uses the CRM to build relationships and win deals


### Troubleshooting Sales Pipelines
**Purpose:** I created a pipeline and now I cannot update the Stage field in a record. Creating a pipeline does not affect updating stages in the layout. If a map dependency, blueprint, layout rule, or validation

**Key Points:**
I created a pipeline and now I cannot update the Stage field in a record.
Creating a pipeline does not affect updating stages in the layout.
If a map dependency, blueprint, layout rule, or validation rule has been created based on the Stage field, then you won't be able to update the Stage field.
How can I map the pipeline and stage during Hubspot (API) migration.
By default , the stage and pipeline in HubSpot are automatically mapped to the Stage and Pipeline fields in Zoho CRM and you cannot alter this mapping during API migration.
If you need to migrate stages and pipelines in a different format, then you will need to export the data from HubSpot as a spreadsheet and manually importing that data into Zoho CRM, which will allow you to manually map the fields


### Social integration in sandbox
**Purpose:** Social media platforms like Twitter and Facebook have become vital for understanding and engaging customers. Zoho CRM allows you to monitor and engage with these platforms from within your CRM. This i

**Key Points:**
Social media platforms like Twitter and Facebook have become vital for understanding and engaging customers.
Zoho CRM allows you to monitor and engage with these platforms from within your CRM.
This is possible because of the Zoho Social integration (available through the Social tab).
You can test your Zoho Social integration in a sandbox before using it in your production environment.
This allows you to simulate the effects of the integration on your CRM system and on your internal processes.
Once you've tested the integration to a satisfactory level, you can confidently deploy it to the production environment


### FAQs: Zoho CRM Integration with Zoho Projects
**Purpose:** How is the integration between Zoho CRM and Zoho Projects helpful? The integration between Zoho CRM and Zoho Projects works as a bridge between sales data and team collaboration data—all in one place.

**Key Points:**
How is the integration between Zoho CRM and Zoho Projects helpful.
The integration between Zoho CRM and Zoho Projects works as a bridge between sales data and team collaboration data—all in one place.
Since you can associate projects directly with customers, you can plan and manage your tasks more efficiently and make better business decisions, as you can associate projects directly with customers.
Integrating business and sales data with production data improves the quality of work, and thereby the overall revenue and growth of your business, as well as your clients.
Every project involves multiple meetings and discussions between stakeholders through multiple channels.
It's helpful when records can be synced with CRM so that both clients and internal users can access them anytime in one place


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

- [Setting up Zoho Creator Integration](https://help.zoho.com/portal/en/kb/crm/articles/set-up-creator-crm-integration)
- [Configuring SAML-based SSO in CRM portals](https://help.zoho.com/portal/en/kb/crm/articles/configuring-saml-based-sso-in-crm-portals)
- [An overview of user management in Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/an-overview-of-user-management-in-zoho-crm)
- [Troubleshooting Sales Pipelines](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-pipelines)
- [Social integration in sandbox](https://help.zoho.com/portal/en/kb/crm/articles/social-integration-in-sandbox)
- [FAQs: Zoho CRM Integration with Zoho Projects](https://help.zoho.com/portal/en/kb/crm/articles/faqs-zoho-crm-projects)
- [Use Cases for Validation Rules Using Functions](https://help.zoho.com/portal/en/kb/crm/articles/use-cases-validation-rules-functions)
- [Desk integration in sandbox](https://help.zoho.com/portal/en/kb/crm/articles/desk-integration-in-sandbox)
- [Intelligent character recognition by Zia Vision](https://help.zoho.com/portal/en/kb/crm/articles/intelligent-character-recognition-by-zia-vision)
- [Copy Customization](https://help.zoho.com/portal/en/kb/crm/articles/copy-customization-from-crm)
- [FAQs: General questions on customization](https://help.zoho.com/portal/en/kb/crm/articles/general-questions-on-customization)
- [Using Copy Customization](https://help.zoho.com/portal/en/kb/crm/articles/using-copy-customization)
- [Creating Sandbox](https://help.zoho.com/portal/en/kb/crm/articles/creating-sandbox)
- [Survey integration in Sandbox](https://help.zoho.com/portal/en/kb/crm/articles/survey-integration-in-sandbox)
- [Kaizen posts 2024: API series](https://help.zoho.com/portal/en/kb/crm/articles/api-2024)
- [SAML based Single Sign On (SSO) in CRM portals - Overview](https://help.zoho.com/portal/en/kb/crm/articles/saml-based-single-sign-on-sso-in-crm-portals-overview)
- [Switching between organizations in Zoho CRM iOS app ](https://help.zoho.com/portal/en/kb/crm/articles/switching-between-organizations-in-zoho-crm-ios-app)
- [FAQs: Wizards](https://help.zoho.com/portal/en/kb/crm/articles/faqs-wizards)
- [Canvas in sandbox](https://help.zoho.com/portal/en/kb/crm/articles/canvas-in-sandbox)
- [Why your business needs multiple sales processes in your CRM?](https://help.zoho.com/portal/en/kb/crm/articles/why-your-business-needs-multiple-sales-processes-in-your-crm)
- [Storage in Sandbox](https://help.zoho.com/portal/en/kb/crm/articles/storage-in-sandbox)
- [Deploying sandbox changes to production](https://help.zoho.com/portal/en/kb/crm/articles/deploy-sandbox)
- [Webinar integration in Sandbox](https://help.zoho.com/portal/en/kb/crm/articles/webinar-integration-in-sandbox)
- [Sandbox Overview](https://help.zoho.com/portal/en/kb/crm/articles/sandbox-overview)
- [Working with Sales Orders](https://help.zoho.com/portal/en/kb/crm/articles/sales-orders)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*

---
## UI Screenshots & Image Reference
This feature has **3 KB articles** with **23 UI images** available for UI replication.
### Articles with Screenshots
| # | Article | Images | Source |
|---|---------|--------|--------|
| 1 | [Working with Sandbox](https://help.zoho.com/portal/en/kb/crm/working-with-sandbox) | 12 | [View Article](https://help.zoho.com/portal/en/kb/crm/working-with-sandbox) |
| 2 | [Creating Sandbox](https://help.zoho.com/portal/en/kb/crm/creating-sandbox) | 7 | [View Article](https://help.zoho.com/portal/en/kb/crm/creating-sandbox) |
| 3 | [Sandbox Overview](https://help.zoho.com/portal/en/kb/crm/sandbox-overview) | 4 | [View Article](https://help.zoho.com/portal/en/kb/crm/sandbox-overview) |

### Sample Image URLs (from top articles)
**[Working with Sandbox](https://help.zoho.com/portal/en/kb/crm/working-with-sandbox)** — 12 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57e92e44f779040136eb7b1a0519d1d9d3cb7cabf15549a41fd56c4cc6f44bc5ef41ad91820c14f804e5e3c104cb2c664a?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57d81bfc1247c3aaaca36359d1ffea86ce553f60500c58229f937f439a89eaedbdf2ce3091940d16d4257ba5db4015f454?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b572907ca2b6cc6e9fc5718563f100bbe6fd3b215311e95bf017cabcb821f166570b372f24c573b7dfc3ddf3e87389fdf42?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57ad51d86b7a6bba41e4163988e08e19b4bf49020f4aacaa4ecc9ffc2d36e3e581711e1bfff237def61d4aeac2348d6964?inline=true`
[View all 12 images in article →](https://help.zoho.com/portal/en/kb/crm/working-with-sandbox)

**[Creating Sandbox](https://help.zoho.com/portal/en/kb/crm/creating-sandbox)** — 7 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57f576b26b417a146f40fe6695b15f84f21debcd4264327fb225f359f5080057e5be70f6ede8cac9071ec0feb36c22314e?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b574bf4ca50053c8e1b1d12f4b712146877d15b52e48b4be982b5bffdf6b0f2c94fab5ec98c2e03d8d7bbf6ce43d3630a43?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57562adf73a8b28030857c2c64f878f610a9820c294131fe98c4a59f8ae84cfde878723fa6f9e039d754bcee98fa36955c?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579fa4b788ff1030b4b6d4d17228bbe24988f89fc5b46b81be66fc32f45cfb311c918e1845fd350f8212081ed7f70a1827?inline=true`
[View all 7 images in article →](https://help.zoho.com/portal/en/kb/crm/creating-sandbox)

**[Sandbox Overview](https://help.zoho.com/portal/en/kb/crm/sandbox-overview)** — 4 images
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b571076d9aeba564a8f9ecaf57adc5bf152b752c0697d113a7add253256cfd53f82ccd0d869bc6e14e1df02fcc6de9f7c23?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b579fbdfd7e85fe2265e5ef409bfb70c4740f373732ad05ffe31b54dc166f7c44bfdab1bb3bc64cddabfb20a694be0dd1dc?inline=true`
- `https://help.zoho.com/galleryDocuments/edbsnee9ab807a7b25b4e8f807e302b324b57171491171b7e26c212f8aaffa3f9438b3bf4a4604516f7cc7feb492826cebffc2dbd68cd5105bd78c5175e13dba078f5?inline=true`
- `https://desk.zoho.in/galleryDocuments/edbsnc9befd5f9ee9ab27f9668982b795593ccdbed59c566c7530a1583bf0d43fdbf4912b04fb4baf881dbe4df1b6a0286208b1ff288bdcf6a93e3395934e254032fd?inline=true`
[View all 4 images in article →](https://help.zoho.com/portal/en/kb/crm/sandbox-overview)

