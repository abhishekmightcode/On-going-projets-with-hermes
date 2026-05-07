# Project_Execution Module — VSS Zoho CRM

> Custom module for tracking solar installation projects end-to-end.
> Status: **Active** — 13 records as of May 2026

## Fields

### Core Identity
| Field | Type | Notes |
|-------|------|-------|
| Name | Text | Project name (e.g. "MOHAMED ISHACK 10 KW NON DCR ONGRID") |
| Customer_name | Text | Customer full name |
| Phone | Phone | Customer contact |
| Email | Email | Customer email |

### Address
| Field | Type | Notes |
|-------|------|-------|
| Address | Long Text | Full address string |
| Address_Flat_House_No... | Text | House/building |
| Address_Street_Address | Text | Street info |
| Address_City | Picklist | City (Bengaluru, HOSKOTE, TAMIL NADU, etc.) |
| Address_State_Province | Text | State |
| Address_Country_Region | Text | Country |
| Address_Zip_Postal_Code | Text | PIN code |
| Address_Coordinates | Text | Lat/long |

### Project Specs
| Field | Type | Notes |
|-------|------|-------|
| Project_type | Picklist | On grid / Hybrid / Off grid |
| Sanctioned_load | Number | kW load sanctioned |
| Project_lead | Text | Field team lead name |

### Execution Stages
| Field | Type | Notes |
|-------|------|-------|
| Execution_stage | Picklist | Current stage in pipeline |
| On_site_execution_stage | Picklist | On-site progress |
| Date_and_time_of_execution | DateTime | Scheduled execution datetime |
| Day_1 / Day_2 / Day_3 | Date | Execution day 1, 2, 3 |
| Current_on_site_execution | Text | Live execution status |

### Team
| Field | Type | Notes |
|-------|------|-------|
| Project_assistance_team | Multi-line | Day 1 team (name + phone list) |
| Project_assistance_team_Day2 | Multi-line | Day 2 team |
| Project_assistance_team_Day3 | Multi-line | Day 3 team |

### Installation Checklist (Booleans?)
| Field | Notes |
|-------|-------|
| ACDB_DCDB_setup | AC DB / DC DB box setup |
| Structure_setup | MS structure installation |
| Panel_mounting | Solar panel mounting |
| Unloading_on_roof | Material unloading |
| Electrical_wiring | Wiring work |
| Inverter_UPS_Battery_installation | Inverter + battery install |
| Lightning_arrester | LA installation |
| Material_Delivered_on_Location | Delivery confirmed |

### Payments
| Field | Type | Notes |
|-------|------|-------|
| Total_deal_amount | Currency | Full deal value |
| Advance_amount_received | Currency | Advance paid |
| Second_installment_amount | Currency | Second milestone amount |
| Second_installment_received | Picklist | Pending / Received |
| Pending_payment_amount | Currency | Amount still due |
| Full_payment_cleared | Picklist | Yes/No |
| Commissioning | Picklist | Status |

## Records (13 Total)

| Project | Customer | City | Type | Stage | Deal Amount | Advance | 2nd Installment |
|---------|----------|------|------|-------|-------------|---------|----------------|
| MOHAMED ISHACK 10 KW NON DCR ONGRID | MOHAMED ISHACK | Bengaluru | On grid | Procurement done and Team assigned | Rs.634,000 | Rs.50,000 | Rs.520,600 Pending |
| S MANJUNATH X VSS | S MANJUNATH | BANGALORE | Hybrid | Advance received | Rs.750,000 | Rs.50,000 | — |
| MADHU X VSS | MADHU | BANGALORE | On grid | Execution day 1 | Rs.289,239 | Rs.75,000 | — |
| PRAVEEN X VSS | PRAVEEN BHAT | HOSKOTE | On grid | Advance received | Rs.220,000 | Rs.30,000 | — |
| NAGRAJ X VSS | NAGRAJ | BANGALORE | On grid | Advance received | Rs.220,000 | Rs.20,000 | — |
| AJAY X VSS | AJAY SHARMA | KASAVANAHALLI | On grid | Execution day 1 | Rs.550,000 | Rs.5,000 | — |
| GAURAV X VSS | GAURAV SHARMA | TAMIL NADU | Off grid | Advance received | Rs.724,000 | Rs.289,000 | — |
| BASWARAJ X VSS | BASWARAJ | BANGALORE | On grid | Advance received | Rs.376,000 | Rs.100,000 | — |
| SANJAY X VSS | SANJAY THAKUR | BANGALORE | On grid | Execution day 1 | Rs.220,000 | Rs.40,000 | — |
| PARTH X VSS | PARTH | BANGALORE | On grid | Advance received | Rs.558,533 | Rs.100,000 | — |
| LINUS X VSS | LINUS | HAL, BANGALORE | On grid | Advance received | Rs.387,253 | Rs.50,000 | — |
| Nnajay X VSS | Nanjay gowda K | Bengaluru | On grid | Procurement done and Team assigned | — | — | — |
| abhixcx | Abhishek test | Bengaluru | On grid | — | — | — | — |

## Stage Pipeline Summary

```
Leads (incoming) → Advance received → Execution day 1 → Day 2 → Day 3
                                         ↓
                           Procurement done and Team assigned
```

## Financial Summary
- **Total deal value (10 records):** Rs.4.2M+ (approx)
- **Most deals:** 60-90 day payment cycle after installation
- **Second installment:** Always pending (post-installation milestone)

## Observations
1. No link between `Leads` module and `Project_Execution` — they're siloed
2. No `Deals` module being used — deals are tracked as projects
3. Team assignments stored as text strings (not linked to Contacts/Users)
4. Installation checklist fields are present but all empty — execution tracking not yet active
5. Project_lead (Shailesh) appears to be a key field engineer

## API Name
```
Project_Execution
```

## Linked Modules
- Currently **NOT linked** to Leads or Deals
- Future: Link to Deals via custom field, or create a Deal per project
