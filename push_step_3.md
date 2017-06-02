---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Set up service client SDK's
{: #push_step_3}
Last updated: 22 May 2017
{: .last-updated}

After you have [obtained your notification credentials](push_step_1.html) and have [configured a push service instance](push_step_2.html), you need to set up the application for using Push Notifications service to register, subscribe and receive push notifications. 


## On Android applications
{: #push_step_3_Android}

You can enable Android applications to receive push notifications to your devices. Android Studio is a prerequisite and is the recommended method to build Android projects. Basic knowledge of Android Studio is essential.

Ensure that you have gone through [Obtain your notification provider credentials](push_step_1.html) to setup the FCM project and obtain your credentials.

Complete the steps for [Push Notifications Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) to enable Android apps to receive push notifications sent from the service. 

Complete the following steps using the Firebase Cloud Messaging (FCM) console.

1. In the Firebase console, click the **Project Settings** icon.
    ![Firebase Project Settings](images/FCM_4.jpg)

3. Select **ADD APP** or **Add Firebase to your Android app** icon from the General tab on the Your apps pane.
    ![Adding Firebase to Android](images/FCM_5.jpg)

4. In Add Firebase to your Android app window, add **com.ibm.mobilefirstplatform.clientsdk.android.push** as the Package Name. The App nickname field is optional. Click **REGISTER APP**. 
    ![Adding Firebase to your Android window](images/FCM_1.jpg)

5. Include the package name of your application, by entering the package name in Add Firebase to your Android app window. The App nickname field is optional. Click **ADD APP**. 

	![Adding the package name of your application](images/FCM_2.jpg)

6. The `google-services.json` file is generated. 
7. Open the app in Android Studio. Copy the `google-services.json` file to your Android application module root directory. Note that the `google-service.json` file includes the added package names.

    ![Adding the json file to the root directory of your application](images/FCM_7.jpg)

5. In Add Firebase to your Android app window, click **Continue** and then **Finish**. 
6. Build and run your application. Upon a successfull build, the `Gradle build finished` message would appear.
7. Include the client Push SDK with Gradle.
	1. Configure your [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) file. 
	1. Configure the [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) file.
	1. Add the `google-services.json` file to your Android application module root directory.
9. Initialize the SDKs. See [Initializing the Core SDK and the Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
10. Build the application.
11. You can choose to register to the Push Notifications service by clicking the Register Device button on the application or by going through [Registering to the service using the Push Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

Your next step is to [Send a Push Notification](push_step_4.html).


## On Cordova applications
{: #push_step_3_Cordova}

Cordova is a platform for building hybrid applications with JavaScript, CSS, and HTML. The Push Notifications service supports development of Cordova-based iOS and Android applications.

To enable Cordova applications to receive push notifications to your devices, you need to configure the [Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

After setting up the Cordova Plugin Push SDK, the next step is to [Send a Push Notification](push_step_4.html).


## On iOS applications
{: #push_step_3_iOS}

To enable iOS applications to receive {{site.data.keyword.mobilepushshort}} to your devices, you need to configure the [iOS SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

After setting up the iOS SDK, your next step is to [Send a Push Notification](push_step_4.html).


## On Web browsers
{: #push_step_3_web}

To enable your browser applications to receive push notifications, you need to configure the [Web SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

After setting up the Web SDK, your next step is to [Send a Push Notification](push_step_4.html).