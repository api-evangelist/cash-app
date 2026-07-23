---
name: Provision scoped API keys and subscribe to webhooks
description: Bootstrap least-privilege API keys and register a signed webhook endpoint on the Management API.
api: openapi/cash-app-management-api-openapi.json
operations: [create-api-key, list-api-keys, create-webhook-endpoint, list-webhook-events, retrieve-webhook-endpoint]
---

# Provision scoped API keys and subscribe to webhooks

## Bootstrap keys
1. With your `client_id` + `client_secret` in the `Authorization` header, call `create-api-key` to
   mint a key with `API_KEYS_READ` and `API_KEYS_WRITE` scopes.
2. Using **that** key (not the client secret), call `create-api-key` again to create least-privilege
   operational keys (e.g. `PAYMENTS_READ`, `PAYMENTS_WRITE`). Use `list-api-keys` to audit.
3. Rotate keys several days before their 30-day `expires_at`; keep old keys until webhooks re-key.

## Subscribe to webhooks
1. Discover subscribable events with `list-webhook-events` (11 types: `payment.status.updated`,
   `refund.status.updated`, `grant.status.updated`, `dispute.created`, `dispute.state.updated`,
   `customer.created/updated/deleted`, `customer_request.state.updated`, `merchant.status.updated`,
   `grant.created`).
2. `create-webhook-endpoint` with the HTTPS URL, the subscribed event types, and the `api_key_id`
   used to sign deliveries. New domains need ~1 business day to be allowlisted.
3. Verify signatures on each delivery using the endpoint's API key (webhook-signature-generation).
   Respond `2xx` within the delivery timeout (default 5s). Allow Cash App source IPs through your
   firewall (see asyncapi/cash-app-webhooks.yml).

## Rules
- `WEBHOOK_ENDPOINT_TOO_MANY` / `WEBHOOK_ENDPOINT_NOT_FOUND`: errors/cash-app-problem-types.yml.
- Update the endpoint's `api_key_id` whenever the signing key is rotated.
