---
layout: default
---

Getting started with the Ionic Platform
-----

The Ionic Platform offers a range of powerful, hybrid-focused mobile backend services and tools to make it easy to build
beautiful, performant hybrid apps. And do it quickly.

Follow this simple guide to getting started on the Ionic Platform:

## Step 1: Register

First, [Create an Account](https://apps.ionic.io/signup) on the Ionic Platform site.

## Step 2: Link your app

To create and sync your Ionic app to the Ionic dashboard, run:

```bash
$ ionic upload
```

Note: This will create and modify an ionic.project file in the root of your app's code directory. Do not modify the app_id field in the JSON; it is supplied by the server.

## Step 3: Identify your app

Install the `ionic-service-core` client code:

```bash
$ ionic add ionic-service-core
```

Next, add the script to the `www/index.html` file in your project:

```html
<script src="lib/ionic-service-core/ionic-core.js"></script>
```

Finally, Add the following code into your `www/js/app.js` file:

```javascript
// Add the 'ionic.service.core' module to your main angular module:
angular.module('test', ['ionic.service.core'])
// Identify App
.config(['$ionicAppProvider', function($ionicAppProvider) {
  // Identify app
  $ionicAppProvider.identify({
    // The App ID for the server
    app_id: 'YOUR_APP_ID',
    // The API key all services will use for this app
    api_key: 'YOUR_PUBLIC_API_KEY'
  });
}])
```

Replace `YOUR_APP_ID` and `YOUR_CLIENT_API_KEY` with the correct values from the app settings page of your app.  You can
find instructions for locating these <a href="/find-your-keys">here</a>.

## That's it!

Have a cookie; you now have the core code needed to identify your app with the Ionic Platform. Now you can choose a core
Ionic service from the left and try it out. Follow the specific service guide to continue.
