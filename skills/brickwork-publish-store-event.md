---
name: Publish a store event and take RSVPs
description: Create a store event and register customer RSVPs against it on the Brickwork API v3.
api: openapi/brickwork-openapi.yml
operations: [GetLocaleApiV3AdminStore_events, PostLocaleApiV3AdminStore_events, GetLocaleApiV3AdminStore_eventsId, PutLocaleApiV3AdminStore_eventsId, PostEventsStore_event_idRsvps]
generated: '2026-07-18'
method: generated
source: openapi/brickwork-openapi.yml
---

# Publish a store event and take RSVPs

Brickwork drives in-store traffic through local store events with online RSVP.

## Auth
Company `api_key` as a query parameter for admin operations (see `authentication/brickwork-authentication.yml`). The RSVP creation endpoint is a front-end (customer-facing) operation.

## Steps
1. **List current events.** `GetLocaleApiV3AdminStore_events`.
2. **Create the event.** `PostLocaleApiV3AdminStore_events` with the store, title, and schedule.
3. **Verify / edit.** `GetLocaleApiV3AdminStore_eventsId` then `PutLocaleApiV3AdminStore_eventsId` to adjust details.
4. **Collect RSVPs.** Customers register with `PostEventsStore_event_idRsvps` for the published `store_event_id`.

## Conventions
- Dates `YYYY-MM-DD`; `utc_offset` query param for timezone (encode `+` as `%2B`).
- Optional `/{locale}/` path prefix for localized content.
- No idempotency-key mechanism documented — confirm via the read in step 3.
