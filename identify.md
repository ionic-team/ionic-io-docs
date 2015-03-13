---
layout: default
---

<img style="height:80px;" src="/img/push-docs/ionic_blog.png">
Ionic User
-------

Ionic User helps you keep track of all the users of your app, using <strong>just a single line of code</strong>.

## Setting up

Assuming you've followed the <a href="/getting-started">ionic.io Installation</a> guide, you're already 99% of the way 
there!  Just add the following code to your app whenever you want to identify a new user with the service:

```javascript
$ionicUser.identify({
  user_id: '0',
  name: 'Test User',
  message: 'I come from planet Ion'
});
```

<strong>Please note: </strong>The `user_id` field <strong>is expected</strong>, and should be unique to every user you identify.

You can use this feature to track <strong>any</strong> type of data for your users.  One idea to consider: if you're 
tracking anonymous users, you could specify `user_id` with Cordova's 
<a href="http://docs.phonegap.com/en/edge/cordova_device_device.md.html#device.uuid">device.uuid</a> functionality.

If you ever want to update the data for a user, use the following code:

```javascript
$ionicUser.push('key', value, unique);
```

This will add a `key: value` pair to the last user you identified.  If the `unique` value is set to `true`, the value 
specified <strong>must be unique</strong>.