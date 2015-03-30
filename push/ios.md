---
layout: default
---

<img src="/img/push-docs/pushlogo.png" style="width: 300px;">
Ionic Push iOS Setup
-------

iOS requires generating push certificates from the <strong>iOS Dev Center</strong>, then building a provisioning profile 
for your app.

## Step 1: Generating an SSL certificate

### 1.1: The certificate request

First, we're going to need to generate a certificate signing request file.  This is used to authenticate the creation of 
an SSL certificate.

* Launch the <strong>Keychain Access</strong> application on your Mac.  It will likely be in the 
<strong>Applications/Utilities</strong> folder.
* Navicate to <strong>Keychain Access</strong> > <strong>Certificate Assistant</strong> > 
<strong>Request a Certificate From a Certificate Authority</strong>
* Enter your name and email address.
* Select <strong>Saved to disk</strong> and hit <strong>continue</strong>.  This will download your 
`.certSigningRequest` file.

<img style="width:100%;" src="/img/push-docs/keychain-access.png">

### 1.2: The App ID

iOS applications installed on your development devices require an App ID.  For this example, you may use an ID that you 
have already created, or create a new one.  We'll describe how to create a new one below.

<strong>Note: </strong> As a convention, App ID's are represented as a reversed address (for example 
`com.ionicframework.IonicPushApp`).

* Go to the <a href="https://developer.apple.com/membercenter/index.action">Apple Developer Center</a>.
* Select <strong>Certificates, Identifiers, & Profiles</strong>:

<img style="width:100%;" src="/img/push-docs/certs-dash.png">

* Select <strong>Identifiers</strong> under the iOS Apps section.
* Here, you're going to see a list of your iOS App IDs.  Hit the <strong>+</strong> button in the top-right corner to 
register a new one.
* Choose a name for your new App ID and make sure to <strong>select the checkbox for Push Notifications</strong> under 
App Services.

<img style="width:100%;" src="/img/push-docs/push-checkbox.png">

* Choose an App ID Prefix (in most cases, the default will be just fine).
* For App ID Suffix, you need to select Explicit App ID and enter your iOS app's bundle ID.  This string should match 
the ID you've specified in your Ionic project's config.xml file.
* Hit <strong>Continue</strong> and make sure that all information was entered correctly.  Push Notifications should 
show up as <strong>Configurable</strong>.

<img style="width:100%;" src="/img/push-docs/app-confirm-screen.png">

### 1.3: Configuring the App ID

Now that your App ID is successfully created, it's time to configure it to send some Push Notifications.

* From the list of available iOS App IDs, select your new ID, then click <strong>Edit</strong>.
* Scroll down to the <strong>Push Notifications</strong> section of you app and click 
<strong>Create Certificate</strong> under the Development SSL Certificate section.

<img style="width:100%;" src="/img/push-docs/edit-app-push-section.png">

* The next screen will give you instructions to create a certificate signing request, which you have already done in the 
first section of this tutorial (this is the .certSigningRequest file you created).
* Once you have located your signing request, click <strong>Continue</strong> and follow the instructions to upload your 
file and generate a new certificate.

<img style="width:100%;" src="/img/push-docs/edit-app-download-ssl.png">

* Once the certificate is ready, download it from the App ID Edit screen and double click on the downloaded certificate 
to install it to your keychain.
* In Keychain Access, under <strong>My Certificates</strong>, find the certificate you just added.  It should be called 
<strong>Apple Development IOS Push Services</strong>.
* Right Click on it, select <strong>Export Apple Development IOS...</strong>, and save it as a <strong>.p12</strong> 
file.  You will be prompted to enter a password which will be used to protect the exported certificate, 
<strong>do not enter one</strong>.
* You may be asked to enter your OSX password at this point.

<img style="width:100%;" src="/img/push-docs/keychain-access-export.png">

Congratulations! You've just enabled Push Notification for your app in development mode.  Before you release you app to 
the app store, you need to repeat the previous steps, but instead generate a 
<strong>Production Push SSL Certificate</strong>.

## Step 2: Creating a Provisioning Profile

A Provisioning profile authenticates your device to run the app that you're developing.  Whether you're using an 
existing App ID or have created a new one, you're going to need to regenerate and install a Provisioning Profile. In 
this tutorial, we're going to create a new profile.

* Go to the <a href="https://developer.apple.com/membercenter/index.action">Apple Developer Center</a>.
* Select <strong>Certificates, Identifiers, & Profiles</strong>.
* Select <strong>Provisioning Profiles</strong> under the iOS Apps section.
* Select the <strong>+</strong> in the top-right of the screen to create a new iOS Provisioning Profile.
* Select <strong>iOS App Development</strong> as your profile type, then select <strong>Continue</strong>.
* Select the App ID you created in Section 1, then select <strong>Continue</strong>.
* Select the iOS development certificate you created on the next screen, then select <strong>Continue</strong>.
* You will now be asked which devices will be included in your provisioning profile.  Select all of your development 
devices then hit <strong>Continue</strong>.
* Choose a descriptive name for the profile, then hit <strong>Generate</strong>.
* Download the profile from the next screen with the <strong>Download</strong> button, then install it by double 
clicking on it (This should open Xcode).

## Step 3: Ensure the bundle identifier is correct

Because of the way Apple uses provisioning profiles, the app ID you specify on the Apple Developer site...

<img style="width:100%;" src="/img/push-docs/ios-app-ids.png">

...should match the bundle identifier you see in xCode...

<img style="width:100%;" src="/img/push-docs/xcode-ios-bundle.png">

...which can be ensured by editing the <code>config.xml</code> file at the root of your project.

<img style="width:100%;" src="/img/push-docs/config-xml-note.png">

## Step 4: Hooking up ionic.io

### Development

Before Ionic.io can send notifications, we're going to need the push certificates you created in step 1.

* Go to your Ionic project directory and execute the following command:

```bash
    $ ionic push --ios-dev-cert
```

* The CLI will prompt for the location of your push cert, which should be your PFX (.p12) file. Paste it in and hit 
enter. You should see a "Successfully uploaded certificate" message.

### Production

* Go to your Ionic project directory and execute the following command:

```bash
    $ ionic push --ios-prod-cert
```

* The CLI will prompt for the location of your push cert, which should be your PFX (.p12) file. Paste it in and hit
enter. You should see a "Successfully uploaded certificate" message.

* All you need to do now is turn on production mode for your app, which can be completed with the following command:

```bash
    $ ionic push --production-mode=y
```

## All Done!

That's all there is, make sure your Ionic app is properly configured, and you're ready to go!
