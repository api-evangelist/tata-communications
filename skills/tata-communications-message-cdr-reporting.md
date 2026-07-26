---
name: Pull message CDRs from the Tata Communications Mobile Messaging Exchange
description: >-
  Retrieve A2P/wholesale SMS call detail records for an account and time window, or for a
  single customer message id, from the Mobile Messaging Exchange CDR Report API.
api: openapi/tata-communications-mobile-messaging-exchange-cdr-report-api.json
operations:
  - top_25_cdr
  - cdr_by_messageId
generated: '2026-07-25'
method: generated
source: openapi/tata-communications-mobile-messaging-exchange-cdr-report-api.json
---

# Pull message CDRs from the Mobile Messaging Exchange

Use this to reconcile wholesale SMS traffic: what was attempted, what was submitted, what
was delivered, and why anything failed.

## Before you start

- An approved application on `https://developer.tatacommunications.com/` and the account id
  assigned to you at onboarding (`accountId`). One caller may hold more than one.
- No `host`/`basePath` is declared in the specification — the base URL arrives with your
  credential.
- Send the portal `Authorization` header; Mobile Messaging Exchange operations also carry an
  `appid` application-identifier header.

## Step 1 — the account window (`top_25_cdr`)

`GET /CDR/account/{accountId}`

- `accountId` (path, required).
- `fromDate`, `toDate` (query) — the reporting window.
- `pageNo`, `pageSize` (query) — offset pagination.

Returns an `OutputList`: `totalItems`, `displayItems`, and `items[]` of CDR records. Page
until you have collected `totalItems`.

**Timing rule from the provider:** a `400` on this operation may mean the window is not
ready, not that the request is malformed — the documented text is "CDRs for the selected
period are not loaded because the SMS retry period of 72 hours is not completed". Treat a
`400` on a recent window as *retry later*, not as a permanent failure.

## Step 2 — a single message (`cdr_by_messageId`)

`GET /CDR/message/{messageId}`

- `messageId` (path, required) — the internal unique message id, e.g. the
  `b94ef907-7778-442c-9743-fe02238c6977` shape published in the specification examples.

Returns one `SuccessResponse` with `requestTime`, `lastDeliveredTime`, `messageId`,
`accountId`, `destinationId`, `destinationCountry`, `destinationAddress`,
`originatingAddress`, `attemptedStatus`, `submittedStatus`, `deliveredStatus`, `errorCode`
and `errorDescription`.

Read the three status fields as a funnel — attempted, then submitted, then delivered — and
use `errorCode`/`errorDescription` only when `deliveredStatus` is not a success.

## Error handling

`400`, `401` and `500` are documented on both operations with the two-field envelope
`{status, message}`. This is not RFC 9457. See
`errors/tata-communications-problem-types.yml` and
`conventions/tata-communications-conventions.yml`.

## Rules

- Both operations are reads: safe to retry on `5xx`, and there is no idempotency key to
  send (none is published).
- Do not assume a maximum page size; none is documented. Start small and read
  `displayItems`.
- Field-level examples in `examples/tata-communications-examples.yml` come from the
  provider's own specification — use them for shapes, never as live data.
