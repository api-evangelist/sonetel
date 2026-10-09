---
name: sonetel-get-an-access-token
description: Get and refresh a Sonetel API access token (JWT) for use as a Bearer token on public-api.sonetel.com.
api: openapi/sonetel-authentication-openapi.yml
operations:
- create-JWT-token
generated: '2026-10-09'
method: generated
---

# Get and refresh a Sonetel API access token (JWT) for use as a Bearer token on public-api.sonetel.com.

Auth: Bearer token from `create-JWT-token` (openapi/sonetel-authentication-openapi.yml). Base URL: https://public-api.sonetel.com. Errors come back as `{resource, status: failed, response: {code, detail}}`.

1. `create-JWT-token`: POST https://api.sonetel.com/SonetelAuth/beta/oauth/token as multipart/form-data with `grant_type=password`, `username`, `password` and `refresh=yes` to also get a refresh token.
2. Send the returned `access_token` as `Authorization: Bearer <token>` on every call to https://public-api.sonetel.com.
3. When it expires, call `create-JWT-token` again with `grant_type=refresh_token` and the `refresh_token`. Do not resend the password.
4. Never log or echo tokens. Sonetel's sample scripts (sonetel-api-docs/sample-scripts/api-basics) show the same flow.
