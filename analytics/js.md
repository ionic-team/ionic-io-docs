---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Ionic Analytics JS API
-----

## `$ionicAnalytics`

The `$ionicAnalytics` service is used to send events to the Ionic Analytics system.

### `ionicAnalytics.track`

Takes an eventName and eventData. Both are arbitrary, but the eventName
should be the same as previous events if you wish to query on them later.

The data should be a dictionary of whatever event properties you want to track.
Nested objects are allowed, but arrays are discouraged. Keeping the structure
of the data as simple and consistent as possible will make querying easy.

```javascript
$ionicAnalytics.track('order', {
  price: 39.99,
  item: 'Time Machine'
});

$ionicAnalytics.identify('post_created', {
  length: 452,
  topic: 'fruits'
});
```

### `ionicAnalytics.identify`

Shortcut to `$ionicUser.identify`

### `ionicAnalytics.getDispatchInterval`, `ionicAnalytics.setDispatchInterval`

To save battery usage, we cache events in memory and send them in batch every 30 seconds. To change this time interval, use `setDispatchInterval`. Use a dispatch interval of 0 to disable event batching and dispatch all events immediately.

```javascript
$ionicAnalytics.getDispatchInterval(); // 30

// Dispatch events immediately (more battery-intensive)
$ionicAnalytics.setDispatchInterval(0);
```

## `ion-track` Directive

The `ion-track-EVENT` directive can be added to buttons and other event targets to automatically
send an event with some data based on a DOM event.

For example, to send an event on tap:

```html
<button class="button button-positive"
  ion-track-tap="Face Tapped"
  ion-track-data="scopeData">Tap Here</button>
```

Where `ion-track-tap` tracks tap events and sends an event with the event name of `"Face Tapped"` and
event data copied from the current object value of `scopeData`, which must be in scope.

You can also supply an object string directly instead of a scope object:

```html
<button class="button button-positive"
  ion-track-tap="Face Tapped"
  ion-track-data="{'account_id': 100}">Tap Here</button>
```

## `$ionicUser`

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

Grab the current user at any time by calling `$ionicUser.get()`.
