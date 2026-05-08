# Close (close)

Close is an inside-sales CRM with calling, email, SMS, and WhatsApp built in. The Close API exposes leads, contacts, opportunities, tasks, activities (calls, emails, SMS, meetings, notes), pipelines, custom objects, sequences, smart views, scheduling, phone numbers, reporting, and webhooks for sales automation.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/close/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=close-api-evangelist&utm_content=repo)

## Type

- **x-type:** company

## Tags

CRM, Sales Engagement, Inside Sales, Calling, SMS, SaaS

## Timestamps

- **Created:** 2026-05-08
- **Modified:** 2026-05-08

## APIs

| API | Tags |
|---|---|
| Close Leads API | Leads, Companies |
| Close Contacts API | Contacts, People |
| Close Opportunities API | Opportunities, Pipeline |
| Close Tasks API | Tasks, Action Items |
| Close Activities API | Activities, Timeline |
| Close Calls API | Calls, Voice |
| Close Emails API | Emails |
| Close SMS API | SMS, Texting |
| Close Meetings API | Meetings, Calendar |
| Close Pipelines & Statuses API | Pipelines, Statuses |
| Close Custom Fields API | Custom Fields, Metadata |
| Close Custom Objects API | Custom Objects |
| Close Templates API | Templates, Email, SMS |
| Close Sequences API | Sequences, Automation |
| Close Bulk Actions API | Bulk, Background Jobs |
| Close Smart Views API | Smart Views, Saved Searches |
| Close Exports API | Exports, Reporting |
| Close Reporting API | Reporting, Analytics |
| Close Phone Numbers API | Phone Numbers, Telephony |
| Close Scheduling Links API | Scheduling |
| Close Connected Accounts API | Connected Accounts, Integrations |
| Close Users API | Users, Memberships |
| Close Organizations API | Organizations, Workspaces |
| Close Roles & Permissions API | Roles, Permissions |
| Close Groups API | Groups |
| Close Event Log API | Event Log, Audit |
| Close Webhooks API | Webhooks, Events |
| Close OAuth & Apps API | OAuth, Apps |

## Plans

- **Solo:** $9/mo annual ($19 monthly), 1 user / 10K leads
- **Essentials:** $35/seat/mo annual ($49 monthly)
- **Growth:** $99/seat/mo annual ($109 monthly) — Chloe AI, Power Dialer
- **Scale:** $139/seat/mo annual ($149 monthly) — Predictive Dialer, RBAC
- **Add-ons:** Premium phone numbers $19/line, AI Call Assistant $50/mo + $0.02/min, additional org $50/mo

## Rate Limits

- **Per endpoint group, per API key** with separate buckets per (path + method)
- **Org-level limit is 3x** the per-key limit — share load via multiple keys
- `RateLimit` response header (limit / remaining / reset) — preferred over `Retry-After`
- Some endpoints carry tighter unpredictable limits

## Common Properties

- [Website](https://www.close.com/)
- [Documentation](https://developer.close.com/)
- [API Reference](https://developer.close.com/resources/)
- [Pricing](https://www.close.com/pricing)
- [Status](https://status.close.com/)
- [Plans](plans/close-plans-pricing.yml) — API Commons Plans 0.1
- [Rate Limits](rate-limits/close-rate-limits.yml) — API Commons Rate Limits 0.1
- [FinOps](finops/close-finops.yml) — FOCUS-aligned FinOps Framework 1.0

## Artifacts

| Artifact | Path |
|---|---|
| Plans | `plans/close-plans-pricing.yml` |
| Rate Limits | `rate-limits/close-rate-limits.yml` |
| FinOps | `finops/close-finops.yml` |

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
