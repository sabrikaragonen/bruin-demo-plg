# PLG (Product-Led Growth) Pipeline

## How to Query Data

**Use Bruin MCP tools to query data.** Do NOT write Python scripts or functions to fetch data. Bruin MCP provides direct database access - use it.

## CRITICAL: Dataset Prefix Required

**Dataset:** `plg`
**Project:** `bruin-demo-data`

**ALWAYS prefix table names with `plg.` in ALL queries.**

```sql
-- CORRECT
SELECT * FROM plg.users;

-- WRONG (will fail)
SELECT * FROM users;
```

## Available Tables

- `plg.users` - User master data
- `plg.mixpanel_activity` - Product usage events from Mixpanel
- `plg.stripe_billing` - Payment transactions from Stripe
- `plg.hubspot_crm` - Sales deals from HubSpot
- `plg.intercom_comms` - Support tickets from Intercom

Table schemas are defined in `assets/*.asset.yml` files.

## Key Relationships

- `user_id` links users to activity, billing, deals, and support tickets
- `company_id` groups users by company
