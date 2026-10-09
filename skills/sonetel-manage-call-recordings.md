---
name: sonetel-manage-call-recordings
description: List, fetch, summarize and delete Sonetel call recordings.
api: openapi/sonetel-recorded-calls-openapi.yml
operations:
- get-call-recording
- get-recording-recordingId
- get-call-recording-recording-id-summarize
- delete-call-recording-recording-id
generated: '2026-10-09'
method: generated
---

# List, fetch, summarize and delete Sonetel call recordings.

Auth: Bearer token from `create-JWT-token` (openapi/sonetel-authentication-openapi.yml). Base URL: https://public-api.sonetel.com. Errors come back as `{resource, status: failed, response: {code, detail}}`.

1. `get-call-recording`: list recordings.
2. `get-recording-recordingId`: get one recording's details and download location.
3. `get-call-recording-recording-id-summarize`: get an AI summary of that recording.
4. `delete-call-recording-recording-id`: delete it. Deletion is permanent, so confirm first. The bulk `delete-call-recording` deletes many at once; avoid it unless the user explicitly asks.
Recording behaviour per account is set via `get-account-accountId-settings-data-mgr-call-recording` / `put-account-accountId-settings-data-mgr-call-recording` (Account API).
