---
layout: default
---

Ionic Push
------

Ionic Push makes it easy to send push notifications to your users.

Currently, the service supports sending notifications on both Apple's APNS and Google Cloud Messaging (GCM) for Android.

### Syncing Certificates and Identities

Before you can use the push notification service, you must register an app on the Apple Developer Center and/or the Google Play Console. [iOS](http://) [Android](http://)

Once you have your certificates, sync them with the ionic service:

```javascript
$ ionic add:cert /path/to/cert
```

### Sending a push notification

Sending a push notification involes performing a `POST` on the send API endpoint:

{% highlight bash %}
```bash
$ curl -X POST
$ curl -i -H "Accept: application/json" -X POST -d "{POST_JSON_HERE}" https://push.ionic.io/api/v1/send
```
{% endhighlight %}

Where `{POST_JSON_HERE}` is a JSON string of the form:

```javascript
  {
    platform: 'ios,android',
    token: 'blah',
    // OR
    tokens: ['blah', 'blah'],
    notification: {
      alert: "This important thing",
      OR
      alert: {
        'body': 'message',
        'action-loc-key': 
        'loc-key': 
        'loc-args': 
        'launch-image': 
      },
      badge: 2,
      sound: 'Sound file nmae'
      priority: //APNS priority
    }
  }
```

