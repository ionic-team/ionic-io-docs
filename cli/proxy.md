---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Working behind a proxy
---

Ionic CLI gives you the ability to your proxy your app's requests through the development server.

Let's say you want to proxy the requests from your app to `http://my.server.com/api`.

Since we type `ionic serve` - it will open a local node webserver to host your ionic files. The url defaults to `http://localhost:8100`.

If you open your browser and go to that url and make a request to `http://my.server.com/api/feed`, you would have to do a [CORS request](http://wikipedia.com) from your localhost to the my.server.com host.

However, to avoid this, we instead will send our app's requests to `http://localhost:8100/api/feed` to have our server issue the request and return, thus avoiding CORS issues.

First open your `ionic.project` settings file - and add the `proxies` attribute.

```json
{
  "name": "appname",
  "email": "",
  "app_id": "",
  "proxies": [
    {
      "path": "/api",
      "options": "http://my.server.com/api"
    }
  ]
}

```

* `path`: string that will be matched against after the host in the request URL (for example, the `/api` in `http://localhost:8100/api`)
* `options`: a string of the address to proxy to. Allows any options that are permitted on the [http](http://nodejs.org/api/http.html#http_http_request_options_callback) request options.
