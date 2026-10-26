# Tata Communications (tata-communications)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Tata Communications is the global wholesale carrier and digital-infrastructure arm of India's Tata Group, headquartered in Mumbai. It owns one of the world's largest subsea cable networks, carries a large share of global internet routes, and sells international voice and messaging wholesale, IZO network services, MOVE global IoT and eSIM connectivity, MVNE services, and — through its October 2023 acquisition of Kaleyra — a full CPaaS, UCaaS, and CCaaS stack. It sits in the supply layer of the telecom value chain: a carrier's carrier whose customers are mostly other operators, enterprises, and aggregators rather than individual developers.

Its API posture matches that position and is honestly partner-gated.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/tata-communications/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/tata-communications/refs/heads/main/apis.yml)

## Tags

- Telecommunications
- India
- Wholesale Carrier
- CPaaS
- Messaging
- Voice
- IoT
- eSIM
- Number Intelligence
- Connectivity
- Subsea Cable
- Partner Gated

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## Developer Surface

Tata Communications runs a real first-party developer portal at [developer.tatacommunications.com](https://developer.tatacommunications.com/) (HTTP 200), built on Akana Community Manager. Its public catalogue names **49 APIs**, but only **3** are marked `Public` and return a downloadable Swagger 2.0 document to an anonymous caller — the other **46 answer HTTP 401**. That is a real portal, not a marketing page, and it is 94% gated.

Tata Communications MOVE (global IoT / eSIM / MVNE) runs a **second, separate** developer portal on Azure API Management at [move-external-apim-prod.developer.azure-api.net](https://move-external-apim-prod.developer.azure-api.net/) (HTTP 200). Three API products are named publicly; the reference and every machine-readable export sit behind sign-in (anonymous catalogue calls return 401).

The DIGO CPaaS documentation site publishes a faithful HTML product breakdown but no downloadable definition, and access is explicitly sales-led — *"You will need auth token to access our APIs. Please fill in your details below and we will get in touch with you."* At the time of review its TLS certificate had **expired on 2026-07-23** and its console host `console-ssp.tatacommunicationsdigo.io` did not resolve.

The corporate [API Zone](https://www.tatacommunications.com/api-zone) marketing page promises *"easy to use REST APIs … through our purpose-built API Zone"* — and its **"API Reference" link points at `https://docs.tclaws.co/`, which is NXDOMAIN**.

In practice, Tata Communications' CPaaS business reaches developers through the separately branded **Kaleyra** portal (`developers.kaleyra.io`, acquired October 2023), whose pages carry no Tata branding and which is profiled separately in this network.

## CAMARA and GSMA Open Gateway

**No CAMARA reference of any kind was found** on tatacommunications.com, on the first-party developer portal, on the MOVE portal, or on DIGO. Tata Communications is not a mobile network operator, and no GSMA Open Gateway participation could be evidenced. There is not even a press release here — this is an absence, not an announcement.

The GSMA Open Gateway / CAMARA memorandum of understanding widely reported in November 2025 belongs to **Tata Elxsi**, a *different* Tata Group company (design and engineering services, TETHER platform). It must not be attributed to Tata Communications.

The closest adjacent capabilities are pre-CAMARA and carrier-native rather than CAMARA-shaped: the **Number Intelligence API** (E.164 lookup, portability dip indicator, MCC/MNC) on the first-party portal, and DIGO's **Mobile Connect** (the older GSMA identity scheme), **One Tap Authentication**, **HLR Lookup**, and **Verified Calls / Verified SMS** product entries.

No TM Forum Open API conformance certification, and no 3GPP NEF/SCEF exposure surface, could be evidenced.

## APIs

### Number Intelligence API

Queries the number-lookup details of any E.164 number and returns subscriber type, the current and parent network, the port-corrected service provider network (SPN), and MCC/MNC when the number is mobile.

- **Human URL:** [https://developer.tatacommunications.com/#/api/0cd4be86-167c-4770-9459-e68fe925f63a.tcl](https://developer.tatacommunications.com/#/api/0cd4be86-167c-4770-9459-e68fe925f63a.tcl)

#### Properties

- [OpenAPI](openapi/tata-communications-number-intelligence-api.json) — Swagger 2.0, harvested 2026-07-25, 2 operations
- [Documentation](https://developer.tatacommunications.com/#/api/0cd4be86-167c-4770-9459-e68fe925f63a.tcl)

### Mobile Messaging Exchange - Account Administration

Account administration and lookup reporting for the Tata Communications Mobile Messaging Exchange (A2P / wholesale SMS) platform — destination lookup, report retrieval, and sender-ID registration.

- **Human URL:** [https://developer.tatacommunications.com/#/api/5d771bb7-97eb-4e36-bf9d-9edd3d51baa8.tcl](https://developer.tatacommunications.com/#/api/5d771bb7-97eb-4e36-bf9d-9edd3d51baa8.tcl)

#### Properties

- [OpenAPI](openapi/tata-communications-mobile-messaging-exchange-account-administration.json) — Swagger 2.0, harvested 2026-07-25, 3 operations
- [Documentation](https://developer.tatacommunications.com/#/api/5d771bb7-97eb-4e36-bf9d-9edd3d51baa8.tcl)

### Mobile Messaging Exchange - CDR Report API

Call/message detail record reporting for the Mobile Messaging Exchange — message logs by account ID and time frame, or by a single customer message ID.

- **Human URL:** [https://developer.tatacommunications.com/#/api/eef35c15-1259-4b32-8d00-19b8b913ce2d.tcl](https://developer.tatacommunications.com/#/api/eef35c15-1259-4b32-8d00-19b8b913ce2d.tcl)

#### Properties

- [OpenAPI](openapi/tata-communications-mobile-messaging-exchange-cdr-report-api.json) — Swagger 2.0, harvested 2026-07-25, 2 operations
- [Documentation](https://developer.tatacommunications.com/#/api/eef35c15-1259-4b32-8d00-19b8b913ce2d.tcl)

### MOVE SIM Connect API

Full-service API for the MOVE platform SIM Connect product, supporting management of a tenancy, its key entities and services, and the products the tenancy avails. Reference behind portal sign-in; no anonymous machine-readable definition.

- **Human URL:** [https://move-external-apim-prod.developer.azure-api.net/api-details#api=move-api](https://move-external-apim-prod.developer.azure-api.net/api-details#api=move-api)

### MOVE IOT Connect API

MOVE platform IOT API, permitting management of a tenancy of the MOVE IOT Connect product. Reference behind portal sign-in; no anonymous machine-readable definition.

- **Human URL:** [https://move-external-apim-prod.developer.azure-api.net/api-details#api=move-iot-api](https://move-external-apim-prod.developer.azure-api.net/api-details#api=move-iot-api)

### MOVE Access Token API

Issues an OAuth 2.0 bearer access token used to call the other MOVE APIs. Reference behind portal sign-in.

- **Human URL:** [https://move-external-apim-prod.developer.azure-api.net/api-details#api=tata-move-api-access-manager](https://move-external-apim-prod.developer.azure-api.net/api-details#api=tata-move-api-access-manager)

## Authentication

| Surface | Scheme |
| --- | --- |
| developer.tatacommunications.com | Opaque `Authorization` header ("used for authentication in Akana"); no `securityDefinitions` in the published documents |
| MOVE (Azure API Management) | OAuth 2.0 bearer token, issued by the Move Access Token API |
| DIGO | Auth token issued on request after a sales contact form |

**CIBA does not appear anywhere.** That follows from the CAMARA absence — there is no network-based authorization surface to back it. Neither `/.well-known/openid-configuration` nor `/.well-known/oauth-authorization-server` is served (both 404).

## Source Code and SDKs

The GitHub organisations [tatacommunications](https://github.com/tatacommunications) and [tata-communications](https://github.com/tata-communications) both exist and both have **0 public repositories**. No first-party SDK was found on npm, PyPI, Maven, or NuGet. No public Postman workspace, GraphQL endpoint, published `.proto`, or AsyncAPI document was found.

## Links

- [Website](https://www.tatacommunications.com/)
- [Developer Portal](https://developer.tatacommunications.com/)
- [API Catalogue](https://developer.tatacommunications.com/apis)
- [MOVE API Developer Portal](https://move-external-apim-prod.developer.azure-api.net/)
- [API Zone](https://www.tatacommunications.com/api-zone)
- [Blog](https://www.tatacommunications.com/blog/)
