---
name: Look up Bitwise fund and ETF data
description: >-
  Retrieve per-fund market data (NAV, AUM, holdings, crypto-per-share) and ETF
  listings and details from the Bitwise market-data API.
api: openapi/bitwise-openapi.yml
operations: [getFundData, listEtfs, getEtf]
---

# Bitwise fund and ETF data

## Auth
Send your API key in the `Authorization` header on every request (request a key
from `api@bitwiseinvestments.com`).

## Steps
1. `getFundData` — GET `/api/v1/fundData/{fundName}` (e.g. `defiFund`) for market
   price, intra-day and previous-day NAV, AUM, price change, performance, shares
   outstanding, holdings, and crypto-per-share.
2. `listEtfs` — GET `/api/v1/etfs` to enumerate all supported Bitwise ETFs.
3. `getEtf` — GET `/api/v1/etf/{etfName}` (e.g. `BITB`) for a single ETF's
   pricing, holdings, and metadata. Pass `date` (YYYY-MM-DD) for an as-of value;
   omit to default to today.

## Errors
Custom envelope `{ message, id, errors[] }`; `401` means a missing or invalid
API key. See `errors/bitwise-problem-types.yml` and
`conventions/bitwise-conventions.yml`.
