---
name: Create a Close lead and log the first touch
description: >-
  Create a company (Lead) in Close, attach the person you spoke to as a Contact,
  and log the first call, email or note on the timeline — without creating
  duplicates.
api: openapi/_original/close-api-openapi.json
base_url: https://api.close.com/api/v1
operations:
  - leads_list
  - leads_create
  - contacts_create
  - activities.notes_create
  - activities.calls_create
  - activities.emails_create
generated: '2026-08-13'
method: generated
source: >-
  Grounded in openapi/_original/close-api-openapi.json (every operationId
  verified present) plus conventions/close-conventions.yml and
  errors/close-problem-types.yml.
---

# Create a Close lead and log the first touch

In Close, a **Lead is a company**, not a person. People are **Contacts** attached to a Lead.
Getting this backwards is the single most common modelling mistake against this API.

## Authenticate

HTTP Basic, API key as the username, **empty password** — the trailing colon matters:

```
curl https://api.close.com/api/v1/me/ -u YOUR_API_KEY:
```

Or `Authorization: Bearer <token>` for OAuth. See `authentication/close-authentication.yml`.

## 1. Check for an existing lead first — the API is not idempotent

Close documents **no idempotency key**. A retried `POST /lead/` creates a second company.
Always search before you create.

- `leads_list` — `GET /lead/?query=<name>&_fields=id,display_name`

If a match comes back, skip to step 3 and use its `id`.

## 2. Create the lead

- `leads_create` — `POST /lead/`

Send `name`, and optionally `url`, `description`, `addresses[]`, `status_id` and a `custom` map.
Look up valid statuses with `lead_statuses_list` (`GET /status/lead/`) — the ids are org-specific
and start with `stat_`. The response `id` starts with `lead_`.

## 3. Attach the person as a contact

- `contacts_create` — `POST /contact/`

Send `lead_id` plus `name`, `title`, `emails[]`, `phones[]`, `urls[]`. Since 2025-02-14
`lead_id` is optional, but supplying it is what binds the person to the company.
The response `id` starts with `cont_`.

## 4. Log the first touch on the timeline

Pick the activity type that actually happened. All of them take `lead_id`, and most take
`contact_id`:

- Note — `activities.notes_create` (`POST /activity/note/`). Send `note` (plaintext) or
  `note_html` (rich text). At least one is required.
- Logged call — `activities.calls_create` (`POST /activity/call/`). This *logs an external
  call*; it does not place one.
- Email — `activities.emails_create` (`POST /activity/email/`). Set `status: "draft"` to
  leave it for a human to review and send, or `"outbox"` to queue it for sending. As of
  2025-12-17 the sender field has stricter requirements — read the changelog entry before
  sending programmatically.

## Rules that will bite you

- **Every `PUT` is a `PATCH`.** Send only changed fields; omitted fields are left alone.
- **Rate limits are per endpoint group**, per API key and per organization (org = 3x key).
  On `429`, sleep for `rate_reset` — Close's own guidance prefers it over `Retry-After` —
  then retry the same group. Read the `RateLimit` header (`limit`, `remaining`, `reset`) on
  every response.
- **`402` means a plan limit was hit**, not a transient failure. Do not retry it. Solo is
  capped at 10,000 leads; custom fields are capped at 250 on every tier.
- **No 5xx contract exists.** Close declares no server-error responses in its spec, so
  treat 5xx as unknown-outcome: re-query before re-posting, or you will duplicate.
- Use `_fields` to trim responses — Close warns that undocumented fields may appear and may
  change without notice, so never depend on a field that is not in the reference.

## Verify

- `leads_get` — `GET /lead/{id}/` and confirm the contact id is in `contact_ids` and the
  activity appears on the timeline via `activities_list` (`GET /activity/?lead_id=<id>`).
