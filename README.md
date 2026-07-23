# Cash App (cash-app)

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
