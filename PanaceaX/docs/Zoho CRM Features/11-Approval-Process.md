# Approval Processes

> **Feature ID:** `11-Approval-Process`  
> **Knowledge Base Articles:** 58  
> **Last Updated:** 2026-05-05

## Overview

Multi-level approvals, approval workflows, record locking, and escalation rules

---

## 1. Core Functionality

### 1. Managing Process

Understanding Approval Process Sometimes, for a process to take place, you need approval from people at higher levels in an organization. This type of formal approval requires input from multiple roles. The approval processes created in the web version of Zoho CRM will also appear in the mobile version. Permission Required Users with Manage workflow permission in their profile can access this feature. Check Feature Availability and Limits Records that are waiting for approval can be viewed in the Android app and can then be approved, rejected, or delegated from the My Jobs module or from the record detail view of a specific module. To approve a record Tap the icon in your Zoho CRM app. Tap My Jobs . Tap on the required record in the list. Tap the record to view its details. Tap Approve . T
### 2. Field of Lookup

Overview Lookup fields enable users to associate records between two modules. Let's say, for example, you have two modules: Students and Courses. By adding a lookup field called Course type in the Students module, users can select a course when a new student record is created or added in Zoho CRM, as well as view the list of students enrolled in a particular course in the Courses module's related list. While the Course type lookup field displays the names of the courses in which a student has expressed interest, in instances when you want to view more details—such as course fee, course duration, subjects, course instructor, and so on—you can use the field of lookup module option. Business scenarios View additional details of a contact in the Deals module Sales associates can view a contact
### 3. Cisco Telephony Integration

Calls are the primary method of communication for executives with prospects and clients. Your team can make and take calls directly from their sales software by integrating Cisco Unified Communication Manager with Zoho CRM, and you can track the outcomes of each call against transactions. Additionally, each record will include a call history so you can keep track of past discussions. For now, we have introduced Cisco Unified Communication Manager as a beta version, this can be installed only on request. Later this can be directly downloaded. Request Access To request access for Cisco Unified Communication Manager , go to Setup > Channels > Telephony > Cisco > Request Access Once you request for access, a trigger is generated for the support team. Then the support team from Zoho provides th
### 4. Acting on VoC insights

In today's technologically-rich business market, companies are in close quarters with customers and their opinions. Through various channels, customers are expressing their contentment and discontentment; gratitude and grievances about your business. This is an opportunity to understand your customers truly and grow at scale. But, businesses just do not succeed by mere understanding their customers. Of course, understanding helps at a greater level. But, success lies in action. Your customers leave different kinds of feedback with distinct purposes like a complaint to report a fault, a suggestion to improve the deliverables, a query about the recent purchase, a comparison of brand offering, an escalation on lapsed SLA, disappointment on the recent engagement, or even appreciation on latest
### 5. View Approval History

Approval History gives you a list of records that were submitted for approval. To view the Approval History In your Zoho CRM account, click the My Jobs tab. Click the Approval Process tab. In the Awaiting your Approval page, click Approval History. The Approval History page displays all the approval-related records in a chronological order. Since the Approval History could get exhaustive over a period of time, it could be quite tiresome to sift through the entries if you are looking for a few specific details. For example, if you wish to see only the records submitted for approval by a particular user or a list of records submitted for approval in the last 7 days, it could be difficult to find those specific entries among a huge list. In such a case, you can use the Filter options offered 
### 6. Automation in Team Module

This document will cover the automation-related information for team modules. CRM for everyone opens up module creation to non-admins as mentioned here . This brings the work of customer facing teams into the CRM and gives it context. But teams will soon want to automate repetitive work to make their processes faster and to focus on more important tasks. Teams do not have to rely on org admins for automating their team's work or managing their team's processes. With CRM for everyone, team module admins can do this on their own. This lets teams configure and own their processes fully, while reducing the load on the org admins. They can do this by using the following features: Assignment rules Workflow rules Blueprint Approval process Assignment rules Assignment rules can be configured to au
### 7. Approving or Rejecting from the Approval Tab

