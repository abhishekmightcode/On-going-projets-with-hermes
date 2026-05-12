---
name: vss-zoho-ups-cadence
description: Daily cadence for VSS field team — fetch Fresh UPS leads, schedule visit reminders, update CRM fields on Zoho
trigger_keywords:
  - fresh leads
  - check my leads
  - show my leads
  - what are my leads today
  - update CRM
  - update my CRM
  - my visits today
schedule: "0 10 * * *"  # 10 AM daily
---

# VSS Zoho UPS Daily Cadence

## Trigger Conditions
- **Morning cron** → runs at 10 AM daily, checks for Fresh leads
- **Manual trigger** → user says: "fresh leads", "check my leads", "show my leads", "what are my leads today"
- **Manual trigger** → user says: "update CRM", "update my CRM"

## Phase 1 — Morning Lead Fetch

When triggered, fetch all `Stage = Fresh` records from Zoho UPS module.

**API Call:**
```
GET https://crm.zoho.in/crm/v2/UPS?per_page=200
Filter: Stage EQ Fresh
```

**Display as lead cards:**
```
[N] Name
   📞 Phone | 🏷️ Dealer Code: XXXXX | 📍 Address
   📅 Created: DD/MM/YYYY | 🕐 Last Activity: DD/MM/YYYY HH:MM
   Stage: Fresh
```

## Phase 2 — User Selects Leads (max 3)

Ask user: *"Which leads are you visiting today?"*
Show numbered list. User picks 1-3.

**Example:**
```
Today's visits:
1. SAI POWER SOLUTIONS — 3:00 PM
2. DELHI ENTERPRISES — 4:30 PM
3. MUMBAI TRONICS — 6:00 PM
```

## Phase 3 — Schedule Visit Reminders

For each selected lead, ask: *"What time are you visiting [Name]?"*
User replies with time (e.g. "3 PM", "15:00", "around 4").

**Scheduling logic:**
- Visit time + 1 hour = reminder time
- Schedule a cron job (one-shot) to fire at that time
- Reminder message: *"Did you complete your visit to [Name]? Want me to update CRM?"*

## Phase 4 — CRM Update Flow

**Trigger:** User says "yes", "update CRM", "do it", or scheduled reminder fires.

**Step 1 — Choose Lead:**
Show leads being visited today:
```
Which lead are you updating?
1. SAI POWER SOLUTIONS
2. DELHI ENTERPRISES
3. MUMBAI TRONICS
```

**Step 2 — Collect Visit Data:**
For the selected lead, ask these fields ONE BY ONE (in order):

```
1. Dealer Type: ___________
2. Last Order Date (DD/MM/YYYY): ___________
3. Existing Battery Stock: ___________
4. Last Order Value (₹): ___________
5. Existing UPS Stock: ___________
6. Total Lifetime Value (₹): ___________
7. Existing High KV UPS Stock: ___________
8. Follow up Date (DD/MM/YYYY): ___________
9. Follow up Time: ___________
10. Follow up Notes: ___________
11. Credit Value with Dealer (₹): ___________
12. Approx Value in Outlet (₹): ___________
```

**Step 3 — Confirm & Push to Zoho:**
Show summary, ask: *"Push this to CRM for [Name]?"*
On confirmation → PATCH record to Zoho.

**Zoho CRM Update Fields (API names confirmed from UPS module):**

| # | Display Name | API Name | Type |
|---|---------------|----------|------|
| 1 | Dealer Type | `Dealer_Type` | text |
| 2 | Last Order Date | `Last_Order_Date` | date |
| 3 | Existing Battery Stock | `Existing_Battery_stock` | text |
| 4 | Last Order Value | `Last_Order_Value` | currency |
| 5 | Existing UPS Stock | `Existing_UPS_stock` | text |
| 6 | Total Lifetime Value | `Total_Lifetime_Value` | currency |
| 7 | Existing High KV UPS Stock | `Existing_High_KV_UPS_stock` | text |
| 8 | Follow up Date and Time | `Follow_up_date_and_time` | datetime |
| 9 | Follow up Notes | `Follow_up_notes` | text |
| 10 | Credit Value with Dealer | `Credit_value_with_dealer` | currency |
| 11 | Approx Value in Outlet | `Approx_value_in_outlet` | currency |

**Zoho PATCH call:**
```
PATCH https://crm.zoho.in/crm/v2/UPS/{record_id}
Headers: Authorization: Zoho-oauthtoken {token}
Body:
{
  "Dealer_Type": "...",
  "Last_Order_Date": "YYYY-MM-DD",
  "Existing_Battery_stock": "...",
  "Last_Order_Value": 12345,
  "Existing_UPS_stock": "...",
  "Total_Lifetime_Value": 67890,
  "Existing_High_KV_UPS_stock": "...",
  "Follow_up_date_and_time": "YYYY-MM-DDTHH:MM:SS+05:30",
  "Follow_up_notes": "...",
  "Credit_value_with_dealer": 5000,
  "Approx_value_in_outlet": 15000
}
```

**Stage Transition (confirmed 4 stages in Zoho UPS):**
`Fresh` → `Visit Done` → `Revisit Needed` / `Not Contacted`

After successful CRM push → PATCH `Stage = "Visit Done"`

## Skill Notes

- Auth: Use Zoho OAuth token (refresh token flow)
- Record ID comes from the lead card's `id` field
- All ₹ values: store as integer (no currency symbol)
- Dates: Zoho accepts `YYYY-MM-DD` format internally
- Follow up datetime: combine date + time fields into ISO string
- Max 3 leads per day cadence
- If user says "skip" to a field → leave blank, don't push empty strings