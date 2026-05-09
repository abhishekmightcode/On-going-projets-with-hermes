# VSS — CRM Data Status

**Last updated:** 2026-05-09

## Current State

### Zoho UPS Module
- **Records:** 80 (corrupted — missing Dealer_Code, phones without +91)
- **Problem:** When seeded from CSV, dealer_code was NOT written to Zoho. All 80 records have `Dealer_Code = null`. Also phones stored as `9008000553` instead of `+919008000553`.

### Firebase ups_dealers Collection
- **Records:** 80, keyed by dealer_code (e.g. `1000036809`)
- **Field `zoho_id`:** Stores Zoho's numeric record ID for API calls
- **Field `phone`:** Empty strings (phone not synced to Firebase in current schema)
- **Status:** Clean — Firebase is correct, Zoho is wrong

## Plan: Wipe and Re-Seed

1. **Wipe Zoho UPS** — delete all 80 records
2. **Re-insert from CSV** — all 80 dealers with:
   - `Name` = dealer name from CSV
   - `Dealer_Code` = CSV column 1 (e.g. `1000036809`)
   - `Phone` = CSV column 3 with `+91` prefix (e.g. `+919008000553`)
3. **Get Zoho IDs** — capture returned record IDs
4. **Sync Firebase** — update `zoho_id` field on all 80 docs

## CSV Schema
- Column 1: `Dealer code` — the business identifier (what goes in Firebase doc ID AND Zoho Dealer_Code)
- Column 2: `Dealer Name` — business name
- Column 3: `Phone` — 10-digit Indian mobile, prepend `+91`

## Important Rules
1. **Zoho is source of truth.** Firebase is read-cache.
2. **Dealer_Code field in Zoho = dealer code from CSV.** This is the primary business identifier.
3. **Phone in Zoho = +91XXXXXXXXXX.** Always.
4. **Firebase doc ID = dealer_code.** `zoho_id` field inside doc = Zoho's numeric record ID.
5. **Never use Zoho's internal ID as Firebase doc ID.** That ID is for API calls only, stored as a field.

## Credentials
- Zoho DC: `.in` (India)
- OAuth Client ID: `1000.GRI56LMPI3FQGQBZYK7UG2C49XUSDB`
- OAuth Refresh Token: stored in `~/.hermes/zoho_credentials.json`
- Firebase Project: `upscrm-16643`
- Firebase Collection: `ups_dealers`
- CSV Source: `~/.hermes/cache/documents/doc_64b45d2a1aa4_Untitled spreadsheet - Sheet1 (9).csv`