Records that are lined for approval can be viewed in the My Jobs tab. From this tab, you can approve or reject the records that are waiting for your approval. If needed, you can also delegate the record's approval to another user. Only after the approval, you can convert, edit or delete the record. Users with Administrator profile can view all the records that are waiting for approval in the organization. Administrator can also approve or reject the records as and when required. To approve/reject from the Approvals tab Navigate to My Jobs and click the Approvals tab. You will be able to see the list of records that are waiting for your approval. Click on a record to view the following details: Details of the record - You can view the details of the user who owns the record that is waiting 
### 8. Set up your Organization Account

As an administrator your first step towards implementing Zoho CRM for your organization will involve entering details in the personal settings and defining the organization details, which will be visible to all users across the departments. You will also need to define the email settings in your CRM account and configure Motivator to keep your team members motivated by giving timely rewards and perks. Personal Settings First, personalize your CRM account by changing language and time zone. Then, you can set other personal preferences like date format, time format, number format, and so on. You can also set up accessibility controls to make the CRM experience work for you. Organization Settings Company details: Add your company details such as the company name for all your business communic


---

## 2. Technical & Architectural Approach

### Data Model

**Primary Module:** `APPROVAL`

**Standard Fields (inherited):**
- `Created_By` (User) — Record creator
- `Modified_By` (User) — Last modifier
- `Created_Time` (DateTime) — Creation timestamp
- `Modified_Time` (DateTime) — Last modification
- `Owner` (User) — Record owner for access control

**Key Articles:**
- `Managing Process`
- `Field of Lookup`
- `Cisco Telephony Integration`
- `Acting on VoC insights`

### API Reference

| Operation | Endpoint | Method |
|-----------|----------|--------|
| List Records | `/crm/v8/approval` | GET |
| Get Record | `/crm/v8/{module}/{recordId}` | GET |
| Create Record | `/crm/v8/{module}` | POST |
| Update Record | `/crm/v8/{module}/{recordId}` | PUT |
| Delete Record | `/crm/v8/{module}/{recordId}` | DELETE |
| Bulk Create | `/crm/v8/batch` | POST |

### Zoho Deluge Scripting

