---
name: Manage a store profile and hours
description: Create or update a store and set its regular operating hours on the Brickwork API v3.
api: openapi/brickwork-openapi.yml
operations: [GetApiV3AdminStores, PostApiV3AdminStores, GetApiV3AdminStoresId_or_number, PutApiV3AdminStoresId_or_number, GetApiV3AdminStoresStore_id_or_numberRegular_hours, PostApiV3AdminStoresStore_id_or_numberRegular_hours, PutApiV3AdminStoresStore_id_or_numberRegular_hoursId]
generated: '2026-07-18'
method: generated
source: openapi/brickwork-openapi.yml
---

# Manage a store profile and hours

Keep a retailer's physical store records and operating hours current so store-locator and local pages stay accurate.

## Auth
Company `api_key` as a query parameter (see `authentication/brickwork-authentication.yml`).

## Steps
1. **List existing stores.** `GetApiV3AdminStores`.
2. **Create or update the store.** `PostApiV3AdminStores` for a new store, or `PutApiV3AdminStoresId_or_number` to update an existing one (address, contact, type).
3. **Read back.** `GetApiV3AdminStoresId_or_number` to confirm the persisted record.
4. **Set regular hours.** `GetApiV3AdminStoresStore_id_or_numberRegular_hours` to inspect, then `PostApiV3AdminStoresStore_id_or_numberRegular_hours` / `PutApiV3AdminStoresStore_id_or_numberRegular_hoursId` to set the weekly schedule.

## Conventions
- Stores are addressable by `id`, `code`, or store `number`.
- No idempotency-key header is documented — read back after writes to confirm.
- See `data-model/brickwork-data-model.yml` for how stores relate to services, events, and hours.
