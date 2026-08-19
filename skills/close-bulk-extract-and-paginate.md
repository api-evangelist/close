---
name: Page through and bulk-extract Close data without hitting the ceilings
description: >-
  Choose the right pagination style, window on date_created instead of paging
  deeply, and use the Export API for full extracts.
api: openapi/_original/close-api-openapi.json
base_url: https://api.close.com/api/v1
operations:
  - leads_list
  - contacts_list
  - activities_list
  - events_list
  - exports_create_lead
  - exports_get_lead
  - exports_list_lead
  - exports_create_opportunity
  - exports_get
generated: '2026-08-13'
method: generated
source: >-
  Grounded in openapi/_original/close-api-openapi.json (every operationId
  verified present) plus conventions/close-conventions.yml.
---

# Page through and bulk-extract Close data

Close has three read paths with different ceilings. Picking the wrong one is why bulk jobs
against this API stall.

## Path 1 — offset pagination (most list endpoints)

`_skip` + `_limit`, response carries `data` and `has_more`:

```
GET /lead/?_skip=0&_limit=100&_fields=id,display_name,date_created
```

Operations: `leads_list`, `contacts_list`, `activities_list`, and most `*_list` ids.

Two hard limits, both per-resource and both undocumented as numbers:

- Exceeding max `_limit` returns **400** with a message naming the cap.
- Exceeding max `_skip` also fails — so **deep pagination does not work**. Close says so
  itself: paging past a few pages is "inefficient at best or outright impossible at worst".

**Always send `_fields`.** It trims the payload and materially speeds up the call. And never
depend on a field that is not in the reference — Close warns undocumented fields may appear
and may change without notice.

## Path 2 — date windowing (the fix for deep pagination)

Instead of increasing `_skip`, hold `_skip` low and move a `date_created` range forward:

1. Sort/filter on `date_created`.
2. Request a window (say one day) with `_limit=100`, `_skip=0`.
3. Page within the window until `has_more` is false.
4. Advance the window.

This is Close's own recommended pattern and it is the only offset-safe way to walk a large
organization.

## Path 3 — cursor pagination

Two surfaces use cursors instead:

- **Events API** — `events_list` (`GET /event/`), `_cursor` + `_limit` query parameters.
  30-day retention.
- **Advanced Filtering API** — `cursor` + `_limit` in the request body. Note this surface is
  documented but is **not** in Close's OpenAPI, so no operationId exists for it.

Cursors avoid drift when data changes mid-walk. Prefer them where available.

## Path 4 — the Export API (for a real full extract)

For anything approaching "all of it":

- `exports_create_lead` — `POST /export/lead/` with a search query
- `exports_create_opportunity` — `POST /export/opportunity/` with opportunity filters
- `exports_get_lead` / `exports_get` — poll `GET /export/lead/{id}/` until the export is ready
- `exports_list_lead` / `exports_list` — enumerate prior exports

Exports are asynchronous: create, then poll. CSV date formatting changed on 2024-11-06 —
check the changelog entry if you parse dates out of an export.

## Long filters

If your filter is a long list of ids, the URL will exceed the ~2000-character limit. Send it
in the body instead:

```
curl -X POST -u apikey: \
  -H 'content-type: application/json' \
  -H 'x-http-method-override: GET' \
  -d '{"_params": {"lead_id": "lead_..."}}' \
  https://api.close.com/api/v1/activity/
```

## Rate limits during a bulk walk

Limits are per **endpoint group** (path + method), enforced per API key and per organization,
where the org limit is 3x the key limit. That means up to three keys can run in parallel
before the org ceiling binds; a fourth adds nothing.

Read `RateLimit: limit=…, remaining=…, reset=…` on every response and throttle proactively.
On `429`, sleep `rate_reset` seconds — Close recommends it over `Retry-After` — then resume
against that same endpoint group only. Some endpoints carry stricter unpredictable limits
where only `rate_reset` and `retry-after` are set, so never assume `remaining` is the whole story.
