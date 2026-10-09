---
name: sonetel-create-an-ivr-voice-app
description: Create a Sonetel voice app (IVR / auto-attendant) and attach voice prompts to it.
api: openapi/sonetel-voice-apps-openapi.yml
operations:
- create-voiceapp-account
- get-voiceapps-account
- update-account-voiceappid
- post-user
- upload-message
generated: '2026-10-09'
method: generated
---

# Create a Sonetel voice app (IVR / auto-attendant) and attach voice prompts to it.

Auth: Bearer token from `create-JWT-token` (openapi/sonetel-authentication-openapi.yml). Base URL: https://public-api.sonetel.com. Errors come back as `{resource, status: failed, response: {code, detail}}`.

1. `create-voiceapp-account`: POST /account/{accountid}/voiceapp to create the app.
2. `get-voiceapps-account` lists the account's apps. Use it to confirm the app exists before you retry a create.
3. `post-user` (in this spec it is POST /account/{accountid}/voiceapp/{voiceappid}/prompt, despite the name) adds a prompt. `upload-message` (POST /prompt/{promptid}/message) uploads the prompt audio. Text-to-speech audio can be produced with `post-prompt-convert` (Text to speech API).
4. `update-account-voiceappid`: configure menu options. Then point a number at the app with `putaccount-accountid-phonenumbersubscription-phnum` (`connect_to_type`/`connect_to`).
Mirrors Sonetel's sample-scripts/create_new_ivr and ivr_config.
