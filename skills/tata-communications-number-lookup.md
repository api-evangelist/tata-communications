---
name: Look up a phone number with Tata Communications Number Intelligence
description: >-
  Resolve any E.164 number to its port-corrected serving network, subscriber type and
  MCC/MNC using the Tata Communications Number Intelligence API, then review your own
  lookup history.
api: openapi/tata-communications-number-intelligence-api.json
operations:
  - numberLookupDetails
  - numberLookupRecords
generated: '2026-07-25'
method: generated
source: openapi/tata-communications-number-intelligence-api.json
---

# Look up a phone number with Number Intelligence

Use this when you need to decide how to route traffic to a destination number — whether it
is fixed or mobile, and which operator actually serves it after portability.

## Before you start

- You need an approved application on the Tata Communications developer portal
  (`https://developer.tatacommunications.com/`). There is no anonymous sign-up: an
  administrator approves your application contract against the API, then issues the
  credential. Only 3 of the 49 APIs in that portal are publicly visible; this is one.
- **No base URL is published.** The Swagger 2.0 document declares no `host`, `basePath` or
  `schemes`. The host comes with your portal credential — do not guess one.
- Authentication is a required `Authorization` header, described in the specification as
  "used for authentication in Akana". There is no `securityDefinitions` block, so treat the
  token as opaque. See `authentication/tata-communications-authentication.yml`.

## Step 1 — look up one number (`numberLookupDetails`)

`GET /number/{phnum}`

- `phnum` (path, required) — the subscriber number in E.164 form.
- `Authorization` (header, required).

Read from `result`:

| Field | Meaning |
| --- | --- |
| `npdi` | Number Portability Dip Indicator |
| `spn` | Service Provider Network — the port-corrected operator serving the number |
| `altSpn` | Alternative SPN, when `spn` alone is insufficient |
| `mcc` / `mnc` | ITU-T E.212 country and network codes, present when the number is mobile |
| `name` | Mobile operator name |
| `queryStatus` / `description` | Query status code and its description |

Branch on `mcc`/`mnc` being present to decide fixed versus mobile routing. Use `spn`, not
the number range, once `npdi` shows the number has been ported.

## Step 2 — reconcile your usage (`numberLookupRecords`)

`GET /records`

- `Authorization` (header, required).
- `pageNo`, `pageSize` (query) — offset pagination. Read `totalRecords` to know when to
  stop; there is no documented default or maximum page size.

Each record repeats the lookup fields plus a `timestamp` and the queried `number`, keyed to
`queriedUserid` (your Akana appid).

## Error handling

Both operations document `400`, `401`, `403`, `404` and `500`. Errors are **not** RFC 9457
problem details — expect a vendor JSON body. See
`errors/tata-communications-problem-types.yml`.

## What this API does not do

It is a lookup/portability dip, not a CAMARA Number Verification or SIM Swap API. Tata
Communications publishes no CAMARA endpoints. Do not treat `spn` as a proof of possession
or as an identity signal.

## Rules

- Never invent a base URL, a scope, or an idempotency key — none are published.
- There is no idempotency contract; both operations are reads, so retry is safe on `5xx`.
- No rate-limit headers are documented. Back off on `429`/`5xx` conservatively.
