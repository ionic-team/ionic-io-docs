---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Ionic Push Quick Start
-------

Want to dive in to Ionic Push as quickly as possible?  Let's get started!

We've built a simple push notification starter app that, once configured, can be modified to your heart's content.

## Step 0: Set up your environment

Ionic Push is in alpha at the moment, so if you haven't already, install the alpha version of the Ionic CLI with the 
following command:

```bash
$ npm install -g ionic@1.4.0-alpha.6
```

## Step 1: Download the starter app

First off, open up a command line and enter the following:

```bash
$ ionic start myPushApp push
$ cd myPushApp
$ ionic upload
```

Congratulations!  You now have a (nearly) working Ionic app all set and uploaded to 
<a href="http://apps.ionic.io">apps.ionic.io</a>!  

## Step 2: Adding in your ID and API key

First, we need to identify this app as your own!  Go to <a href="http://apps.ionic.io">apps.ionic.io</a>, login, and select 
<strong>Ionic Services (alpha)</strong>.  Here you should see your <strong>App ID</strong>, 
<strong>Public API Key</strong>, and <strong>Private API Key</strong>. 

Now, open `www/js/app.js` in your Ionic app directory.  You should see a `.config` near the top that looks like this:

```javascript
.config(['$ionicAppProvider', function($ionicAppProvider) {
  // Identify app
  $ionicAppProvider.identify({
    // The App ID for the server
    app_id: 'YOUR_APP_ID',
    // The API key all services will use for this app
    api_key: 'YOUR_PUBLIC_API_KEY'
    // Your GCM sender ID/project number (Uncomment if supporting Android)
    //gcm_id: 'YOUR_GCM_ID'
  });
}])
```

Replace `app_id` with your <strong>App ID</strong> and `api_key` with your <strong>Public API Key</strong> from 
<a href="http://apps.ionic.io">apps.ionic.io</a>.

## Step 3: Adding Platform Support

<strong>Please note:</strong> Push notifications require a physical device to run.  You will <strong>not</strong> be 
able to test them on an emulator or with `ionic serve`.

Depending on the platforms you're planning on supporting, you should now 
follow either the <a href="/push/android">Android</a> or <a href="/push/ios">iOS</a> guide for device authentication.

## All done!

Congrats!  You now have a working Ionic app with push notifications!  Check out the guide on 
<a href="/push/send">Sending Push</a> to send some pushes!
