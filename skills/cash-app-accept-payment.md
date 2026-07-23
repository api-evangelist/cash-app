---
name: Accept a Cash App Pay payment
description: Collect a customer grant via a Customer Request, then create and capture a payment on the Network API.
api: openapi/cash-app-network-api-openapi.json
operations: [create-request, retrieve-request, create-payment, capture-payment]
---

# Accept a Cash App Pay payment

Use this flow to charge a Cash App customer as a PSP partner.

## Auth (once per request)
- Every Network and Management call needs `Authorization: Client {CLIENT_ID} {KEY_ID}` **and** an
  `X-Signature: V1 {hmac}` header (HMAC-SHA256 over `{method}\n{path}\n{headers}\n{bodyDigest}`).
  In sandbox you may send `X-Signature: sandbox:skip-signature-check`.
- Use an API key that carries the `PAYMENTS_WRITE` scope. Keys expire after 30 days.
- Always send a consistent `X-Region` (e.g. `PDX`); idempotency is scoped to it.

## Steps
1. **Create a customer request** — `create-request` (Customer Request API) to ask the customer for
   permission (a grant) to collect a payment. Include a unique `idempotency_key` (1-64 chars).
2. Present the request through **Pay Kit** (`https://kit.cash.app/v1/pay.js`) and wait for the
   `CUSTOMER_REQUEST_APPROVED` event; optionally poll `retrieve-request` for the approved grant.
3. **Create the payment** — `create-payment` (Network API) referencing the approved `grant_id` and a
   fresh `idempotency_key`. Handle `PAYMENT_DECLINED_*` codes as permanent (do not retry).
4. **Capture** — if the payment was authorized (not auto-captured), call `capture-payment`.

## Rules
- Idempotency keys are case-sensitive and one-payload-per-key; a changed payload reusing a key returns
  `IDEMPOTENCY_KEY_REUSED`. See conventions/cash-app-conventions.yml.
- Decline codes: errors/cash-app-decline-codes.yml. API errors: errors/cash-app-problem-types.yml.
- Test amounts (7771 = insufficient funds, 7773 = risk, etc.): sandbox/cash-app-sandbox.yml.
