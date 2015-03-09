---
layout: default
---

<img src="/img/liveupdate-preview.png" style="width: 76px">

Updating the app
-----

To actually perform an app update on the client side, you can use the `$ionicDeploy` service.

## Simple mode

To detect and perform app updates, use 

```javascript
$ionicDeploy.check().then(function(response) {
});
```

## Full manual mode

To control the complete app update cycle, use the following code snippet
that checks for updates, downloads, extracts, and then loads the new version. `$ionicDeploy.check()` will
continuously check for new updates at a predefined interval.

```javascript
angular.module('myApp', ['ionic', 'ionic.service.deploy'])

.run(['$ionicDeploy', function($ionicDeploy) {
  // Check for updates
  $ionicDeploy.check().then(function(response) {
     // response will be true/false
     if (response) {
         // Download the updates
         $ionicDeploy.download().then(function() {
             // Extract the updates
             $ionicDeploy.extract().then(function() {
                 // Load the updated version
                 $ionicTrack.load();
             }, function(error) {
                 // Error extracting
             }, function(progress) {
                 // Do something with the zip extraction progress
                 $scope.extraction_progress = progress;
             });
         }, function(error) {
             // Error downloading the updates
         }, function(progress) {
             // Do something with the download progress
             $scope.download_progress = progress;
         });
     }
  } else {
     // No updates, load the most up to date version of the app
     $ionicDeploy.load();
  }, function(error) {
     // Error checking for updates
  })
}]);
```

