---
name: number-lookup
description: Retrieve number lookup details via the Number Intelligence API.
api: openapi/tata-communications-number-intelligence-api-openapi.yml
operations:
  - numberLookupDetails
---

## Steps
1. **Authenticate** – Provide an `Authorization` header with a valid bearer token.
2. **Call** `GET /number/{phnum}` replacing `{phnum}` with the phone number.
3. **Handle** the JSON response containing lookup details.
