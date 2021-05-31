---

copyright:
   years: 2020
lastupdated: "2020-09-15"

keywords: push notifications, push notification, android tutorial

subcollection: mobilepush

content-type: tutorial
services: mobilepush
account-plan: paid 
completion-time: 30m

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:external: target="_blank" .external}
{:important: .important}
{:step: data-tutorial-type='step'}

# Send Push Notifications to Android devices
{: #push-tutorial-android}
{: toc-content-type="tutorial"} 
{: toc-services="mobilepush"} 
{: toc-completion-time="30m"} 

In this tutorial, you learn how to create a native Android application with high-value mobile service like {{site.data.keyword.mobilepushshort}} on {{site.data.keyword.cloud_notm}}.
{: shortdesc}

This tutorial walks you through the creation of a mobile starter application, adding a mobile service, setting up client SDK, importing the code to Android Studio and then further enhancing the application.

## Objectives
{: #push-tutorial-android-objectives}

- Create a mobile app with {{site.data.keyword.mobilepushshort}} service.
- Obtain FCM credentials.
- Download the code and complete required setup.
- Configure, send, and monitor {{site.data.keyword.mobilepushshort}}.

## Before you begin
{: #push-tutorial-android-beforeubegin}

- [Android Studio](https://developer.android.com/studio/index.html) for importing and enhancing your code.
- Google account to log in to Firebase console for Sender ID and Server API Key.
- {{site.data.keyword.cloud_notm}} account. If you do not have an {{site.data.keyword.cloud_notm}} account, create an [IBM Cloud account](https://cloud.ibm.com/).

## Create an {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service instance
{: #push-tutorial-create-push-service-instance}
{: step}
1. Log in to your [IBM Cloud account](https://cloud.ibm.com/).
1. In the [IBM Cloud catalog](https://cloud.ibm.com/catalog#services), click **Mobile** > **Push Notifications**.
1. **Select a Region** from the list of supported region and **Select a pricing plan**.
1. Provide a **Service name**. 
1. `Optional`: Select a resource group.

   Consider how you want the resources that are organized in your account. The resource group that you selected cannot be changed after the service instance is created. 
   {: note}

1. Click **Create**. 

In the next step, you will obtain Firebase Cloud Messaging (FCM) credentials.

## Obtain FCM credentials 
{: #push-tutorial-obtain-fcm-credentials}
{: step}
Firebase Cloud Messaging (FCM) is the gateway that is used to deliver push notifications to Android devices. To set up the {{site.data.keyword.mobilepushshort}} service on the console, you need to get your FCM credentials (Sender ID and API key). 

The API key is stored securely and used by the {{site.data.keyword.mobilepushshort}} service to connect to the FCM server and the sender ID (project number) is used by the Android SDK and the JS SDK for Google Chrome and Mozilla Firefox on the client side. 

1. Go to the [Firebase Console](https://console.firebase.google.com/?pli=1){: external}. A Google user account is required. 
1. Click **Create a project**. If you are already having a project, then click **Add Project**.
1. In the **Create a project** window, provide a project name, and accept the terms and enable or disable Google analytics (*optional*) by selecting the toggle switch and click **Continue**.
1. If Google analytics is enabled, then in the **Configure Google Analytics** window, choose the **Analytics location**, and accept the terms. Click **Create Project**.
1. Click **Continue** when the new project is ready.
1. In the navigation pane, select the settings icon next to the *Project Overview* and select **Settings** > **Project settings**.
1. Click **Cloud Messaging** tab to view your project credentials - **Server Key** and **Sender ID**.

   ![Obtaining credentials for FCM](images/FCM_settings_2.jpg "Settings page with the Cloud messaging tab-selected showing project credentials")

You would also need to generate the `google-services.json` file. Complete the following steps:

1. In the Firebase console Project overview section, under *Get started by adding Firebase to your app* section click the **Android** icon.

   ![Firebase Project overview](images/FCM_settings_6.jpg "Firebase Project overview consoles open")

1. In *Add Firebase to your Android app* window, first add **com.ibm.mobilefirstplatform.clientsdk.android.push** as the Package Name. The App nickname field is optional. Click **Register APP**. 

   ![Adding Firebase to your Android window](images/FCM_1.jpg "Add Firebase to your Android app screen on the Enter app details tab with the package and app name fields")

1. Now, include the package name of your application, by entering the package name in Add Firebase to your Android app window. The App nickname field is optional. Click **Register APP**. See the following example:

   ![Adding the package name of your application](images/FCM_settings_4.jpg "Add Firebase to your Android app screen on the Register app tab with the package and app name fields")

   If you don't have any apps to start with, download the Android sample app [here](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush/).
   {: note}

1. The `google-services.json` file is generated.
1. Download the latest config file `google-services.json` under **Your apps**.

Once you have obtained your FCM credentials and have generated the `google-services.json` file, the next step is to Configure a service instance.

## Configure the {{site.data.keyword.mobilepushshort}} service instance 
{: #push-tutorial-configure-service-instance}
{: step}
1. In the {{site.data.keyword.mobilepushshort}} service console, click **Configure Service** on the left navigation menu.
1. In the Android tile, click **Configure**. 
1. In the side panel, update the FCM Push Credentials with the **Sender ID/Project number** and **Server Key** or **Legacy Server Key**. You can get these details from your FCM **Project Settings &gt; Cloud Messaging** section.

   ![Configure Android apps](images/mpush-android-config.png "Graphic outlining the configuring push service instance for Android")

1. Click **Save**. The {{site.data.keyword.mobilepushfull}} service is now configured.

After you have setup the service, you need to Set up the Push service client SDKs.

## Set up {{site.data.keyword.mobilepushshort}} Android SDK
{: #push-tutorial-setup-push-android-sdks}
{: step}
The {{site.data.keyword.mobilepushshort}} Android SDK enables Android apps to receive the sent push notifications. In this section, you will complete the steps to install {{site.data.keyword.mobilepushshort}} Android SDK, initialize the SDK, and register for notifications for your Android app.

### Installation of {{site.data.keyword.mobilepushshort}} Android SDK
{: #push-tutorial-setup-push-android-sdks-installation}
1. Integrate the {{site.data.keyword.mobilepushshort}} Android Client SDK package through Gradle from this [location]().

#### Initialize the {{site.data.keyword.mobilepushshort}} Android SDK
{: #push-tutorial-setup-push-android-sdks-initialize}
In the initialization process, you will include client Push SDK with Gradle and include core SDK and Push SDK.

##### Include client Push SDK
1. Add the following dependencies to your Project level `build.gradle` file.
		
   ```
	buildscript {
		repositories {
			jcenter()
			maven { url 'https://maven.google.com' }
            google()
		}
		dependencies {
			classpath 'com.android.tools.build:gradle:3.4.1'
            classpath 'com.google.gms:google-services:4.3.2'
		}
	}

	allprojects {
		repositories {
			jcenter()
			maven { url 'https://maven.google.com' }
            google()
		}
	}
  	```
   {: codeblock}

1. Add {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} Android SDK dependency to your Module level `build.gradle` file.
	
	```
	dependencies {
    	........
		implementation 'com.google.firebase:firebase-messaging:20.0.0'
        implementation 'com.ibm.mobilefirstplatform.clientsdk.android:core:3.+'
		.......
	}
	```
   {: codeblock}

1. Add the `Google Play services` dependency to your Module level `build.gradle` file at the end, after the `dependencies{.....}`:

	```
	apply plugin: 'com.google.gms.google-services'
	```
   {: codeblock}

1. Configure the `AndroidManifest.xml` file. Refer the [example here](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush/blob/master/helloPush/app/src/main/AndroidManifest.xml). Add the following permissions inside application's `AndroidManifest.xml` file. 

	 ```
	 <uses-permission android:name="android.permission.INTERNET"/>
	 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
	 <uses-permission android:name="android.permission.WAKE_LOCK" />
	 ```
   {: codeblock}

1. Add the notification intent settings for the activity. This setting starts the application when the user clicks the received notification from the notification area.

	```
	 <intent-filter>
     <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
     <category  android:name="android.intent.category.DEFAULT"/>
	 	</intent-filter>
	```
   {: codeblock}

   Replace `Your_Android_Package_Name` in the previous action with the application package name used in your application.
   {: note}

1. Update the `Firebase Cloud Messaging (FCM)` or `Google Cloud Messaging (GCM)` intent service and intent filters for the `RECEIVE` and `REGISTRATION` event notifications:

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

1. Push Notifications service supports retrieval of individual notifications from the notification tray. For notifications accessed from the notification tray, you are provided with a handle only to the notification that is being clicked. All notifications are displayed when the application is opened normally. Update your `AndroidManifest.xml` file with the following snippet to use this functionality:
	
	```
	<activity android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushNotificationHandler"
	   android:theme="@android:style/Theme.NoDisplay"/>
	```
   {: codeblock}

1. Add the `google-services.json` in Android application module root directory. The `google-service.json` file includes the added package names.

   ![Adding the JSON file to the root directory of your application](images/FCM_7.png "Adding the JSON file to the root directory of your application")
 
##### Include core SDK and Push SDK

A common place to put the initialization code is the `onCreate()` method of the `main activity` in your Android application: 

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "ibmCloudRegionSuffix");
//Initialize client Push SDK

MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}

Where `ibmCloudRegionSuffix` specifies the location where the app is hosted. You can use any of the following values:

- `BMSClient.REGION_US_SOUTH`
- `BMSClient.REGION_UK`
- `BMSClient.REGION_SYDNEY`
- `BMSClient.REGION_GERMANY`
- `BMSClient.REGION_US_EAST`
- `BMSClient.REGION_TOKYO`

![Editing Main activity file](images/mp-gradle-main-activity.png "Editing the main activity file with IBM cloud application region")

The `appGUID` is the push app GUID value, while `clientSecret` is the push client secret value.

Initialize Push SDK by copying APP GUID and CLIENT SECRET from **Service credentials** page for the Push Notification service on IBM Cloud.

![App GUID and Client secret](images/mp-appguid.png "Editing the main activity file with APP GUID and client secret")

Paste the APP GUID and CLIENT SECRET under your app’s Main Activity file.

![Editing Main activity file](images/mp-gradle-main-activity1.png "Editing the main activity file with APP GUID and client secret")

#### Register device for notifications
{: #push-tutorial-setup-register-for-notifications}

Use the `MFPPush.register()` API to register the device with Push Notifications service. 

```
//Register Android devices
push.registerDevice(new MFPPushResponseListener<String>() {
	
	@Override
	public void onSuccess(String response) {
	   //handle successful device registration here
	}

	@Override
	public void onFailure(MFPPushException ex) {
	   //handle failure in device registration here
	}
});
```
{: codeblock}

The userId is used to pass the unique userId value for registering for Push Notifications. If the userId is provided, ensure that the the client secret value is also provided.

1. If you have an android device, connect to your mac/windows and select the device in the Android studio.
1. Click the run button. If you don't have an android device, [create an emulator](https://developer.android.com/studio/run/emulator) with API 28 or higher.
1. Run the app and click Register device button that appears on your app for the push notifications.

#### Receiving notifications
{: #push-tutorial-setup-receive-notifications}

To register the `notificationListener` object with Push Notifications service, use the `MFPPush.listen()` method. This method is typically called from the `onResume()` and `onPause()` methods of the activity that is handling push notifications.

```
//Handles the notification when it arrives
MFPPushNotificationListener notificationListener = new MFPPushNotificationListener() {
	
	@Override
	public void onReceive (final MFPSimplePushNotification message){
      // Handle Push Notification
    }	
};

@Override
protected void onResume(){
    super.onResume();
    if(push != null) {
      push.listen(notificationListener);
    }
}

@Override
protected void onPause() {
	super.onPause();
	if (push != null) {
		push.hold();
	}
}
```
{: codeblock}

Your next step is to Send a notification.

### On Cordova applications
{: #push-tutorial-android-Cordova}

Cordova is a platform for building hybrid applications with JavaScript, CSS, and HTML. The {{site.data.keyword.mobilepushshort}} service supports development of Cordova-based Android applications.

To enable Cordova applications to receive, push notifications to your devices, you need to configure the [Cordova plug-in Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/master#ios-app){: external}.

After setting up the Cordova plug-in Push SDK, the next step is to Send a notification.

## Send a notification 
{: #push-tutorial-send-a-notification}
{: step}
After your applications are developed, you can send basic push notifications.
1. In the {{site.data.keyword.mobilepushshort}} service console, click **Notifications** on the left navigation menu.
1. Click **Create**, and compose a message.
   - Compose a new notification by providing the following information: **Notification text**, **Notification title** (optional), **Additional payload** (optional).
   - Select the **Target audience** by one of the following targets:
      - **Platforms** - Options are: **Android**, **iOS**, **Web Notifications**, **Chrome Apps and Extensions**, **Chrome Browser**, **Firefox**, **Safari**, and **All Devices**.
      - **Tags** - Enter the Tag, topic name or create a tag.
      - **Devices/user IDs** - Select either **Device ID** or **User ID** and enter the device/user ID detail for the selection.

   When you select the **All Devices** option, all devices that are subscribed to {{site.data.keyword.mobilepushshort}} will receive notifications.
   {: note}

   - Optionally for rich media notifications use **Advanced settings**. Select the **Priority** (valid options are: Default, Max, Min, Low, High) and select the type of notification to be sent (**Default** or **Silent**).
   - Quickly review your selection in the **Review** section.

1. Click **Send**.
1. Verify that your devices or browser has received the notification.

The following screen capture shows an alert box handling a push notification in the foreground on an Android device.

![Foreground push notification on Android](images/Android_Screenshot.jpg "Alert box with test notification")

The following screen capture shows a push notification in the background for Android.

![Background push notification on Android](images/background.jpg "Push notification on an Android device")

Optionally, You can further customize the Push Notifications settings for sending notifications to Android devices. For more information, see [here](/docs/mobilepush?topic=mobilepush-push_step_4#push_step_4_Android).
{: note}

