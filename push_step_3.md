---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-04"

keywords: push notifications, setup client sdk, android application, cordova application, iOS application, web browser

subcollection: mobile-pushnotification

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:java: .ph data-hd-programlang='java'}
{:ruby: .ph data-hd-programlang='ruby'}
{:c#: .ph data-hd-programlang='c#'}
{:objectc: .ph data-hd-programlang='Objective C'}
{:python: .ph data-hd-programlang='python'}
{:javascript: .ph data-hd-programlang='javascript'}
{:php: .ph data-hd-programlang='PHP'}
{:swift: .ph data-hd-programlang='swift'}
{:reactnative: .ph data-hd-programlang='React Native'}
{:csharp: .ph data-hd-programlang='csharp'}
{:ios: .ph data-hd-programlang='iOS'}
{:android: .ph data-hd-programlang='Android'}
{:cordova: .ph data-hd-programlang='Cordova'}
{:xml: .ph data-hd-programlang='xml'}

# Step 4: Set up service client SDK's
{: #push_step_3}

Ensure that you have [obtained your notification credentials](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) and have [configured a push service instance](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2). You then need to set up the application for using {{site.data.keyword.mobilepushshort}} service to register, subscribe, and receive push notifications. 

To set up the service client SDK, go through the following steps based on your application type.

## On Android applications
{: #push_step_3_Android}

You can enable Android applications to receive push notifications to your devices. Android Studio is a prerequisite and is the recommended method to build Android projects. Basic knowledge of Android Studio is essential.

Ensure that you have gone through [Obtain your notification provider credentials](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) to set up the FCM project and obtain your credentials.

Complete the steps for [{{site.data.keyword.mobilepushshort}} Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) to enable Android apps to receive push notifications sent from the service. 

1. Open the app in Android Studio. Copy the `google-services.json` file that you have created through [Step 2: Obtain your credentials](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) to your Android application module root directory. Note that the `google-service.json` file includes the added package names.

   ![Adding the JSON file to the root directory of your application](images/FCM_7.jpg "Adding the JSON file to the root directory of your application")

1. In Add Firebase to your Android app window, click **Continue** and then **Finish**. 
1. Build and run your application. Upon a successful build, the `Gradle build finished` message would appear.
1. Include the client Push SDK with Gradle.
   1. Configure your [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) file. 
   2. Configure the [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) file.
   3. Add the `google-services.json` file to your Android application module root directory.
1. Initialize the SDKs. See [Initializing the Core SDK and the Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
1. Build the application.
1. You can choose to register to the {{site.data.keyword.mobilepushshort}} service by clicking the Register Device button on the application or by going through [Registering to the service by using the Push Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

Your next step is to [Send a notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

## On Cordova applications
{: #push_step_3_Cordova}

Cordova is a platform for building hybrid applications with JavaScript, CSS, and HTML. The {{site.data.keyword.mobilepushshort}} service supports development of Cordova-based iOS and Android applications.

To enable Cordova applications to receive, push notifications to your devices, you need to configure the [Cordova plug-in Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

After setting up the Cordova plug-in Push SDK, the next step is to [Send a notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

## On iOS applications
{: #push_step_3_iOS}

To enable iOS applications to receive {{site.data.keyword.mobilepushshort}} to your devices, you need to configure the [iOS SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

After setting up the iOS SDK, your next step is to [Send a notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

## On Web browsers
{: #push_step_3_web}

To enable your browser applications to receive, push notifications, you need to configure the [Web SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

After setting up the Web SDK, your next step is to [Send a notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).
