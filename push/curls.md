---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Testing Ionic Push with curl
-------

Below are some common tasks associated with Ionic push, and a `curl` command to complete them.  For these commands,
you're going to need your <strong>Public API Key</strong>, <strong>Private API Key</strong>, and
<strong>App ID</strong>.  For some, you may also need a list of <strong>Device Tokens</strong> or a
<strong>Message ID</strong>.

## Send a push notification

```bash
curl -u [PRIVATE_API_KEY]: -H "Content-Type: application/json" -H "X-Ionic-Application-Id: [APP_ID]" https://push.ionic.io/api/v1/push -d '{"tokens":["[RECIPIENT_TOKENS]"],"notification":{"alert":"I come from planet Ion."}}'
```

## Check the status of a queued push notification

```bash
curl -H "Content-Type: application/json" -H "X-Ionic-Application-Id: [APP_ID]" https://push.ionic.io/api/v1/status/[message_id] -u [private_api_key]:
```