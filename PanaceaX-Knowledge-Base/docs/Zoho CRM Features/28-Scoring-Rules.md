# Scoring Rules

> **Feature ID:** `28-Scoring-Rules`  
> **Knowledge Base Articles:** 9  
> **Last Updated:** 2026-05-05

## Overview

Lead and contact scoring based on engagement, attributes, and behavioral signals

---

## 1. Core Functionality

### 1. Segmentation Analysis

Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account. This dashboard presents five charts and are as follows. The Segmentation Analytics category on VoC is designed to offer you insights about the sentiments and keywords from segmented customers based on their labels created using RFM values. Analyzing customer behavior based on their recent purchase (R), frequent purchase (F), and monetary value (M) will help you decide on a better customer retention strategy. The different labels based on your customers' RFM
### 2. Sales process: Lead engagement

Edition : Paid editions | Industry : Applicable for all industries | Features : Integrations with Zoho products and built-in features In the Lead Generation use case, we saw the marketing strategies used by Orange Interiorz to generate leads and capture them in CRM. In the next step, they engage the leads and qualify them for sales. Their lead engagement process is as follows: The sales team gets notifications whenever a lead is added to CRM so they can immediately begin the follow-up process. They prioritize the leads based on their responsiveness to different touch points used for contact an
### 3. Scoring Rules

Prioritise your leads, deals or contacts with Scoring Rules Scoring rules help qualify prospects based on various parameters such as their behavior, insights, attributes, or other key details of their persona. The higher the score, the more likely the prospect is to become a customer. Scoring helps companies improve their marketing outreach by focusing their efforts on the customers who have the highest conversion potential. Users can create scoring rules both manually and through Zia to set automation triggers across all modules. While manual scores allow you to set customized scores for each
### 4. Kaizen posts 2023: API series

Here is a complete list of Kaizen posts related to APIs published in 2023. Sl No Title Description 1 Scoring Rules - Part -1 Learn about scoring rules and how to create, delete, update and execute scoring rule APIs 2 Scoring Rules - Part -2 Learn about active and deactivate scoring roles, cloning scoring rules and getting a record's scoring rule using API 3 Portal APIs - Part I Learn about portals in Zoho CRM, and how to fetch, create and update a portal via APIs, and also how to fetch the portal user types, invite users to a portal, and get users of a particular user type via APIs. 4 Portal A
### 5. FAQs: Segmentation

1. What are the benefits of segmentation? Segmentation allows you to classify your customer base based on how they interact with your company. It gives you a platform to take cues from their buying patterns and categorize them into groups such as not interested, visiting customers, interested buyers, high spenders, and occasional buyers. Once you understand which category your customers belong to, you can personalize marketing strategies and sales experience, resulting in higher customer satisfaction and conversion rates. Read more about the benefits of segmentation, here . 2. Where can I see
### 6. Scoring Rules

What are scoring rules? Scoring rules help qualify prospects based on various parameters such as their behavior, insights, attributes, or other key details of their persona. The higher the score, the more likely the prospect is to become a customer. Scoring helps companies improve their marketing outreach by focusing their efforts on the customers who have the highest conversion potential. Users can create scoring rules both manually and through Zia to set automation triggers across all modules. While manual scores allow you to set customized scores for each channel and its factors, Zia Scores
### 7. How Zoho CRM Administration and Configuration Works for Sales Operations

Zoho CRM gives sales operations teams a full stack of admin tools covering workflow automation, lead routing, UI customisation, permissions, and change management, all accessible without needing a development team. Here is how each layer works, including how AI features fit into the configuration experience. Workflow automation Workflow rules in Zoho CRM are a set of actions such as email notifications, tasks, and field updates that are executed when certain specified conditions are met. These rules automate the process of sending email notifications, assigning tasks, and updating certain fiel
### 8. Zia Scores

Zia Scores - Scope and benefits: Every lead or customer a business encounters is unique, and they all have different thought processes before making a purchase. While there are many ways to understand a customer's point of view, segmentation is a proven method. By segmenting customers in a CRM system based on various factors, such as interactions, support approach, demographics, customer journey, deal history, revenue spent, and conversion period, businesses can better understand which customers require attention, which ones to focus on, and what the next step in the sales cycle should be. Why


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `SCORING`

**Standard Fields (inherited):**
- `Created_By` (User) -- Record creator
- `Modified_By` (User) -- Last modifier
- `Created_Time` (DateTime) -- Creation timestamp
- `Modified_Time` (DateTime) -- Last modification
- `Owner` (User) -- Record owner for access control

