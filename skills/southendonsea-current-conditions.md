---
name: southend-current-conditions
description: Read the current source-linked Southend-on-Sea conditions snapshot (weather, bathing waters, marine, air quality, flood alerts) and use it responsibly.
api: SouthendOnSea.city Southend Now API
operations:
- getSouthendNow
generated: '2026-09-03'
method: generated
source: openapi/southendonsea-southend-now-api-openapi.yml + https://southendonsea.city/data/reuse
---

# Get current Southend-on-Sea conditions

1. Call `getSouthendNow` — `GET https://southendonsea.city/api/southend-now`. No key,
   no auth, CORS is open (`access-control-allow-origin: *`).
2. On a `200`, check `generatedAt` and `refreshIntervalSeconds` (1800). Do not poll
   faster than the refresh interval — responses are edge-cached for 1,800 seconds.
3. Check each section's `available` flag before reading it: `weather`, `air`, `marine`
   and `flood` are ObservationGroups that may be individually unavailable when an
   upstream source is down. `beaches[]` entries carry their own `available` flags.
4. On a `503`, no current snapshot could be assembled — retry after the refresh interval.
5. Before republishing values, honor `licenceNote` and each section's `sourceUrl`:
   the data is source-linked to Met Office, UKHSA, Environment Agency, DEFRA UK-AIR
   and Open-Meteo, and their terms apply to the underlying values.
6. Attribute correctly: SouthendOnSea.city is independent and unofficial — it is not
   Southend-on-Sea City Council, Essex Police or any government body. Never present
   this as an official council or government API.
