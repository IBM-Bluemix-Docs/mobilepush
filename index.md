---

copyright:
  years: 2015, 2017, 2018, 2019
lastupdated: "2019-05-30"

keywords: push notifications, before you begin

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Getting started with Push
{: #getting-started-with-push}

In this {{site.data.keyword.mobilepushfull}} getting started tutorial, we walk through the process of enabling an Android app to receive push notifications and sending a basic push notification to a device.
{:shortdesc}

<div id="prerequisites"></div>

## Before you begin
{: #prereqs}

You'll need a [IBM Cloud account](https://cloud.ibm.com/registration/), an instance of the 
{{site.data.keyword.mobilepushshort}} service, and the following tools and requirements:

  * Android API 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android helloPush sample app](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} and 
  [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} SDKs installed by using 
  either Android Studio or Gradle

## Step 1: Configure your {{site.data.keyword.mobilepushshort}} instance for Android devices

1. Copy the package name from the sample `AndroidManifest.xml` file.

2. Create a FCM app and add the package name of your Android app:
  1. In the the [Firebase console](https://console.firebase.google.com){: new_window}, click **Add Project**, provide a 
  project name, and click **Create Project**.
  2. Click **Add Firebase to your Android app**, enter the app package name, and click **Register App**. You can skip the 
  next two prompts by click **Continue > Finish**. 

3. Add the FCM credentials to your {{site.data.keyword.mobilepushshort}} instance:
  1. In the Firebase console, go to **Settings > Project Settings > Cloud Messaging**, and copy the Server key and Sender ID.
  2. In the {{site.data.keyword.Bluemix_notm}} console, open the dashboard for your service instance.
  3. Click **Manage > Configure**.
  4. Enter the Sender ID and Server key to the **GCM/FCM Push Credentials** field.

## Step 2: Enable your Android app to send push notifications

1. Configure the project level `build.gradle` and module level `build.gradle` files:

  * Add the SDK dependency to the project level `build.gradle` file:
  
  ```
  dependencies {
  ........
  compile group: 'com.ibm.mobilefirstplatform.clientsdk.android',
      name: 'push',
      version: '3.+',
      ext: 'aar',
      transitive: true
  .......
	      }
  ```
  {: codeblock}

  * Add the following dependencies to the module level `build.gradle` file:
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * Add the Google play services dependency to the end of the module level `build.gradle` file after the dependencies:
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * Add the following permissions to your app's `AndroidManifest.xml` file:
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
  <uses-permission android:name="android.permission.GET_ACCOUNTS" />
  <uses-permission android:name="android.permission.USE_CREDENTIALS" />
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  ```
  {: codeblock}
  
  * Add the notification intent settings for the activity. 
  
  This setting starts the app when the user clicks the received notification from the notification area. Replace 
  `<yourAndroidPackageName>` with the app package name that's used in your app.
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * Update the FCM intent service and intent filters for the `RECEIVE` and `REGISTRATION` event notifications:
  
  ```
  <service android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushIntentService"
  android:exported="true" >
  <intent-filter>
     <action android:name="com.google.firebase.MESSAGING_EVENT" />
  </intent-filter>
  </service>
  <service
  android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPush"android:exported="true" >
  <intent-filter>
   <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
  </intent-filter>
  </service>
  ```
  {: codeblock}
  
2. Open the app in Android Studio, and add the `google-services.json` file to the app module root directory.

3. Initialize the core SDK and the Push SDK. 

A common place to put the initialization code is the onCreate() method of the main activity in your Android app:

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... where `<bluemixRegionSuffix>` is the location where the app is hosted. You can use any of the following values:

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID is the push app GUID value and clientSecret is the push client secret value. 

## Step 3: Register your Android device with your {{site.data.keyword.mobilepushshort}} instance

1. Run your app.

2. Use the MFPPush.register() API to register your device to enable user-based notifications.

```
//Register the device to Push Notifications service instance
 push.registerDeviceWithUserId("userId",new MFPPushResponseListener<String>() {
 @Override	
 public void onSuccess(String response) {
 //Handle successful device registration here
 }
 @Override	
 public void onFailure(MFPPushException ex) {
 //Handle failure in device registration here
 }
 });
 ```
 {: codeblock}
 
 
 userId is used to pass the unique user ID value for registering push notifications. Make sure you also provide the clientSecret value.
 {: tip}
 
 ## Step 4: Send a basic push notification
 
 1. In the {{site.data.keyword.Bluemix_notm}} console, go to the dashboard for your service instance.
 2. Click **Manage > Send Notifications**.
 3. Select Android Devices from the **Send To** menu.
 4. Enter your message, and click **Send**. 
 
