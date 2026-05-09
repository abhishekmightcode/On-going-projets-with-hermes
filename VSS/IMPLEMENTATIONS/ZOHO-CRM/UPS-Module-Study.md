# UPS Module — VSS

## Schema
Custom module in VSS Zoho CRM. Fields:
- Name (text)
- Phone (phone)
- Email (email)
- Dealer_Type (picklist)
- Address fields (street, city, state, zip, coordinates)
- Total_Lifetime_Value (currency)
- Last_Order_Date (date)
- Last_Order_Value (currency)
- Total_visits (number)
- Next_Follow_up_date_and_time (datetime)
- Dealer_Code (text) — dealer ID from Excel
- Owner_email (email)

## Subforms
- Dealer_meets (subform) — meeting/visit records per dealer

## Records
- 60+ dealer records imported from `DEALER CONTACT_NO.xlsx`
- Each record: Dealer_Code + Name + Phone (+91 format)
