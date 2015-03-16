---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Troubleshooting Ionic Push
-------

Below are some common issues with setting up Ionic Push, as well as their solutions.

## I always see "success: \[object\] \[object\]" when I register for notifications.

This is a debug alert which we allow you to toggle in order to simplify testing push notification registration.  If you 
would like to remove it, simply make sure you are passing the argument `canShowAlert: false` to your call of 
`$ionicPush.register()`.

## I can't find my App ID or API Key.

At the moment, you can find this information by going to <a href="apps.ionic.io">apps.ionic.io</a>, login, and selecting 
<strong>Ionic Services (alpha)</strong>.  Here you should see your <strong>App ID</strong>, 
<strong>Public API Key</strong>, and <strong>Private API Key</strong>. 

## When I try to test my app, I get a "cannot read property 'pushNotification' of undefined" error.

This error is often the result of testing push registration using `ionic serve` or a device emulator.  In these cases, 
Cordova will not initialize the push notification service.  For this reason, push notifications <strong>must</strong> be
tested on a physical device.

