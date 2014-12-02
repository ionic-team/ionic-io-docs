---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Ionic Analytics JS API
-----

## `$ionicTrack`

The `$ionicTrack` Angular service is used to send events to the Ionic Analytics system.

Example:

```javascript
angular.module('myApp', ['ionic', 'ionic.services.analytics'])

.run(['$ionicTrack', function($ionicTrack) {
  // The run function is useful for sending events on app load
  $ionicTrack.track('load', {
    'version': 1
  });
}])

.controller(['$scope', '$ionicTrack', function($scope, $ionicTrack) {
  $scope.newPost = function() {
    // The run function is useful for sending events on app load
    $ionicTrack.track('Post Created');
  };
}]);
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
event data copied from the current object value of `scopeData` which must be in scope.

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
  email: 'timmy@otoole.net`
});
```

Feel free to send any data you'd like to associate with future events.

