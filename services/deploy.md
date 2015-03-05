---
layout: default
---

<img src="/img/liveupdate-preview.png" style="width: 76px">

Deploying app updates with Ionic Deploy
-----

The Ionic deploy service makes it possible to ship new updates to your app without
going through the app store resubmission process. For many changes, Apple
allows immediate app updating without resubmission, if the core functionality or purpose of the
app does not change.

One important caveat is that this plugin is not able to perform binary app updates. There is
no possible mechanism to modify an App binary without resubmission to the app store, considering
each app is signed with a certificate ensuring its integrity. This is just how it works on the App Store, and it's 
out of our hands. However, the vast majority of app updates performed are simple HTML, CSS, and Javascript
code updates from the `www` folder in a Ionic/Cordova app.

## Using Ionic Deploy

There are three parts to the Ionic Deploy service: the client-side JS library, the command-line interface, and the dashboard view.

The JS library makes it possible to detect available updates, notify the user, and perform an update. The command-line
interface deploys new releases and manages old ones. The Dashboard view is our web-based tool for managing
deployed app versions, which can be shared across a team.

## Javascript Library

The JS Library for the deploy service provides means for watching for and performing app updates. There are two main modes of
operation: __user-prompt__, and __auto-update__. The user-prompt method allows you, the developer, to 
perform the detection and update manually. The auto-update mode provides a common
update process that works well in most apps (the auto-update method is not yet released).

To add the deploy service JS library to your app, run:

```bash
$ ionic add ionic-service-deploy
```

```javascript
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
```

## Command-line

To release new versions of your app, make sure you've typed `upload` at least once to register your app with the server,
then run: 

```bash
$ ionic deploy
```

This will deploy your current app web content, and clients will now detect that there is a new version of the app.

