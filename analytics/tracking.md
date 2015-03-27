---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Tracking events with Ionic Analytics
-----

An *event* in the Analytics system is a key/value pair that represents
a single action in your app, such as a purchase, scroll, signup, or login. The key is an event name, and the value is an object with any data you'd like to associate with that event.

To track events, just use `$ionicAnalytics.track`, which takes your event name and event data as arguments.

```javascript
.controller('MyCtrl', function($ionicAnalytics) {
  $ionicAnalytics.track('purchase', {
    item_id: 11,
    item_name: 'Zany Socks'
  });
});
```

Guidelines
-----
All of the events coming in under a single event name are called an *event collection*. The event name is a label for that event collection. To be able to track your app usage over time, make sure your event name is nonchanging and future-proof. Event names should also be verbs representing a single action a user takes — 'swipe', 'refresh', and 'logout' are good event names, whereas 'user' or 'is_admin' are not.

Feel free to put a lot of data into each event. The more properties you have, the more flexibility you have in filtering and tracking your app usage over time. Additionally,avoid using arrays in your event data, as these are hard to get a hold on with metrics. Instead, send multiple events to represent a sequence of actions.
