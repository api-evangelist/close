---
name: Subscribe to Close webhooks and verify deliveries
description: >-
  Create a filtered webhook subscription, verify the HMAC signature on every
  delivery, and recover missed events from the 30-day event log.
api: openapi/_original/close-api-openapi.json
base_url: https://api.close.com/api/v1
operations:
  - webhooks_create
  - webhooks_list
  - webhooks_get
  - webhooks_update
  - webhooks_delete
  - events_list
  - events_get
generated: '2026-08-13'
method: generated
source: >-
  Grounded in openapi/_original/close-api-openapi.json (every operationId
  verified present) plus asyncapi/close-webhooks.yml.
---

# Subscribe to Close webhooks and verify deliveries

Close webhooks are a change-data feed, not just notifications: each delivery carries
`data`, `previous_data` and `changed_fields`, so a consumer can diff without re-reading.

## 1. Create the subscription

- `webhooks_create` — `POST /webhook/`

Send the destination `url` and an `events[]` array of `{object_type, action}` pairs.
There are 38 object types (`lead`, `contact`, `opportunity`, `activity.call`,
`activity.email`, `task.SUBTYPE`, `custom_object`, …) and 15 actions (`created`,
`updated`, `deleted`, `merged`, `completed`, `sent`, `answered`, `scheduled`,
`canceled`, `started`, `paused`, `activated`, `deactivated`, `reverting`, `reverted`).
The full matrix is in `asyncapi/close-webhooks.yml`.

For finer control, attach a JSON filter expression — see
https://developer.close.com/api/resources/webhooks/webhook-filters.

**Capture `signature_key` from the create response.** It is returned once, at creation, and
you cannot verify deliveries without it.

Leave `verify_ssl` at its default (`true`). Subscriptions can be modified in place since
2025-01-06 via `webhooks_update` (`PUT /webhook/{id}/`).

## 2. Verify every delivery

Each POST carries two headers:

```
close-sig-hash: <hex>
close-sig-timestamp: <unix seconds>
```

The hash is `HMAC-SHA256(key = hex-decoded signature_key, message = close-sig-timestamp + raw_payload)`.
Compare with a constant-time comparison. Reject anything that does not match, and reject a
timestamp far outside your clock skew tolerance.

## 3. Queue first, process later

Close is explicit that **ordering is not guaranteed** — event consolidation, delivery
parallelism and retries all reorder. Write the delivery to your own queue, return 2xx fast,
and process asynchronously. Dedupe on the event `id`; order on `date_created`.

Failure behaviour you must design for:

- Retries back off exponentially up to every 20 minutes, for up to **72 hours**, then drop.
- A subscription is **auto-paused** if the backlog hits 100,000 events (warning emails at
  80,000) or if all delivery fails for 3 straight days.
- A paused subscription stays paused until reactivated through the API — nothing resumes it
  for you.
- Maximum **40 subscriptions per organization** (500 for Zapier, Backendless, Integrately
  and the Customer.io Journeys Track API).

## 4. Recover what you missed

There is no replay endpoint. Backfill from the event log:

- `events_list` — `GET /event/?_cursor=…&_limit=…`
- `events_get` — `GET /event/{id}/`

Retention is **30 days**. Anything older is unrecoverable, which sets the hard ceiling on
how long your consumer can be down.

## 5. Audit and clean up

- `webhooks_list` — `GET /webhook/` (admins see the whole org; non-admins see only their own)
- `webhooks_delete` — `DELETE /webhook/{id}/`

Note that full event data is delivered even for non-admin subscribers.
