---
name: sonetel-buy-a-phone-number
description: Find an available Sonetel phone number in a country, subscribe to it, and route its incoming calls.
api: openapi/sonetel-phone-numbers-openapi.yml
operations:
- get-country
- get-stock
- get-numberstocksummary-country-availablephonenumber
- postaccount-accountid-phonenumbersubscription
- putaccount-accountid-phonenumbersubscription-phnum
- get-subscribed-numbers
generated: '2026-10-09'
method: generated
---

# Find an available Sonetel phone number in a country, subscribe to it, and route its incoming calls.

Auth: Bearer token from `create-JWT-token` (openapi/sonetel-authentication-openapi.yml). Base URL: https://public-api.sonetel.com. Errors come back as `{resource, status: failed, response: {code, detail}}`.

1. Get the `account_id` with `get-users-userId` (GET /account/{accountId}, in openapi/sonetel-account-openapi.yml).
2. `get-country`: look up the three-letter ISO country code.
3. `get-stock`, then `get-numberstocksummary-country-availablephonenumber`: list numbers available in that country.
4. `postaccount-accountid-phonenumbersubscription`: subscribe with `{"phnum": "..."}`. You can also set `connect_to_type` and `connect_to`. **This purchases a number and costs money, so confirm with the user first.** It is not idempotent: check `get-subscribed-numbers` before you retry.
5. `putaccount-accountid-phonenumbersubscription-phnum`: change call routing (`connect_to_type`, `connect_to`, both required). This is the call-forwarding flow in Sonetel's sample-scripts/call-forwarding.
6. `get-subscribed-numbers` confirms the subscription status.
