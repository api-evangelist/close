# Close (close)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Close is an inside-sales CRM with calling, email, SMS, and WhatsApp built in. The Close API exposes leads, contacts, opportunities, tasks, activities (calls, emails, SMS, meetings, notes), pipelines, custom objects, sequences, smart views, scheduling, phone numbers, reporting, and webhooks for sales automation.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/close/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/close/refs/heads/main/apis.yml)

## Tags

- CRM
- Sales Engagement
- Inside Sales
- Calling
- SMS
- SaaS

## Timestamps

- **Created:** 2026-05-08
- **Modified:** 2026-05-19

## APIs

### Close Leads API

Manage leads — Close's central CRM object representing a company / account. Includes contacts, opportunities, custom fields, addresses, and status.

#### Tags

- Leads
- Companies

#### Properties

- [Documentation](https://developer.close.com/)
- [API Reference](https://developer.close.com/resources/leads/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Contacts API

Manage individual contacts (people) within a lead, including emails, phones, custom fields, and titles.

#### Tags

- Contacts
- People

#### Properties

- [API Reference](https://developer.close.com/resources/contacts/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Opportunities API

Manage opportunities (deals) attached to leads, with pipeline stage, value, status, and custom fields.

#### Tags

- Opportunities
- Pipeline

#### Properties

- [API Reference](https://developer.close.com/resources/opportunities/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Tasks API

Manage tasks assigned to users with due dates, supporting bulk updates and snooze actions.

#### Tags

- Tasks
- Action Items

#### Properties

- [API Reference](https://developer.close.com/resources/tasks/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Activities API

Read and create activities — notes, calls, emails, SMS, WhatsApp, meetings, and custom activity types — that build a lead's timeline.

#### Tags

- Activities
- Timeline

#### Properties

- [API Reference](https://developer.close.com/resources/activities/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Calls API

Log inbound and outbound calls with duration, direction, recording URLs, transcripts, and disposition outcomes.

#### Tags

- Calls
- Voice

#### Properties

- [API Reference](https://developer.close.com/resources/activities/call/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Emails API

Send and log emails with templates, attachments, and tracking against contacts and leads.

#### Tags

- Emails

#### Properties

- [API Reference](https://developer.close.com/resources/activities/email/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close SMS API

Send and log SMS and WhatsApp messages, with conversation threading against contacts.

#### Tags

- SMS
- Texting

#### Properties

- [API Reference](https://developer.close.com/resources/activities/sms/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Meetings API

Log meeting activities synced from connected Zoom / Microsoft / Calendly accounts, with outcomes and notes.

#### Tags

- Meetings
- Calendar

#### Properties

- [API Reference](https://developer.close.com/resources/activities/meeting/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Pipelines & Statuses API

Manage opportunity pipelines and the configurable lead and opportunity statuses driving funnel progression.

#### Tags

- Pipelines
- Statuses

#### Properties

- [API Reference](https://developer.close.com/resources/pipelines/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Custom Fields API

Define and read custom field schemas across leads, contacts, opportunities, activities, and custom objects.

#### Tags

- Custom Fields
- Metadata

#### Properties

- [API Reference](https://developer.close.com/resources/custom-fields/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Custom Objects API

Define user-defined object types with custom fields for tenant- specific data models.

#### Tags

- Custom Objects

#### Properties

- [API Reference](https://developer.close.com/resources/custom-objects/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Templates API

Manage email and SMS templates with variable substitution and rendering for outbound messaging.

#### Tags

- Templates
- Email
- SMS

#### Properties

- [API Reference](https://developer.close.com/resources/templates/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Sequences API

Manage automated multi-step sequences (cadences) and subscriber enrollment with stop conditions.

#### Tags

- Sequences
- Automation

#### Properties

- [API Reference](https://developer.close.com/resources/sequences/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Bulk Actions API

Submit bulk email send / edit / delete / sequence-subscribe jobs that execute as background tasks.

#### Tags

- Bulk
- Background Jobs

#### Properties

- [API Reference](https://developer.close.com/resources/bulk-actions/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Smart Views API

Manage saved search queries (Smart Views) with structured filter grammar across leads, contacts, and opportunities.

#### Tags

- Smart Views
- Saved Searches

#### Properties

- [API Reference](https://developer.close.com/resources/smart-views/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Exports API

Export leads, opportunities, and activities to CSV asynchronously for downstream analytics.

#### Tags

- Exports
- Reporting

#### Properties

- [API Reference](https://developer.close.com/resources/exports/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Reporting API

Generate activity reports, funnel analysis, and status-change tracking across the team.

#### Tags

- Reporting
- Analytics

#### Properties

- [API Reference](https://developer.close.com/resources/reports/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Phone Numbers API

Rent and manage Close-provided phone numbers for inbound and outbound calling and SMS.

#### Tags

- Phone Numbers
- Telephony

#### Properties

- [API Reference](https://developer.close.com/resources/phone-numbers/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Scheduling Links API

Manage user and shared scheduling links that customers use to book meetings into rep calendars.

#### Tags

- Scheduling

#### Properties

- [API Reference](https://developer.close.com/resources/scheduling/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Connected Accounts API

Manage connected email, Zoom, Microsoft, and Calendly accounts backing the Close calling, email, and meeting integrations.

#### Tags

- Connected Accounts
- Integrations

#### Properties

- [API Reference](https://developer.close.com/resources/connected-accounts/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Users API

Manage users (sales reps, managers) and their availability, membership in organizations, and roles.

#### Tags

- Users
- Memberships

#### Properties

- [API Reference](https://developer.close.com/resources/users/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Organizations API

Manage organizations (Close workspaces) including settings, memberships, and inboxes.

#### Tags

- Organizations
- Workspaces

#### Properties

- [API Reference](https://developer.close.com/resources/organization/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Roles & Permissions API

Manage roles and permission sets that govern access to leads, activities, and admin functions (Scale plan only).

#### Tags

- Roles
- Permissions

#### Properties

- [API Reference](https://developer.close.com/resources/roles/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Groups API

Manage user groups for assignment, reporting, and permission scoping.

#### Tags

- Groups

#### Properties

- [API Reference](https://developer.close.com/resources/groups/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Event Log API

Query the 30-day historical event log of all changes across leads, contacts, opportunities, and activities.

#### Tags

- Event Log
- Audit

#### Properties

- [API Reference](https://developer.close.com/resources/event-log/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close Webhooks API

Subscribe to Close events with advanced filtering on event type and object attributes; deliveries include HMAC signatures.

#### Tags

- Webhooks
- Events

#### Properties

- [API Reference](https://developer.close.com/resources/webhooks/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Close OAuth & Apps API

OAuth 2.0 authorization for third-party applications building against Close, plus app registration in the Close Marketplace.

#### Tags

- OAuth
- Apps

#### Properties

- [Documentation](https://developer.close.com/topics/oauth/)
- [OpenAPI](openapi/close-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/close.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/close.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/close-crm)
- [Website](https://www.close.com/)
- [Documentation](https://developer.close.com/)
- [API Reference](https://developer.close.com/resources/)
- [Pricing](https://www.close.com/pricing)
- [Login](https://app.close.com/)
- [Status Page](https://status.close.com/)
- [Blog](https://www.close.com/blog)
- [Support](https://help.close.com/)
- [GitHub Organization](https://github.com/closeio)
- [Privacy Policy](https://www.close.com/privacy)
- [Terms of Service](https://www.close.com/terms)
- [Authentication](https://developer.close.com/topics/authentication/)
- [Rate Limits](https://developer.close.com/api/overview/rate-limits.md)
- [Webhooks](https://developer.close.com/resources/webhooks/)
- [Plans](plans/close-plans-pricing.yml)
- [Rate Limits](rate-limits/close-rate-limits.yml)
- [Fin Ops](finops/close-finops.yml)
- [Features](undefined)
- [Integrations](https://close.com/integrations)
- [L L Ms Txt](https://developer.close.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
