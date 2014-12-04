---
layout: default
---

<img src="/img/liveupdate-preview.png" style="width: 76px">

Deploying app updates with Ionic Deploy
-----

There are currently two ways to deploy new versions of your app. The first relies on the `ionic` command line
tool, and if you haven't uploaded a version of your app to the Ionic Platform you'll need to use the command
line to do that first.

The second one uses the Ionic Platform dashboard to deploy older versions of your app or to add notes to existing versions.

## Pushing new versions from the CLI

To release new versions of your app, make sure you've `upload`'ed at least once to register your app with the server:

```bash
$ ionic upload
```

*Note: you may be prompted to log in. Make sure you have an [Ionic](https://apps.ionic.io/signup) account*

Once you've uploaded the new version of your app, you can deploy it:

```bash
$ ionic deploy
```

This will deploy your current app web content and clients will now detect that there is a new version of the app.

## Deploying old versions from the dashboard

The dashboard for your project makes it easy to deploy and tag specific versions with release notes:

<img src="/img/deploy-ss.png" style="max-width: 100%">

Tap "DEPLOY" to promote that specific version to production. Depending on your app update process, users may be notified and your app updated with the latest code.