**Key Articles:**
- `Segmentation Analysis`
- `Sales process: Lead engagement`
- `Scoring Rules`
- `Kaizen posts 2023: API series`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/scoring` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Scoring Rules - Example Implementation
// Triggered on record creation/update

if(input.module == "SEGMENTATION ANALYSIS")
{
    // Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account. This dashboa
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
- [Contacts-Management](../Contacts-Management/README.md)
- [Assignment-Rules](../Assignment-Rules/README.md)
- [Zia-AI](../Zia-AI/README.md)

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

### Segmentation Analysis
**Purpose:** Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account. This dashboard presents five charts and are as follows. The Se

**Key Points:**
Segmentation Analysis is a set of dashboards that groups VoC insights on the basis of customer segmentation settings in your CRM account.
This dashboard presents five charts and are as follows.
The Segmentation Analytics category on VoC is designed to offer you insights about the sentiments and keywords from segmented customers based on their labels created using RFM values.
Analyzing customer behavior based on their recent purchase (R), frequent purchase (F), and monetary value (M) will help you decide on a better customer retention strategy.
The different labels based on your customers' RFM scores help understand each customer's position in the sales cycle and take appropriate actions.
The 5 charts lay out segmented customers based on scoring labels for these RFM values


### Sales process: Lead engagement
**Purpose:** Edition : Paid editions | Industry : Applicable for all industries | Features : Integrations with Zoho products and built-in features In the Lead Generation use case, we saw the marketing strategies u

**Key Points:**
Edition : Paid editions | Industry : Applicable for all industries | Features : Integrations with Zoho products and built-in features In the Lead Generation use case, we saw the marketing strategies used by Orange Interiorz to generate leads and capture them in CRM.
In the next step, they engage the leads and qualify them for sales.
Their lead engagement process is as follows: The sales team gets notifications whenever a lead is added to CRM so they can immediately begin the follow-up process.
They prioritize the leads based on their responsiveness to different touch points used for contact and follow-up.
This helps them move interested leads down the sales funnel faster.
They contact hot leads via call and email and after they qualify these leads, the sales team passes them over to the design team for the next stage


### Scoring Rules
**Purpose:** Prioritise your leads, deals or contacts with Scoring Rules Scoring rules help qualify prospects based on various parameters such as their behavior, insights, attributes, or other key details of their

**Key Points:**
Prioritise your leads, deals or contacts with Scoring Rules Scoring rules help qualify prospects based on various parameters such as their behavior, insights, attributes, or other key details of their persona.
The higher the score, the more likely the prospect is to become a customer.
Scoring helps companies improve their marketing outreach by focusing their efforts on the customers who have the highest conversion potential.
Users can create scoring rules both manually and through Zia to set automation triggers across all modules.
While manual scores allow you to set customized scores for each channel and its factors, Zia Scores can automatically assign scores based on performance metrics for each of your customers.
Refer here for detailed guidance on Zia Scores


### Kaizen posts 2023: API series
**Purpose:** Here is a complete list of Kaizen posts related to APIs published in 2023. Sl No Title Description 1 Scoring Rules - Part -1 Learn about scoring rules and how to create, delete, update and execute sco

**Key Points:**
Here is a complete list of Kaizen posts related to APIs published in 2023.
Sl No Title Description 1 Scoring Rules - Part -1 Learn about scoring rules and how to create, delete, update and execute scoring rule APIs 2 Scoring Rules - Part -2 Learn about active and deactivate scoring roles, cloning scoring rules and getting a record's scoring rule using API 3 Portal APIs - Part I Learn about portals in Zoho CRM, and how to fetch, create and update a portal via APIs, and also how to fetch the portal user types, invite users to a portal, and get users of a particular user type via APIs.
4 Portal APIs - Part II Explore more of Portal APIs: Manage user types & access; create, update, delete; transfer users; change status; delete users from the portal for efficient user management.
5 User's Unavailability APIs Explore Zoho CRM's User's Unavailability APIs for efficient meeting scheduling.
Learn how to mark, update, and delete unavailability periods, and retrieve user availability details via API requests.
6 Multi-select lookup fields in Zoho CRM API Learn how to add data to multi-select lookup fields in Zoho CRM using the insert records API


### FAQs: Segmentation
**Purpose:** 1. What are the benefits of segmentation? Segmentation allows you to classify your customer base based on how they interact with your company. It gives you a platform to take cues from their buying pa

**Key Points:**
What are the benefits of segmentation.
Segmentation allows you to classify your customer base based on how they interact with your company.
It gives you a platform to take cues from their buying patterns and categorize them into groups such as not interested, visiting customers, interested buyers, high spenders, and occasional buyers.
Once you understand which category your customers belong to, you can personalize marketing strategies and sales experience, resulting in higher customer satisfaction and conversion rates.
Read more about the benefits of segmentation, here.
Where can I see the segmentation history of a record


### Scoring Rules
**Purpose:** What are scoring rules? Scoring rules help qualify prospects based on various parameters such as their behavior, insights, attributes, or other key details of their persona. The higher the score, the

**Key Points:**
Scoring rules help qualify prospects based on various parameters such as their behavior, insights, attributes, or other key details of their persona.
The higher the score, the more likely the prospect is to become a customer.
Scoring helps companies improve their marketing outreach by focusing their efforts on the customers who have the highest conversion potential.
Users can create scoring rules both manually and through Zia to set automation triggers across all modules.
While manual scores allow you to set customized scores for each channel and its factors, Zia Scores can automatically assign scores based on performance metrics for each of your customers.
Refer here for detailed guidance on Zia Scores


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

- [Segmentation Analysis](https://help.zoho.com/portal/en/kb/crm/articles/segmentation-analysis)
- [Sales process: Lead engagement](https://help.zoho.com/portal/en/kb/crm/articles/sales-process-lead-engagement)
- [Scoring Rules](https://help.zoho.com/portal/en/kb/crm/articles/scoring-rules)
- [Kaizen posts 2023: API series](https://help.zoho.com/portal/en/kb/crm/articles/api-2023)
- [FAQs: Segmentation](https://help.zoho.com/portal/en/kb/crm/articles/faqs-segmentation)
- [Scoring Rules](https://help.zoho.com/portal/en/kb/crm/articles/multiple-scoring-rule)
- [How Zoho CRM Administration and Configuration Works for Sales Operations](https://help.zoho.com/portal/en/kb/crm/articles/how-zoho-crm-administration-and-configuration-works-for-sales-operations)
- [Zia Scores](https://help.zoho.com/portal/en/kb/crm/articles/scoring-rules-zia-scores)
- [Zoho CRM's Core Data Model and How You Extend It Safely](https://help.zoho.com/portal/en/kb/crm/articles/zoho-crm-s-core-data-model-and-how-you-extend-it-safely)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
