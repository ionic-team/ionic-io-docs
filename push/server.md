---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Ionic Push Backend (webhook) Setup
-------

Ionic Push lets you register a webhook url with the service so that you can receive device tokens and registration data 
at an API endpoint of your choosing.

## Register your webhook URL
The push service is able to send a webhook to your server with information, including the device token, when a device 
registers, when metadata is updated (such as the user_id) or if a token becomes invalid. Registering your webhook url is 
done via the CLI with the following command:

```bash
$ ionic push webhook_url http://example-server.com/example-api-endpoint
```

When a device registers it will receive a HTTP POST with JSON body. The post will contain an ios_token corresponding to 
the device upon registration. It will also contain the metadata object you attached when registering from your client 
code.  Below is an example POST body:

```javascript
{
  "ios_token":"b284a6f7545368d2d3f753263e3e2f2b7795be5263ed7c95017f628730edeaad",
  "metadata":{
    "user_id":100,
    "email":"foo@bar.com",
    "first_name":"John"
  },
  "token_invalid": false
}
```

<strong>Note: </strong>`"ios_token"` will be replaced with `"android_token"` when an Android device is registered.

If a device token becomes invalid, the webhook will receive a HTTP POST with JSON body like the following:

```javascript
{
  "ios_token":"b284a6f7545368d2d3f753263e3e2f2b7795be5263ed7c95017f628730edeaad",
  "token_invalid": true
}
```

## All Done!

That's all there is to it!