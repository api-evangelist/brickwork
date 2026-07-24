---
name: Book a store appointment
description: Find a store, look up its bookable services, and create a customer appointment on the Brickwork API v3.
api: openapi/brickwork-openapi.yml
operations: [GetApiV3Stores, GetLocaleApiV3StoresStore_idStore_services, PostLocaleApiV3AdminCustomers, PostApiV3AdminStoresStore_id_or_numberAppointments, GetLocaleApiV3AdminStoresStore_id_or_numberAppointmentsId_or_code]
generated: '2026-07-18'
method: generated
source: openapi/brickwork-openapi.yml
---

# Book a store appointment

Brickwork powers online-to-in-store appointment booking against a retailer's physical stores.

## Auth
Admin operations require the company `api_key` passed as a query parameter (see `authentication/brickwork-authentication.yml`). Front-end store lookups are public.

## Steps
1. **Find the store.** `GetApiV3Stores` (or `GetApiV3StoresStore_search`) to locate the target store; keep its `id` or store `number`.
2. **List bookable services.** `GetLocaleApiV3StoresStore_idStore_services` to get the store's `store_service` offerings and their ids.
3. **Resolve the customer.** Create with `PostLocaleApiV3AdminCustomers`, or reuse an existing customer id/code.
4. **Create the appointment.** `PostApiV3AdminStoresStore_id_or_numberAppointments` with the `store_service_id`, customer, and requested time.
5. **Confirm.** `GetLocaleApiV3AdminStoresStore_id_or_numberAppointmentsId_or_code` to read back the appointment and its `state` (`new`, `customer_requested`, `confirmed`, `canceled`, `checked_in`, `no_show`, `occured`).

## Conventions
- Dates are `YYYY-MM-DD`; use the `utc_offset` query param for timezone (encode `+` as `%2B`).
- No idempotency-key mechanism is documented — avoid blind retries on the create call; verify via the read in step 5 instead.
- Endpoints accept an optional leading `/{locale}/` path segment.
