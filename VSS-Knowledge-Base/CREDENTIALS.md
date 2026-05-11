# VSS — Credentials Reference

> ⚠️ **Never put actual secrets in this file.** Only reference where secrets are stored locally.
> All actual credentials live in `~/.hermes/` on the server — NOT in this repo.

---

## Zoho CRM

**Data Center:** India (`.in`)
**Base URL:** `https://crm.zoho.in/crm/v2`
**Token URL:** `https://accounts.zoho.in/oauth/v2/token`
**Module:** UPS

### OAuth Credentials (Server-based App)
| Field | Value |
|-------|-------|
| Client ID | `1000.GRI56LMPI3FQGQBZYK7UG2C49XUSDB` |
| Client Secret | Stored in `~/.hermes/zoho_credentials.json` |
| Refresh Token | Stored in `~/.hermes/zoho_credentials.json` |
| Access Token | Auto-refreshed by app.js via `getZohoToken()` |
| Stored in | `~/.hermes/zoho_credentials.json` (key: `access_token`, `refresh_token`, `client_id`, `client_secret`) |

### Old OAuth Credentials (Reference only)
| Field | Value |
|-------|-------|
| Client ID | `1000.YY5J9A6X4R8B3K2M7N0P` (old) |
| Stored in | `~/.hermes/zoho_credentials_old.json` |

---

## Firebase

| Field | Value |
|-------|-------|
| Project ID | `upscrm-16643` |
| Collection | `upsdealers` |
| API Key | `AIzaSyDLBkc4fkJP0wU4-DRil1x4zr0nelBZi5E` |
| Auth Domain | `upscrm-16643.firebaseapp.com` |
| Storage Bucket | `upscrm-16643.firebasestorage.app` |
| Measurement ID | `G-35DMX9YQ5L` |
| Stored in | `~/.hermes/firebase_credentials.json` (if separate) |

**Firebase is configured directly in** `index.html` (public, not a secret).

---

## Google (OAuth for Sheets/Drive/Forms)

| Field | Value |
|-------|-------|
| Token stored in | `~/.hermes/google_token.json` |
| Client secret stored in | `~/.hermes/google_client_secret.json` |

**Scope used:** Google Sheets, Google Drive, Google Forms (for photo upload setup)

---

## Sync Scripts

| Item | Location |
|------|----------|
| Zoho → Firebase sync | `/home/azureuser/.hermes/scripts/vss_zoho_firebase_sync.py` |
| Cron job ID | `e7474b1dd47e` |
| Schedule | `0 * * * *` (every hour at minute 0) |
| Last run | Check cron logs or run `cronjob action=list` |

---

## Field App Deployment

| Field | Value |
|-------|-------|
| GitHub Repo | `abhishekmightcode/vss-ups-field-app` |
| GitHub Pages URL | `https://abhishekmightcode.github.io/vss-ups-field-app/` |
| Config | `/tmp/vss-ups-field-app/js/config.js` |
| Main app logic | `/tmp/vss-ups-field-app/js/app.js` |
| Latest commit | `ecb5edf` (fix: use Zoho record ID as Firebase doc ID everywhere) |

---

## Dealer Data Source

| Field | Value |
|-------|-------|
| CSV file | `~/.hermes/cache/documents/doc_64b45d2a1aa4_Untitled spreadsheet - Sheet1 (9).csv` |
| Columns | Dealer code (col 1), Dealer Name (col 2), Phone (col 3) |
| Records | 80 dealers |
| All 10-digit dealer codes | Confirmed in Zoho |

---

## Dealer Code Schema

- **Format:** 10-digit string, e.g. `1000036809`
- **Zoho field:** `Dealer_code` (string, 255 chars)
- **Firebase field:** `dealer_code` (stored inside doc, NOT doc ID)
- **Firebase doc ID:** Zoho record ID, e.g. `1171062000002901006`

---

## Zoho Rate Limiting

- After ~60-80 rapid API calls, Zoho returns HTTP 401 "Access Denied" on token refresh
- **Safe batch size:** ~10 delete operations or 5 insert operations with fresh token per batch
- **Workaround:** For bulk operations, use fresh access token for each small batch

---

*Last updated: 2026-05-09*