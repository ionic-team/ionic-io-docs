---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Getting started with Ionic Analytics
-----

*Note: make sure to follow the [Getting Started](/services/getting-started) guide to install the core platform client libraries
before following this guide.*

The Ionic Analytics service makes it easy to add powerful analytics to your hybrid mobile apps.

Unlike other analytics providers, Ionic can infer user behavior through the deep
integration of the analytics system with the UI layer. This means Ionic can automatically
track taps and interactions, and also associate events with varios states in your app's routing (to generate heatmaps, for example).

## Installing the service

Installing Ionic Analytics is easy. Just use the `$ ionic service` command to add it:

```bash
$ ionic service add analytics
```

## Including the JS Library

The command above will download the Ionic Analytics JS library, but we need to add it to our
project code.

In your `www/index.html`, add the following script to the `<head>`:

```html
<html>
  ...
  <head>
    ...
    <script src="lib/ionic-service-core/ionic-core.js">
    <script src="lib/ionic-service-analytics/ionic-analytics.js">
  </head>
```

Next, make sure to include the `ionic.service.analytics` module in your main Angular module:

```javascript
angular.module('myApp', ['ionic',  'ionic.service.analytics'])
```

## Going deeper

For a full breakdown of the Ionic Analytics Javascript API and how it works, take a look at the [JS API docs](/services/analytics/js).
