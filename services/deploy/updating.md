---
layout: default
---

<img src="/img/liveupdate-preview.png" style="width: 76px">

Updating the app
-----

To actually perform an app update on the client side, you can use the `$ionicDeploy` service.


## Full manual mode

To control the complete app update cycle, use the following code snippet
that checks for updates, downloads, extracts, and then loads the new version. `$ionicUpdate.check()` will
continuously check for new updates at a predefined interval.

```javascript
angular.module('myApp', ['ionic', 'ionic.service.deploy'])

.run(['$ionicUpdate', function($ionicUpdate) {
  // Check for updates
  $ionicUpdate.check().then(function(response) {
     // response will be true/false
     if (response) {
         // Download the updates
         $ionicUpdate.download().then(function() {
             // Extract the updates
             $ionicUpdate.extract().then(function() {
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
     $ionicUpdate.load();
  }, function(error) {
     // Error checking for updates
  })
}]);
```

