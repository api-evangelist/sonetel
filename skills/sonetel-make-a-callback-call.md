---
name: sonetel-make-a-callback-call
description: 'Connect two parties with a Sonetel callback call: Sonetel calls call1 first, then bridges to call2.'
api: openapi/sonetel-make-calls-openapi.yml
operations:
- post-make-calls-call-call-back
generated: '2026-10-09'
method: generated
---

# Connect two parties with a Sonetel callback call: Sonetel calls call1 first, then bridges to call2.

Auth: Bearer token from `create-JWT-token` (openapi/sonetel-authentication-openapi.yml). Base URL: https://public-api.sonetel.com. Errors come back as `{resource, status: failed, response: {code, detail}}`.

1. Get a token first (see sonetel-get-an-access-token).
2. `post-make-calls-call-call-back`: POST /make-calls/call/call-back with `call1` (your own or a colleague's number, email or extension; per the spec this must belong to your company), `call2` (the person to reach), and caller IDs `show_1`/`show_2` (the spec recommends `automatic`). You can also send `app_id` to identify your app.
3. Each request places real, billable calls. Do not retry blindly after a timeout.
