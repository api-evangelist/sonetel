---
name: sonetel-transcribe-an-audio-file
description: Submit an audio/video file to Sonetel's asynchronous transcription and poll for the result.
api: openapi/sonetel-transcription-openapi.yml
operations:
- transcribeFile
- get-transcription-transcribe_async-req_id
generated: '2026-10-09'
method: generated
---

# Submit an audio/video file to Sonetel's asynchronous transcription and poll for the result.

Auth: Bearer token from `create-JWT-token` (openapi/sonetel-authentication-openapi.yml). Base URL: https://public-api.sonetel.com. Errors come back as `{resource, status: failed, response: {code, detail}}`.

1. `transcribeFile`: POST /transcription/transcribe_async with `file` (a `file_id`, a `file_url` or `data`), `write_to` (a `text_id` and/or `callback_url`), `requested_by`, and an optional `transcription_profile` (`meeting-minutes`, `sonetel-voicemail` or `call-recording`).
2. Keep the returned `req_id`.
3. `get-transcription-transcribe_async-req_id`: poll until the request finishes, or wait for your `callback_url`. Back off between polls.
4. Files can be uploaded first through the File Manager API (`post-filemgr-upload`) to get a `file_id`.
