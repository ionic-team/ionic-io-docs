---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Troubleshooting Ionic Push
-------

Below are some common issues with setting up Ionic Push, as well as their solutions.

## How can I check the status of a queued push notification?

When you queue a message for push, our server will return a `message_id` field that you can use to check the status of
the notification.  Use the following `curl` (Edited with your `app_id`, `message_id`, and `private_api_key`) to quickly
check up on a notification:

```bash
curl -H "Content-Type: application/json" -H "X-Ionic-Application-Id: [APP_ID]" https://push.ionic.io/api/v1/status/[message_id] -u [private_api_key]:
```

## I always see "success: \[object\] \[object\]" when I register for notifications.

This is a debug alert which we allow you to toggle in order to simplify testing push notification registration.  If you 
would like to remove it, simply make sure you are passing the argument `canShowAlert: false` to your call of 
`$ionicPush.register()`.

## I can't find my App ID or API Key.

At the moment, you can find this information by going to <a href="http://apps.ionic.io">apps.ionic.io</a>, login, and selecting 
<strong>Ionic Services (alpha)</strong>.  Here you should see your <strong>App ID</strong>, 
<strong>Public API Key</strong>, and <strong>Private API Key</strong>. 

## I want my app to open to a specific state when I receive a notification.

In addition to handling this in the `onNotification` function described <a href="/push/installation">Here</a>, you can 
specify which $state a notification should open your app to using the push payload.  Below is an example JSON object 
highlighting this.

```javascript
{
  "tokens":["1f0ab62df8b5c672653dea8b01d1bab4dc1b15da93f99216b5ba0f621692a89f"],
  "notification": {
    "alert": "Basic push!",
    "ios":{
      "priority": 10,
      "badge":2,
      "payload":{ "$state": "about", "$stateParams": "{\"id\": 1}" }
    }
  }
}
```

## I want to send my push to a list of tokens that contain both iOS and Android devices.

This is totally A-OK!  Our backend will parse the tokens you send and automatically detect their platform.

## When I try to test my app, I get a "cannot read property 'pushNotification' of undefined" error.

This error is often the result of testing push registration using `ionic serve` or a device emulator.  In these cases, 
Cordova will not initialize the push notification service.  For this reason, push notifications <strong>must</strong> be
tested on a physical device.

