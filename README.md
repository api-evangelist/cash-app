# Cash App (cash-app)

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

Cash App is a consumer mobile-first financial services platform operated by Block, Inc. (formerly Square, Inc.). Cash App is not itself a chartered bank - its deposit accounts and the Cash App Card are issued by partner banks (historically Sutton Bank and Lincoln Savings Bank), while brokerage and bitcoin services run through Block subsidiaries. Its public developer surface is a merchant / payment-service-provider payment-acceptance product (Cash App Pay and Cash App Afterpay), not a consumer-permissioned data-access API.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/cash-app/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/cash-app/refs/heads/main/apis.yml)

## Open Finance Posture

- **First-party developer portal:** Yes - a real, public portal at [developers.cash.app](https://developers.cash.app/home) (built on Fern) that publishes downloadable OpenAPI 3.1 specifications.
- **Downloadable specs:** Yes - 12 OpenAPI 3.1.0 documents were harvested verbatim from the portal's "Available APIs" listing (`developers.cash.app/openapi.json`).
- **API families:** The Cash App Pay Partner API (Customer Request, Network, and Management APIs on `api.cash.app`, scoped API-key auth) and the Afterpay / Cash App Afterpay Global API (`global-api.afterpay.com`, HTTP Basic auth).
- **FDX / CFPB 1033:** No FDX participation or Section 1033 consumer-data-rights posture is documented in the developer portal. Consumer-side account data is reached by third parties through aggregators (e.g. Plaid) rather than a first-party FDX data-access API.

## Tags

- Financial Services
- Payments
- United States
- Fintech
- Neobank
- Buy Now Pay Later
- Payment Acceptance
- Digital Wallet

## Timestamps

- **Created:** 2026-07-23
- **Modified:** 2026-07-23

## APIs

### Cash App Pay Network API

Server-side REST API that registers merchants and processes payments using grants - the core Cash App Pay payment-processing surface for PSP partners.

- **Human URL:** [https://developers.cash.app/cash-app-pay-partner-api/api-reference/network-api](https://developers.cash.app/cash-app-pay-partner-api/api-reference/network-api)
- **Base URL:** `https://api.cash.app/network/v1`
- [OpenAPI](openapi/cash-app-network-api-openapi.json)

### Cash App Pay Customer Request API

REST API used to get permission from customers to perform actions on their accounts (such as collecting a payment), producing the grants consumed by the Network API. Wrapped by the Pay Kit JavaScript SDK.

- **Human URL:** [https://developers.cash.app/cash-app-pay-partner-api/api-reference/customer-request-api](https://developers.cash.app/cash-app-pay-partner-api/api-reference/customer-request-api)
- **Base URL:** `https://api.cash.app/customer-request/v1`
- [OpenAPI](openapi/cash-app-customer-request-api-openapi.json)

### Cash App Pay Management API

REST API that controls scoped API keys and webhooks, automating key aspects of a Cash App Pay integration including least-privileged microservice access.

- **Human URL:** [https://developers.cash.app/cash-app-pay-partner-api/api-reference/management-api](https://developers.cash.app/cash-app-pay-partner-api/api-reference/management-api)
- **Base URL:** `https://api.cash.app/management/v1`
- [OpenAPI](openapi/cash-app-management-api-openapi.json)

### Afterpay Global API (Cash App Afterpay)

The Afterpay / Cash App Afterpay buy-now-pay-later product is documented in the same portal and harvested here as nine OpenAPI documents on the `https://global-api.afterpay.com` host (HTTP Basic auth): Payments, Checkouts, Orders, Configuration, Disputes, Grants (Afterpay), Add Cash App Pay to Your Site (Grants), Service Status, and the deprecated Billing Agreements API.

- **Human URL:** [https://developers.cash.app/afterpay/api-reference/reference/introduction](https://developers.cash.app/afterpay/api-reference/reference/introduction)
- **Base URL:** `https://global-api.afterpay.com`
- OpenAPI specs: [Payments](openapi/cash-app-payments-openapi.json), [Checkouts](openapi/cash-app-checkouts-openapi.json), [Orders](openapi/cash-app-orders-openapi.json), [Configuration](openapi/cash-app-configuration-openapi.json), [Disputes](openapi/cash-app-disputes-openapi.json), [Grants - Afterpay](openapi/cash-app-grants-afterpay-openapi.json), [Grants - Cash App Pay](openapi/cash-app-grants-cash-app-pay-openapi.json), [Service Status](openapi/cash-app-service-status-openapi.json), [Billing Agreements (Deprecated)](openapi/cash-app-billing-agreements-deprecated-openapi.json)

## Common Properties

- [Website](https://cash.app/)
- [Developer Portal](https://developers.cash.app/home)
- [Documentation](https://developers.cash.app/cash-app-pay-partner-api/guides/welcome)
- [GitHub Organization](https://github.com/cashapp)
- [Terms of Service](https://cash.app/legal/us/en-us/tos)
- [Privacy Policy](https://cash.app/legal/us/en-us/privacy)
- [Support](https://cash.app/help)
- [Status Page](https://status.cash.app)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
