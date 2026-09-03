---
name: southend-history-archive
description: List and download the historical archive of daily source-linked Southend-on-Sea snapshots as JSON index or CSV.
api: SouthendOnSea.city Southend Now API
operations:
- getSouthendNowHistoryIndex
- downloadSouthendNowHistoryCsv
generated: '2026-09-03'
method: generated
source: openapi/southendonsea-southend-now-api-openapi.yml + https://southendonsea.city/data/reuse
---

# Pull the Southend Now historical archive

1. Call `getSouthendNowHistoryIndex` — `GET https://southendonsea.city/api/southend-now/history`
   — to list archived snapshot dates: `{ name, count, dates[] }` (ISO dates). No auth.
2. For bulk analysis, call `downloadSouthendNowHistoryCsv` —
   `GET https://southendonsea.city/api/southend-now/history.csv` — a UTF-8 `text/csv`
   archive of daily weather, bathing-water, marine and flood snapshots, including Met
   Office warnings, UKHSA weather-health alerts, observed tide, rainfall and
   Shoeburyness particulates alongside modelled air quality.
3. The archive grows one row set per day; cache your download and refresh daily rather
   than re-pulling per request.
4. Rows retain original source attribution and limitations — check the source-specific
   terms at https://southendonsea.city/data/reuse before republishing underlying values.
   API structure and documentation are CC BY 4.0; the data values are not.
