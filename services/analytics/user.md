---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Associating events with users
---

Ionic Analytics makes it easy to associate events with a specific user in your system. For example, you
may want to do this to make sure all `"Bought Socks"` events are tied to the correct `user_id` field
in your system.

Ionic Analytics exposes an `$ionicUser` service that can be used to identify
and associate analytics events with the current user in your system.

All you need to do is call `identify` once you have a user, and all future events
will be bound to them:

```javascript
$ionicUser.identify({
  username: "Timmy",
  email: 'timmy@otoole.net'
});
```

Feel free to send any data you'd like to associate with future events.

