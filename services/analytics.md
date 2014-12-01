---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Ionic Analytics
-----

*Note: make sure to follow the [Getting Started](/services/getting-started) guide to install the core platform client libraries
before following this guide.*

The Ionic Analytics service makes it easy to add powerful analytics to your hybrid mobile apps.

Unlike other analytics providers, Ionic can infer user behavior through the deep
integration of the analytics system with the UI layer. This means Ionic can automatically
track taps and interactions, and also associate events with varios states in your app's routing (to generate heatmaps, for example).

## Using Ionic Analytics

We start by adding the analytics service client code:

```bash
$ ionic add ionic-service-analytics
```

## Tracking events

An "event" in the Analytics system is just a key/value pair, where the key
is an event name, and the value is an object with any data you'd like to 
associate with that event:

```javascript
.controller('MyCtrl', function($scope, $ionicTrack) {
  $ionicTrack.track('Load', {
    item: 100
  })
});
```

## Auto Tracking

To enable smart auto tracking of events, add `ion-track-auto` to the `<body>` tag:

```html
  <body ng-app="myApp" ion-track-auto>
```

This will automatically detect taps and clicks and send them to the server. Note: this is currently
required for heatmap support.

## Simple button directives

To quickly track a specific event on a tap event, use the `ion-track-click` attribute:

```html
<button ion-track="eventName" ion-track-data="expression">
```

For example, to track the current data in a scope object `userData` on tap:

```html
<button ion-track="start" ion-track-data="userData">Start</button>
```

And to send an object as string data:

```html
<button ion-track="start" ion-track-data="{'game': 'Mario'}">Start</button>
```

