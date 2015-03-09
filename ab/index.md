---
layout: default
---

<img src="/img/ab-preview.png" style="width: 76px">

Ionic A/B Testing
------

The A/B Testing service, combined with the Deploy service, makes it easy to run visual and functional
experiments in real-time, all while integrating with your Analytics insights.

### Cloud Value

Cloud Value are basically just that: variables that are synced with a value on the backend. CVs make
it easy to tweak variables in your code without rebuilding your app, enabling live experimentation, debugging, and
refinement.

To use a Cloud Value, just inject the `$ionicAb` service and grab the correctly named value:

```javascript
.controller('AppCtrl', function($scope, $log, $ionicAb) {
  // Grab a dynamic variable set from the server.
  $ionicAb.value('initialPrice', 50).then(function(val) {
    $scope.initialPrice = val;
  });

  $log.debug('initial value', $scope.initialPrice);
});
```
### Experiments

Experiments are created on the server and specify a set of experimental values
that will be randomly distributed to clients. Experiments run for a length
of time and report the statistical outcome of each variant in the experiment.

To dynamically grab an experimental value, run:

```javascript
.controller('AppCtrl', function($scope, $log, $ionicAb) {
  // Grab the variant from the server
  $scope.purchasePage = $ionicAb.experiment('purchasePage');
});
```

### A/B Switch

The `ionic-ab` attribute directive works much like `ng-switch`, but with the power of Ionic Analytics.

```html
<div ionic-ab="purchasePage">
  <div ionic-ab-when="version1">
  </div>
  <div ionic-ab-when="version2">
  </div>
</div>
```

Depending on the value the client receives for the experiment defined in `purchasePage` on scope,
either the first child `<div>` shows, or the second one does.

Combine this with the Deploy service for realtime experiments and updates!
