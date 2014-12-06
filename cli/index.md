---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Auto Tracking events
---

To enable smart auto tracking of events, add `ion-track-auto` to the `<body>` tag:

```html
  <body ng-app="myApp" ion-track-auto>
```

This will automatically detect taps and clicks and send them to the server. Note: this is currently
required for heatmap support.

## Simple event directives

To quickly track a specific event on a tap event, use the `ion-track-tap` attribute:

```html
<button ion-track-tap="eventName" ion-track-data="expression">
```

For example, to track the current data in a scope object `userData` on tap:

```html
<button ion-track-tap="start" ion-track-data="userData">Start</button>
```

And to send an object as string data:

```html
<button ion-track-tap="start" ion-track-data="{'game': 'Mario'}">Start</button>
```

You can also substitute `tap` for many other events, like `hold`, `release`, and `doubletap` (the most useful ones). For example, to send an event on doubletap of an image:

```html
<img ion-track-doubletap="avatarTap" ion-track-data="userProfile" ng-src="{{userProfile.face}}">
```
