---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Ionic Push, Sending Messages
-------

Assuming you have registered some devices and uploaded your developer SSL certificates through the CLI, you're ready to 
start sending some push notifications!  There are two main ways of accomplishing this; through the REST API and using 
the <a href="http://apps.ionic.io">ionic.io</a> dashboard.

## Using the REST API

Ionic.io has an API endpoint which you can use to send push notifications from your backend server (or with a 
<code>curl</code> for testing).

You can send a push notification by making a POST to <strong>https://push.ionic.io/api/v1/push</strong> with the 
following headers.

```javascript
Content-Type: application/json
X-Ionic-Application-Id: YOUR_APP_ID
```

The POST data should be a JSON object of the following format as well (`"ios"`, and `"android"` sections of 
`"notification"` are optional customizations):

```javascript
{
  "tokens":[
    "b284a6f7545368d2d3f753263e3e2f2b7795be5263ed7c95017f628730edeaad",
    "d609f7cba82fdd0a568d5ada649cddc5ebb65f08e7fc72599d8d47390bfc0f20"
  ],
  "notification":{
    "alert":"Hello World!",
    "ios":{
      "badge":1,
      "sound":"ping.aiff",
      "expiry": 1423238641,
      "priority": 10,
      "contentAvailable": true,
      "payload":{
        "key1":"value",
        "key2":"value"
      }
    },
    "android":{
      "collapseKey":"foo",
      "delayWhileIdle":true,
      "timeToLive":300,
      "payload":{
        "key1":"value",
        "key2":"value"
      }
    }
  }
}
```

Finally, your POST should authenticate using 
<a href="http://en.wikipedia.org/wiki/Basic_access_authentication">Basic Access Authentication</a>, with no password and 
your <strong>private API key</strong> for a username.  Below is an example of this using Python and urllib2:

```python
post_data = YOUR_POST_JSON_OBJECT
app_id = YOUR_APP_ID
app_key = YOUR_PRIVATE_API_KEY
url = "https://push.ionic.io/api/v1/push"
req = urllib2.Request(url, data=post_data)
req.add_header("Content-Type", "application/json")
req.add_header("X-Ionic-Application-Id", app_id)
b64 = base64.encodestring('%s:%s' % (app_key, '')).replace('\n', '')
req.add_header("Authorization", "Basic %s" % b64)
resp = urllib2.urlopen(req)
```

## A handy tip

In addition to the `onNotification` function described <a href="/push/installation">Here</a>, you can specify which 
$state a notification should open your app to using the payload.  Below is an example JSON object highlighting this.

```javascript
{
  "tokens":["1f0ab62df8b5c672653dea8b01d1bab4dc1b15da93f99216b5ba0f621692a89f"],
  "notification": {
    "alert": "Basic push!",
    "ios":{
      "priority": 10,
      "badge":2,
      "payload":{ "$state": "about", "$stateParams": "{\"id\": 1}" }
    }
  }
}
```

## Using the ionic.io dash

In addition to the API, ionic.io provides a powerful tool for scheduling and targeting push notifications.  This feature
leverages <a href="/identify">Ionic User</a> to let you pare down your users however you see fit.

To get started with it, simply go to https://apps.ionic.io/app/YOUR\_APP\_ID and click <strong>Push</strong>.
