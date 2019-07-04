---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, setup client sdk, android application, cordova application, iOS application, web browser

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 步驟 4：設定服務用戶端 SDK
{: #push_step_3}

請確定您已[取得通知認證](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)，且已[配置推送服務實例](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2)。然後，您需要設定應用程式，以使用 Push Notifications 服務來登錄、訂閱和接收推送通知。 

若要設定服務用戶端 SDK，請根據您的應用程式類型完成下列步驟。

## 在 Android 應用程式上
{: #push_step_3_Android}

您可以啟用 Android 應用程式來接收傳送至您裝置的推送通知。Android Studio 是必備項目，而且是建置 Android 專案的建議方法。對 Android Studio 的基本瞭解十分重要。

請確定您已完成[取得通知提供者認證](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)，可以設定 FCM 專案並取得認證。

完成 [Push Notifications Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) 的步驟，以讓 Android 應用程式收到從服務傳送的推送通知。 

1. 在 Android Studio 開啟應用程式。將您透過[步驟 2：取得認證](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)建立的 `google-services.json` 檔案複製到您的 Android 應用程式模組根目錄。請注意，`google-service.json` 檔案包含已新增的套件名稱。

    ![將 json 檔案新增至應用程式的根目錄](images/FCM_7.jpg "將 json 檔案新增至應用程式的根目錄")

2. 在「將 Firebase 新增至 Android 應用程式」視窗中，按一下**繼續**，然後按一下**完成**。 
3. 建置並執行應用程式。順利建置時，會出現 `Gradle build finished` 訊息。
4. 將 Client Push SDK 包含在 Gradle。
	1. 配置 [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) 檔案。 
	2. 配置 [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) 檔案。
	3. 將 `google-services.json` 檔案新增到您的 Android 應用程式模組根目錄。
5. 起始設定 SDK。請參閱 [Initializing the Core SDK and the Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk)。
6. 建置應用程式。
7. 您可以選擇向 Push Notifications 服務登錄，方法是在應用程式上按一下「登錄裝置」按鈕，或完成[使用 Push Android SDK 向服務登錄](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice)。

您的下一步是要[傳送通知](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4)。


## 在 Cordova 應用程式上
{: #push_step_3_Cordova}

Cordova 是一個平台，可使用 JavaScript、CSS 及 HTML 來建置混合式應用程式。Push Notifications 服務支援開發 Cordova 型 iOS 及 Android 應用程式。

若要啟用 Cordova 應用程式來接收傳送至您裝置的推送通知，您需要配置 [Cordova 外掛程式 Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)。

設定 Cordova 外掛程式 Push SDK 之後，您的下一步是要[傳送通知](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4)。


## 在 iOS 應用程式上
{: #push_step_3_iOS}

若要啟用 iOS 應用程式來接收傳送至您裝置的 {{site.data.keyword.mobilepushshort}}，您需要配置 [Push Notifications 服務的 iOS SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application)。 

設定 iOS SDK 之後，您的下一步是要[傳送通知](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4)。


## 在 Web 瀏覽器上
{: #push_step_3_web}

若要啟用瀏覽器應用程式來接收推送通知，您需要配置 [Push Notifications 服務的 Web SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md)。

設定 Web SDK 之後，您的下一步是要[傳送通知](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4)。

