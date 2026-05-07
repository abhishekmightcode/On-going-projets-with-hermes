# VSS — V Sustain Solar Solutions

> Abhishek's client/partner. Solar business automation project. Zoho CRM is LIVE and connected.

## Overview
- **Project Type:** Zoho CRM Implementation + Business Automation
- **Client:** V Sustain Solar Solutions
- **Industry:** Solar Energy
- **CRM URL:** https://crm.zoho.in
- **Stage:** Active — CRM connected, data flowing
- **Owner:** Abhishek Sharma

## Zoho CRM Integration

**Status:** ✅ Connected and tested  
**DC:** `.in` (India)  
**API Base:** `https://www.zohoapis.in/crm/v2`  
**Token Endpoint:** `https://accounts.zoho.in/oauth/v2/token`

### Auth Flow
```
1. POST to accounts.zoho.in/oauth/v2/token
   grant_type=refresh_token
   client_id=<stored in Hermes memory>
   client_secret=<stored in Hermes memory>
   refresh_token=<stored in Hermes memory>

2. Use returned access_token in Authorization header:
   Authorization: Zoho-oauthtoken <access_token>

3. Call CRM API:
   https://www.zohoapis.in/crm/v2/{module}
```

### Current CRM Data (as of May 2026)
- **Leads:** 2+ records
- **Source:** WhatsApp Cloud API integration active
- **Tags in use:** CTWA, SET1
- **Owner:** V sustain Solar Solutions (vsustainsolarenergy@gmail.com)

## What's Here
This folder tracks all plans, research, and implementations for VSS.

### Plans
- Business strategy documents
- Zoho CRM configuration plans
- Sales process workflows

### Research
- Competitor analysis
- Market positioning
- Pricing benchmarks

### Implementations
- Zoho CRM setup logs
- Workflow automation configs
- Custom field mappings

## Goals
- Full Zoho CRM deployment for solar sales team
- Automated lead-to-deal pipeline
- Commission tracking system
- Installation project management module

## ⚠️ Data Separation
- Keep VSS data SEPARATE from Abhishek's personal projects
- Credentials stored in Hermes memory only
- Future cleanup: revoke token → clear credentials → disconnect app

---

*Last updated: May 7, 2026*
