---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Ionic Push Android Setup
-------

Android push notifications use the <strong>Google Cloud Messaging (GCM)</strong> service.

## Step 1: Setting up GCM

### 1.1: Creating a Google API project

* Open the <a href="https://cloud.google.com/console">Google Developers Console</a>.
* If you haven't created an API project yet, click <strong>Create Project</strong>.
* Supply a project name and ID, then click <strong>Create</strong>.
* Once the project has been created, a page appears that displays your <strong>project ID</strong> and <strong>project 
number</strong> as seen below.  Copy down your project number. You will use it later on as the 
<strong>GCM sender ID</strong>.

<img style="width:100%;" src="/img/push-docs/google-project-console.png">

### 1.2: Enabling the GCM service

* In the sidebar on the left, select <strong>APIs</strong> under <strong>APIs & auth</strong>.
* In the displayed list of APIs, turn the <strong>Google Cloud Messaging for Android</strong> toggle to ON.  Your new 
list of enabled APIs should look something like the following:

<img style="width:100%;" src="/img/push-docs/enabled-apis-google.png">

### 1.3: Obtaining an API key

* In the sidebar on the left, select APIs & auth > Credentials.
* Under Public API access, click Create new key.
* In the Create a new key dialog, click Server key.
* In the resulting configuration dialog leave the box blank to allow connections from any IP.
* Click <strong>Create</strong>.  You should see your newly created API key as below.
* <strong>Save your API key!</strong>  You're going to need it later to hook up Ionic.io.

<img style="width:100%;" src="/img/push-docs/google-created-api-key.png">

## Step 2: Hooking up ionic.io

* In the `.config` of your project's `www/js/app.js` file, add a `gcm_id` field with your app's 
<strong>GCM sender ID</strong> as shown below. 

```javascript
    .config(['$ionicAppProvider', function($ionicAppProvider) {
      // Identify app
      $ionicAppProvider.identify({
        // The App ID for the server
        app_id: 'YOUR_APP_ID',
        // The API key all services will use for this app
        api_key: 'YOUR_PUBLIC_API_KEY',
        // The GCM project number
        gcm_id: 'YOUR_GCM_ID'
      });
    }])
```

* Now, navigate to your project directory and execute the following command:

```bash
    $ ionic push --google-api-key [your-google-api-key]
```

## All Done!

That's all there is, make sure your Ionic app is properly configured, and you're ready to go!