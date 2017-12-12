---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 開始使用指導教學
{: #getting-started-with-push}

在此 {{site.data.keyword.mobilepushfull}} 開始使用指導教學中，我們會完成讓 Android 應用程式能接收推送通知以及傳送基本推送通知給裝置的程序。
{:shortdesc}

<div id="prerequisites"></div>

## 開始之前
{: #prereqs}

您將需要 [IBM Cloud 帳戶](https://console.bluemix.net/registration/)、{{site.data.keyword.mobilepushshort}} 服務的實例，以及下列工具和需求：

  * Android API 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android helloPush 範例應用程式](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * 已使用 Android Studio 或 Gradle 安裝 [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} 和
  [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} SDK

## 步驟 1：針對 Android 裝置配置 {{site.data.keyword.mobilepushshort}} 實例

1. 從範例 `AndroidManifest.xml` 檔案複製套件名稱。

2. 建立 FCM 應用程式並新增 Android 應用程式的套件名稱：
  1. 在 [Firebase 主控台](https://console.firebase.google.com){: new_window}中，按一下**新增專案**、提供專案名稱，然後按一下**建立專案**。
  2. 按一下**將 Firebase 加入您的 Android 應用程式**、輸入應用程式套件名稱，然後按一下**註冊應用程式**。您可以按一下**繼續 > 完成**，跳過接下來的兩個提示。 

3. 將 FCM 認證新增至您的 {{site.data.keyword.mobilepushshort}} 實例：
  1. 在 Firebase 主控台中，移至**設定 > 專案設定 > Cloud Messaging**，然後複製「伺服器金鑰」和「寄件者 ID」。
  2. 在 {{site.data.keyword.Bluemix_notm}} 主控台中，開啟服務實例的儀表板。
  3. 按一下**管理 > 配置**。
  4. 將「寄件者 ID」和「伺服器金鑰」輸入到 **GCM/FCM 推送認證**欄位。

## 步驟 2：讓您的 Android 應用程式能傳送推送通知

1. 配置專案層次的 `build.gradle` 及模組層次的 `build.gradle` 檔案：

  * 將 SDK 相依關係新增至專案層次的 `build.gradle` 檔案：
  
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

  * 將下列相依關係新增至模組層次的 `build.gradle` 檔案：
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * 將 Google Play 服務相依關係新增至模組層次的 `build.gradle` 檔案的結尾，相依關係之後：
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * 將下列相依關係新增至您應用程式的 `AndroidManifest.xml` 檔案：
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
  <uses-permission android:name="android.permission.GET_ACCOUNTS" />
  <uses-permission android:name="android.permission.USE_CREDENTIALS" />
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  ```
  {: codeblock}
  
  * 新增活動的通知目的設定。 
  
  此設定會在使用者按一下通知區域中的接收通知時啟動應用程式。將
  `<yourAndroidPackageName>` 取代為您應用程式中使用的應用程式套件名稱。
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * 更新 `RECEIVE` 及 `REGISTRATION` 事件通知的 FCM 目的服務和目的過濾器。
  
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
  
2. 在 Android Studio 開啟應用程式，然後將 `google-services.json` 檔案新增至應用程式模組根目錄。

3. 起始設定核心 SDK 及 Push SDK。 

放置起始設定碼的一般位置位於 Android 應用程式之主要活動的 onCreate() 方法：

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... 其中 `<bluemixRegionSuffix>` 是管理應用程式的位置。您可以使用下列任何值：

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID 是推送應用程式 GUID 值，clientSecret 是推送用戶端密碼值。 

## 步驟 3：向 {{site.data.keyword.mobilepushshort}} 實例登錄 Android 裝置

1. 執行您的應用程式。

2. 使用 MFPPush.register() API 登錄您的裝置，以便啟用以使用者為基礎的通知。

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
 
 
 userId 用來傳遞唯一使用者 ID 值，以便登錄推送通知。請確定您也提供 clientSecret 值。
 {: tip}
 
 ## 步驟 4：傳送基本推送通知
 
 1. 在 {{site.data.keyword.Bluemix_notm}} 主控台中，移至服務實例的儀表板。
 2. 按一下**管理 > 傳送通知**。
 3. 從**傳送至**功能表選取 Android 裝置。
 4. 輸入您的訊息，然後按一下**傳送**。 
 
