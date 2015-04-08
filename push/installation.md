---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Ionic Push Installation
-------

This guide shows you how to add Ionic Push to an existing app.  If you're starting from scratch, try out the 
<a href="/push/quick-start">Quick Start</a> tutorial.

## Step 0: Set up your environment

Ionic Push is in alpha at the moment, so if you haven't already, install the alpha version of the Ionic CLI with the 
following command:

```bash
$ npm install -g ionic@1.4.0-alpha.6
```

Also, make sure you've completed the <a href="/getting-started">ionic.io Installation</a> guide before adding Ionic 
Push.

## Step 1: Add in some plugins

* To get started with the client-side setup, there are three things we need to install; a Cordova plugin, 
<a href="http://ngcordova.com/docs/plugins/pushNotifications/">ngCordova wrapper</a> for that plugin, and our JS service 
code (<b>note:</b> make sure to run these commands in your Ionic/Cordova app's folder).

```bash
    $ ionic plugin add https://github.com/phonegap-build/PushPlugin.git
    $ ionic add ngCordova
    $ bower install ionic-service-push#master
```

* Next, we'll add the Push and ngCordova javascript to our `www/index.html` includes, right after the `ionic.bundle.js` 
file, but before `cordova.js`:

```html
    <script src="lib/ionic-service-push/ionic-push.js"></script>
    <script src="lib/ngCordova/dist/ng-cordova.js"></script>
```

* Now, we add the following code to our `www/js/app.js` file:

```javascript
    // Add the 'ionic.services.push' module to your main angular module: 
    angular.module('test', ['ionic.service.core', 'ionic.service.push'])
```

## Step 2: Identify a user

In order for push registration to work properly, you must register a user by following the guide for setting up the 
<a href="/identify">Ionic User</a> service.  These users may be anonymous, and any data you store on them is entirely 
optional, but they allow use of the powerful push notification dashboard later on.

## Step 3: Register your device

<strong>Please note:</strong> Push notifications require a physical device to run.  You will <strong>not</strong> be 
able to test them on an emulator or with `ionic serve`.

* First, your device must be set up to communicate with [GCM](https://developer.android.com/google/gcm/index.html) or 
[APNS](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html).  
To do this, follow the <a href="/push/android">Android</a> or <a href="/push/ios">iOS</a> guide.

* If you would like to receive device tokens on your own server as they are registered, you should also follow the <a href="/push/server">backend</a> guide.

* Once your device is set up, you can register it to receive push notifications by adding the following code to your 
project (usually on startup or in a root controller).

```javascript
    $ionicPush.register({
      canShowAlert: false, //Should new pushes show an alert on your screen?
      canSetBadge: true, //Should new pushes be allowed to update app icon badges?
      canPlaySound: false, //Should notifications be allowed to play a sound?
      canRunActionsOnWake: true, // Whether to run auto actions outside the app,
      onNotification: function(notification) {
        // Called for each notification.
      }
    }).then(function(deviceToken) {
      //Save the device token, if necessary
      $scope.token = deviceToken;
    });
```

* While you will probably have completed the call to `$ionicUser.identify()` before registering your device for push 
notifications (described <a href="/identify">here</a>), if you wish to identify users and register for push 
notifications at the same time, you can modify your call to `$ionicPush.register()` to include a user object as seen 
below:

```javascript
    $ionicPush.register({
      canShowAlert: false, //Should new pushes show an alert on your screen?
      canSetBadge: true, //Should new pushes be allowed to update app icon badges?
      canPlaySound: false, //Should notifications be allowed to play a sound?
      canRunActionsOnWake: true, // Whether to run auto actions outside the app,
      onNotification: function(notification) {
        // Called for each notification.
      }
    }, {
      user_id: 'ionic101',
      username: 'ionitron',
      age: 9001
    }).then(function(deviceToken) {
      //Save the device token, if necessary
      $scope.token = deviceToken;
    });
```

* <strong>Note</strong>, in general, you want to call `$ionicUser.identify()` <strong>every time</strong> the current 
user data is updated.  Passing user data to register is merely a convenience to simplify notification registration.

## Step 4: Getting device tokens

Upon registration, the <strong>device token</strong> of your testing device will be visible in your console logs (you
can also configure the service to send the token to a server of your own <a href="/push/server">here</a>).  Save this
token, as you're going to need it to send push notifications later on.

## All done!

Congrats!  You now have a working Ionic app with push notifications!  Check out the guide on 
<a href="/push/send">Sending Push</a> to send some pushes!
