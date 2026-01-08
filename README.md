# PLG Demo Dataset

This dataset simulates a Product-Led Growth (PLG) B2B SaaS company with 20 users across different plans (Free, Starter, Pro, Enterprise). All data is linked via `user_id` and `user_email`.

## Data Sources

| File | Source | Description |
|------|--------|-------------|
| `users.csv` | Internal | User master data with plan and company info |
| `hubspot_crm.csv` | HubSpot | Sales deals and pipeline |
| `stripe_billing.csv` | Stripe | Raw payment transaction events |
| `intercom_comms.csv` | Intercom | Raw support ticket events |
| `mixpanel_activity.csv` | Mixpanel | Raw product usage events |

---

## Sample Questions

### Conversion & Upgrade Analysis
- "Which free users are ready to upgrade based on usage?"
- "Show me users with high activity but on free plan"
- "Who has the most API calls but isn't paying?"
- "List Pro users who might upgrade to Enterprise"
- "Which users have active upsell deals?"

### Churn & Risk Analysis
- "Which users are at risk of churning?"
- "Show me paying users with failed payments"
- "Who has high API error rates AND open tickets?"
- "List users with angry sentiment and billing issues"
- "Which Pro users have declining usage?"

### Revenue & Billing
- "What's our MRR by plan?"
- "Who has payment failures in the last 30 days?"
- "Show me revenue by account owner"
- "What's our payment success rate?"
- "List all past due accounts"

### Product Usage
- "Who are the power users (most events)?"
- "Which features are most used?"
- "What's the average session duration by plan?"
- "Which users have the highest API error rates?"
- "Show me users who haven't logged in recently"

### Support Analysis
- "Who has the most open tickets?"
- "What's the sentiment distribution across plans?"
- "Which ticket categories are most common?"
- "List users with billing-related tickets"
- "Show me angry users with high deal values"

### Cross-Source Analysis
- "Find high-usage free users with no sales engagement"
- "Which users have billing issues, support tickets, AND high error rates?"
- "Show me Enterprise users with low engagement"
- "List users in negotiation stage with product issues"
- "Which account owners have the most at-risk users?"

---

## Schema Reference

### users.csv
| Column | Type | Description |
|--------|------|-------------|
| user_id | string | Unique user identifier |
| user_email | string | User email |
| company_id | string | Company identifier |
| company_name | string | Company name |
| plan | string | Free/Starter/Pro/Enterprise |
| signup_date | date | User signup date |
| user_role | string | admin/member |

### hubspot_crm.csv
| Column | Type | Description |
|--------|------|-------------|
| deal_id | string | Unique deal identifier |
| user_id | string | User identifier |
| user_email | string | User email |
| deal_stage | string | Lead/Discovery/Proposal/Negotiation/Closed Won |
| deal_value | integer | Deal value ($) |
| account_owner | string | Sales rep name |
| created_at | date | Deal creation date |
| last_activity_at | date | Last activity date |
| is_upsell | boolean | Whether deal is an upsell |

### stripe_billing.csv
| Column | Type | Description |
|--------|------|-------------|
| payment_id | string | Unique payment identifier |
| user_id | string | User identifier |
| user_email | string | User email |
| payment_date | date | Payment date |
| amount | integer | Payment amount ($) |
| status | string | succeeded/failed |
| plan | string | Subscription plan |

### intercom_comms.csv
| Column | Type | Description |
|--------|------|-------------|
| ticket_id | string | Unique ticket identifier |
| user_id | string | User identifier |
| user_email | string | User email |
| created_at | timestamp | Ticket creation time |
| resolved_at | timestamp | Resolution time (null if open) |
| status | string | open/resolved |
| category | string | bug/billing/question/feature_request/account |
| sentiment | string | Angry/Frustrated/Neutral/Happy |
| message | string | Ticket message |

### mixpanel_activity.csv
| Column | Type | Description |
|--------|------|-------------|
| event_id | string | Unique event identifier |
| user_id | string | User identifier |
| user_email | string | User email |
| event_type | string | login/feature_use/api_call |
| event_timestamp | timestamp | Event timestamp |
| feature | string | dashboard/reports/analytics/integrations/api |
| session_duration_sec | integer | Session duration in seconds |
| error_code | string | Error code (400/500/null) |
