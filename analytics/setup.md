---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

# Setting up Ionic Analytics
-----

## Installing the service

*Note: make sure to follow the [Getting Started](/getting-started) guide to install the core platform client libraries
before following this guide.*

Ionic Analytics is packaged as a Bower repository, so just use the `ionic add` command to install it:

```bash
$ ionic add ionic-service-analytics
```

## Including the JS Library

The command above will download the Ionic Analytics JS library, but we need to add it to our project code.

In your `www/index.html`, add the following script to the `<head>` just below the `ionic.bundle.js` import:

```html
<html>
  ...
  <head>
    ...
    <script src="lib/ionic-service-core/ionic-core.js"></script>
    <script src="lib/ionic-service-analytics/ionic-analytics.js"></script>
  </head>
```

Next, make sure to include the `ionic.service.analytics` module in your main Angular module:

```javascript
angular.module('myApp', ['ionic',  'ionic.service.analytics'])
```

Great! Now you're ready to use Ionic Analytics.

## Going deeper

Continue on to the [tracking guide](/analytics/tracking) to learn how to use Ionic Analytics in action. For a full breakdown of the Ionic Analytics Javascript API and how it works, take a look at the [JS API docs](/services/analytics/js).
