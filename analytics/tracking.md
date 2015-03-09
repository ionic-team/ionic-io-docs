---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Tracking events with Ionic Analytics
-----

An "event" in the Analytics system is just a key/value pair, where the key
is an event name, and the value is an object with any data you'd like to 
associate with that event:

```javascript
.controller('MyCtrl', function($scope, $ionicTrack) {
  $ionicTrack.track('Load', {
    item: 100
  })
});
```
