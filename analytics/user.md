---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Associating events with users
---

Ionic Analytics makes it easy to associate events with a specific user in your system. Each user
is automatically assigned a unique `user_id`, which is appended to every event sent out. This makes
it possible to track the number of unique users who did an event, or the average number of times users
did an an event.

If you want to include additional user data on your events, you will use the `identify` function
exposed on `$ionicUser`. All you need to do is call `identify` once you have a user, and all future events
will be bound to them:

```javascript
$ionicUser.identify({
  username: "Timmy",
  email: 'timmy@otoole.net'
});
```

Calling `identify` again will update this data on all future events, but it will not retroactively change user data on past events. This is because an event represents the state of the user at the time when the event was sent. If you want to measure, for instance, what percentage of users have `is_admin: true`, you can perform a segmentation on the `load` event collection, which is sent whenever a user opens your app.
