---
name: Register a sender ID and check destinations on the Mobile Messaging Exchange
description: >-
  Check which destinations an account can reach, pull the lookup report, and submit a
  sender-ID whitelist request on the Tata Communications Mobile Messaging Exchange.
api: openapi/tata-communications-mobile-messaging-exchange-account-administration.json
operations:
  - getdestination
  - getreport
  - postsenderId
generated: '2026-07-25'
method: generated
source: openapi/tata-communications-mobile-messaging-exchange-account-administration.json
---

# Register a sender ID and check destinations

Use this before you send A2P traffic into a new market: confirm the destination is
reachable for your account, then get the sender ID you intend to display whitelisted.

## Before you start

- An approved application on `https://developer.tatacommunications.com/`, your onboarding
  `accountId`, and your Akana `appid`.
- No `host`/`basePath` is declared — the base URL arrives with your credential.
- **Read this specification defensively.** Every parameter on all three operations is
  declared optional, no request body schema is attached to `SenderIdWhitelistRequest`, and
  every response is a bare `default` with an empty description. Treat the shapes below as
  the contract's outline, and confirm the payload with your Tata Communications account
  team before writing to production.

## Step 1 — check the destination (`getdestination`)

`GET /destination`

- `accountId` (query), `mcc` (query), `mnc` (query), `appid` (header).

`mcc`/`mnc` are the ITU-T E.212 country and network codes for the destination operator —
the same codes the Number Intelligence API returns for a looked-up number, so
`numberLookupDetails` is the natural upstream step when you only have a phone number.

## Step 2 — pull the lookup report (`getreport`)

`GET /report`

- `accountId` (query), `appid` (header).

## Step 3 — request the sender ID (`postsenderId`)

`POST /senderId`

- `accountId` (query), `mcc` (query), `mnc` (query), `appid` (header).
- Body: `SenderIdWhitelistRequest` — **no schema is published for this body**. Do not
  fabricate one; obtain the field list from your account team.

This is the only write operation Tata Communications exposes anonymously in a
specification, and it is a per-destination registration, so it is not free of consequence:
`agentic-access/tata-communications-agentic-access.yml` classifies it as
`action-class: acting` with `consequence: physical`, a 300-second token ceiling, purpose
binding and required audit.

## Error handling

The specification documents no status codes for these three operations — only a `default`
response. Handle the whole `4xx`/`5xx` range defensively and expect the vendor
`{status, message}` envelope used elsewhere on the platform.

## Rules

- **No idempotency key exists.** `postsenderId` has no documented de-duplication behaviour,
  so do not blind-retry it — re-check with `getdestination`/`getreport` before resubmitting.
- Never invent the request body, a base URL, or a scope. Nothing about them is published.
- Sender-ID rules are regulatory and per-country; a successful call is a registration
  request, not a guarantee of delivery.
