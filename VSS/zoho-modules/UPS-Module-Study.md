# UPS Module — VSS Zoho CRM

> Custom module for tracking channel partners / distributors.
> Status: **Active** — 3 records as of May 2026

## Fields

| Field Name | Type | Notes |
|-----------|------|-------|
| Name | Text | Dealer name |
| Phone | Phone | Contact number |
| Email | Email | Contact email |
| Dealer_Type | Picklist? | Type of UPS partner |
| Address_of_the_dealer | Address | Full address with city/state/country/zip |
| Total_Lifetime_Value | Currency | Total business value |
| Last_Order_Date | Date | Last order placed |
| Last_Order_Value | Currency | Value of last order |
| Total_visits | Number | Field visit count |
| Next_Follow_up_date_and_time | DateTime | Scheduled follow-up |
| Owner_email | Email | Owner email |

## Records

| Name | Phone | Lifetime Value | Last Order |
|------|-------|----------------|------------|
| Shivakanth | +916366922515 | — | — |
| abhi | +917483419328 | — | — |
| Eastman distributor | +919844141862 | — | — |

## Observations
- Module is early stage — most fields are empty
- Acts as a **channel partner / distributor registry**
- No orders or visits data captured yet
- No linked Deals or Project_Execution records visible

## API Name
```
UPS
```
