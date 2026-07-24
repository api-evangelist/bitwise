---
name: Pull a Bitwise index's value history and constituents
description: >-
  Retrieve a Bitwise crypto index's metadata, historical daily values, and
  current weighted constituents for analysis or reporting.
api: openapi/bitwise-openapi.yml
operations: [listIndexes, getIndexHistory, getIndexConstituents]
---

# Bitwise index analytics

Use the Bitwise market-data API to analyze a crypto index.

## Auth
Send your API key in the `Authorization` header on every request. Keys are
issued on request from `api@bitwiseinvestments.com`. Without a valid key every
path returns `401 unauthorized_request`.

## Steps
1. `listIndexes` — GET `/api/v1/indexes` to discover available indexes and their
   names, inception dates, and constituent assets. Pick an index name (e.g. `DEFI`).
2. `getIndexHistory` — GET `/api/v1/indexes/{indexName}/history` for the daily
   value series. Filter with `startDate`/`endDate`; set `excludeBacktested=true`
   to drop pre-inception backtested values.
3. `getIndexConstituents` — GET `/api/v1/indexes/{indexName}/constituents` for the
   current index value and weighted constituents (price, supply, weight). Pass a
   `timestamp` for point-in-time data, or omit for the latest.

## Errors
Responses use a custom envelope `{ message, id, errors[{ field, message }] }`
(not RFC 9457). On `401` re-check the `Authorization` header. See
`errors/bitwise-problem-types.yml`.
