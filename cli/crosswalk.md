---
layout: default
---

<img src="/img/analytics-preview.png" style="width: 76px">

Installing the Android Crosswalk Browser
---

Adding Crosswalk
###

`ionic browser add crosswalk` - This will download the Crosswalk web view binaries, the cordova-crosswalk-engine plugin, and the corrected 4.0.x branch of Cordova-android to install the crosswalk browser as a plugin for Android.

Specifying Crosswalk Version
###

Simply specify the Crosswalk version number after the `@` shown below as `9.38.208.10`.

`ionic browser add crosswalk@9.38.208.10`

You can find all of the Crosswalk versions [here](https://download.01.org/crosswalk/releases/crosswalk/android/stable/).

Removing Crosswalk
###

`ionic browser remove crosswalk` - This will remove the Crosswalk web view and revert the project back to use standard Android webviews.
