---
name: Open and advance a Close opportunity through a pipeline
description: >-
  Resolve the right pipeline and opportunity status, open a deal on a Lead, move
  it through stages, and close it won or lost.
api: openapi/_original/close-api-openapi.json
base_url: https://api.close.com/api/v1
operations:
  - pipelines_list
  - opportunity_statuses_list
  - opportunities_create
  - opportunities_list
  - opportunities_get
  - opportunities_update
  - activities.opportunity_status_changes_list
generated: '2026-08-13'
method: generated
source: >-
  Grounded in openapi/_original/close-api-openapi.json (every operationId
  verified present) plus data-model/close-data-model.yml.
---

# Open and advance a Close opportunity

An **Opportunity** is a potential deal on a **Lead**. It sits in one **Opportunity Status**,
and statuses are grouped and ordered into **Pipelines**. Status ids are per-organization —
never hard-code one.

## 1. Resolve the pipeline and its statuses

- `pipelines_list` — `GET /pipeline/`

Pipeline objects embed their opportunity statuses, so one call is usually enough.
If you need statuses on their own: `opportunity_statuses_list` (`GET /status/opportunity/`).

Each status carries a `type` of `active`, `won` or `lost`. That `type` — not the label —
is what tells you whether a deal is open.

## 2. Create the opportunity

- `opportunities_create` — `POST /opportunity/`

Required: `lead_id` and `status_id`. Since 2025-02-14 `lead_id` is optional at the API
level, but an opportunity without a lead is not useful.

**Value is in cents.** `$1,000.00` is `value: 100000`. Getting this wrong by 100x is the
classic error against this endpoint. Also set `value_period` (`one_time` or `monthly`),
`confidence` (0-100), `contact_id` and `user_id` (the owner).

Note that `value_currency` is an organization-wide setting, not a per-opportunity field.

## 3. Advance it

- `opportunities_update` — `PUT /opportunity/{id}/`

Remember every `PUT` behaves as a `PATCH`. To move a stage, send **only** `status_id`.
To close a deal, set `status_id` to a status whose `type` is `won` or `lost`; Close derives
`date_won` and the status roll-up fields itself.

Since 2024-03-27 opportunities also carry pipeline fields, so you can read which pipeline a
deal is in without a second lookup.

## 4. Read the history

Every status move writes an activity:

- `activities.opportunity_status_changes_list` — `GET /activity/status_change/opportunity/`

Filter by `lead_id` or `opportunity_id` to reconstruct how a deal moved. These activities can
also be created directly (`activities.opportunity_status_changes_create`, added 2024-06-20)
when backfilling from another CRM, and deleted (added 2024-06-26) when correcting an import.

## 5. Find deals in flight

- `opportunities_list` — `GET /opportunity/?lead_id=…&status_type=active`

Offset pagination: `_skip` + `_limit`, with `has_more` in the response. Do not page deeply —
Close caps `_skip` per resource. For a full extract, use the Export API
(`exports_create_opportunity`, `POST /export/opportunity/`) and poll `exports_get_opportunity`.

## Rules that will bite you

- Value in **cents**, always.
- No idempotency key: search with `opportunities_list` before creating, or a retry duplicates the deal.
- Up to 300 opportunities per lead.
- On `429`, back off using `rate_reset`; on `402`, a plan limit was reached and retrying will not help.