```deluge
// // Approval Processes - Example Implementation
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

- [Workflow-Automation](../Workflow-Automation/README.md)
- [Blueprint-Process-Management](../Blueprint-Process-Management/README.md)
- [Record-Locking](../Record-Locking/README.md)

### This Feature Enables

- **Workflow-Automation** — shares data model and workflows
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


### Cisco Telephony Integration
**Purpose:** Calls are the primary method of communication for executives with prospects and clients. Your team can make and take calls directly from their sales software by integrating Cisco Unified Communication

**Key Points:**
- Calls are the primary method of communication for executives with prospects and clients.
- Your team can make and take calls directly from their sales software by integrating Cisco Unified Communication Manager with Zoho CRM, and you can track the outcomes of each call against transactions.
- Additionally, each record will include a call history so you can keep track of past discussions.
- For now, we have introduced Cisco Unified Communication Manager as a beta version, this can be installed only on


### Acting on VoC insights
**Purpose:** In today's technologically-rich business market, companies are in close quarters with customers and their opinions. Through various channels, customers are expressing their contentment and discontentm

**Key Points:**
- In today's technologically-rich business market, companies are in close quarters with customers and their opinions.
- Through various channels, customers are expressing their contentment and discontentment; gratitude and grievances about your business.
- This is an opportunity to understand your customers truly and grow at scale.
- But, businesses just do not succeed by mere understanding their customers.
- Of course, understanding helps at a greater level.
- But, success lies in action


### View Approval History
**Purpose:** Approval History gives you a list of records that were submitted for approval. To view the Approval History In your Zoho CRM account, click the My Jobs tab. Click the Approval Process tab. In the Awai

**Key Points:**
- Approval History gives you a list of records that were submitted for approval.
- To view the Approval History In your Zoho CRM account, click the My Jobs tab.
- Click the Approval Process tab.
- In the Awaiting your Approval page, click Approval History.
- The Approval History page displays all the approval-related records in a chronological order.
- Since the Approval History could get exhaustive over a period of time, it could be quite tiresome to sift through the entries if you are looking for a few sp


### Automation in Team Module
**Purpose:** This document will cover the automation-related information for team modules. CRM for everyone opens up module creation to non-admins as mentioned here . This brings the work of customer facing teams 

**Key Points:**
- This document will cover the automation-related information for team modules.
- CRM for everyone opens up module creation to non-admins as mentioned here.
- This brings the work of customer facing teams into the CRM and gives it context.
- But teams will soon want to automate repetitive work to make their processes faster and to focus on more important tasks.
- Teams do not have to rely on org admins for automating their team's work or managing their team's processes.
- With CRM for everyone, team module


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
- [Cisco Telephony Integration](https://help.zoho.com/portal/en/kb/crm/articles/cisco-telephony-integration-beta-release)
- [Acting on VoC insights](https://help.zoho.com/portal/en/kb/crm/articles/acting-on-voc-insights)
- [View Approval History](https://help.zoho.com/portal/en/kb/crm/articles/view-approval-history)
- [Automation in Team Module](https://help.zoho.com/portal/en/kb/crm/articles/automation-in-team-modules)
- [Approving or Rejecting from the Approval Tab](https://help.zoho.com/portal/en/kb/crm/articles/approval-tab)
- [Set up your Organization Account](https://help.zoho.com/portal/en/kb/crm/articles/get-started-setup-organization-account)
- [Awaiting Records](https://help.zoho.com/portal/en/kb/crm/articles/approve-records)
- [Initiate an approval request when the loan applicant has a low credit score](https://help.zoho.com/portal/en/kb/crm/articles/approval-process-scenario)
- [Troubleshooting Blueprint](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-blueprint)
- [Reorder Approval Processes and Process Rules](https://help.zoho.com/portal/en/kb/crm/articles/reorder-approval-processes)
- [FAQ: Approval Process](https://help.zoho.com/portal/en/kb/crm/articles/faq-approval-process)
- [Adding an Approval Process](https://help.zoho.com/portal/en/kb/crm/articles/add-approval-process)
- [Troubleshooting Zoho Campaigns integration with Zoho CRM](https://help.zoho.com/portal/en/kb/crm/articles/troubleshooting-campaigns-integration-for-zoho-crm)
- [Collaborating using Feeds](https://help.zoho.com/portal/en/kb/crm/articles/collaborating-using-feeds-in-zoho-crm-android-app)
- [Grid View](https://help.zoho.com/portal/en/kb/crm/articles/grid-view-for-crm)
- [Installing Zoho CRM in MS Office 365](https://help.zoho.com/portal/en/kb/crm/articles/office-365-crm-integration)
- [Platform widgets in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/articles/platform-widgets-in-zoho-crm-ios-app-29-1-2026)
- [Working on records in approval process](https://help.zoho.com/portal/en/kb/crm/articles/working-on-records-in-approval-process)
- [Collaborate using feeds in Zoho CRM iOS app](https://help.zoho.com/portal/en/kb/crm/articles/collaborate-using-feeds-in-zoho-crm-ios-app)
- [Adobe Sign](https://help.zoho.com/portal/en/kb/crm/articles/adobe-sign-crm-integration)
- [Zia Vision — Intelligent Image Validation](https://help.zoho.com/portal/en/kb/crm/articles/zia-vision)
- [Kaizen posts 2026: Functions series](https://help.zoho.com/portal/en/kb/crm/articles/functions-2026)
- [Extensions for Zoho CRM - Zoho Marketplace](https://help.zoho.com/portal/en/kb/crm/articles/extensions-for-zoho-crm-overview)

---

*Generated for PanaceaX AI-native CRM -- Zoho CRM Feature Analysis*
*Source: Zoho CRM Knowledge Base -- May 2026*
