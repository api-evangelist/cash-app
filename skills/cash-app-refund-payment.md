---
name: Refund a Cash App Pay payment
description: Issue and capture a refund against a captured Network API payment, handling decline codes.
api: openapi/cash-app-network-api-openapi.json
operations: [retrieve-payment, create-refund, capture-refund, retrieve-refund]
---

# Refund a Cash App Pay payment

## Preconditions
- The payment must be **captured** first — refunding an uncaptured payment returns
  `REFUND_INVALID_PAYMENT_UNCAPTURED` (void it instead). Confirm state with `retrieve-payment`.
- Use an API key with a refund-write scope; sign every request (see conventions/).

## Steps
1. **Create the refund** — `create-refund` with the `payment_id`, refund `amount`, and a unique
   `idempotency_key`. A refund amount above the refundable balance returns `REFUND_INVALID_TOO_LARGE`.
2. **Capture the refund** — `capture-refund` if the refund is created in an authorized state.
3. **Confirm** — poll `retrieve-refund` for the final state.

## Rules
- `REFUND_DECLINED_RISK`, `REFUND_DECLINED_COMPLIANCE`, `REFUND_DECLINED_OTHER` are permanent — do not
  retry; see errors/cash-app-decline-codes.yml.
- To reverse before settlement, use `void-refund` (or `void-refund-by-idempotency-key`).
- Sandbox: amount 7773 forces `REFUND_DECLINED_RISK` (sandbox/cash-app-sandbox.yml).
