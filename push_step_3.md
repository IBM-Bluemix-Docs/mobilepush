---

copyright:
  years: 2015, 2017, 2019
lastupdated: "28 May 2019"

keywords: push notifications, setup client sdk, android application, cordova application, iOS application, web browser

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Step 4: Set up service client SDK's
{: #push_step_3}

Ensure that you have [obtained your notification credentials](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) and have [configured a push service instance](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2). You then need to set up the application for using Push Notifications service to register, subscribe and receive push notifications. 

To set up the service client SDK, go through the following steps based on your application type.

## On Android applications
{: #push_step_3_Android}

You can enable Android applications to receive push notifications to your devices. Android Studio is a prerequisite and is the recommended method to build Android projects. Basic knowledge of Android Studio is essential.

Ensure that you have gone through [Obtain your notification provider credentials](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) to setup the FCM project and obtain your credentials.

Complete the steps for [Push Notifications Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) to enable Android apps to receive push notifications sent from the service. 

1. Open the app in Android Studio. Copy the `google-services.json` file that you have created through [Step 2: Obtain your credentials](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) to your Android application module root directory. Note that the `google-service.json` file includes the added package names.

    ![Adding the json file to the root directory of your application](images/FCM_7.jpg)

2. In Add Firebase to your Android app window, click **Continue** and then **Finish**. 
3. Build and run your application. Upon a successfull build, the `Gradle build finished` message would appear.
4. Include the client Push SDK with Gradle.
	1. Configure your [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) file. 
	2. Configure the [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) file.
	3. Add the `google-services.json` file to your Android application module root directory.
5. Initialize the SDKs. See [Initializing the Core SDK and the Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
6. Build the application.
7. You can choose to register to the Push Notifications service by clicking the Register Device button on the application or by going through [Registering to the service using the Push Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

Your next step is to [Send a notification](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## On Cordova applications
{: #push_step_3_Cordova}

Cordova is a platform for building hybrid applications with JavaScript, CSS, and HTML. The Push Notifications service supports development of Cordova-based iOS and Android applications.

To enable Cordova applications to receive push notifications to your devices, you need to configure the [Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

After setting up the Cordova Plugin Push SDK, the next step is to [Send a notification](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## On iOS applications
{: #push_step_3_iOS}

To enable iOS applications to receive {{site.data.keyword.mobilepushshort}} to your devices, you need to configure the [iOS SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

After setting up the iOS SDK, your next step is to [Send a notification](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## On Web browsers
{: #push_step_3_web}

To enable your browser applications to receive push notifications, you need to configure the [Web SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

After setting up the Web SDK, your next step is to [Send a notification](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

