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

# 入门教程
{: #getting-started-with-push}

在此 {{site.data.keyword.mobilepushfull}} 入门教程中，我们将完成使 Android 应用程序能接收推送通知并向设备发送基本推送通知的过程。
{:shortdesc}

<div id="prerequisites"></div>

## 开始之前
{: #prereqs}

您将需要 [IBM Cloud 帐户](https://console.bluemix.net/registration/)、{{site.data.keyword.mobilepushshort}} 服务实例以及下列工具和需求：

  * Android API 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android helloPush 样本应用程序](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * 使用 Studio 或 Gradle 安装的 [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} 和 [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} SDK

## 第 1 步：为 Android 设备配置 {{site.data.keyword.mobilepushshort}} 实例

1. 复制样本 `AndroidManifest.xml` 文件中的程序包名。

2. 创建 FCM 应用程序，并添加 Android 应用程序的程序包名：
  1. 在 [Firebase 控制台](https://console.firebase.google.com){: new_window}中，单击**添加项目**，提供项目名称，然后单击**创建项目**。
  2. 单击**将 Firebase 添加到您的 Android 应用**，输入应用程序的程序包名，然后单击**注册应用程序**。可以通过单击**继续 > 完成**跳过接下来的两个提示。 

3. 将 FCM 凭证添加到 {{site.data.keyword.mobilepushshort}} 实例：
  1. 在 Firebase 控制台中，转至**设置 > 项目设置 > 云消息传递**，并复制“服务器密钥”和“发送方标识”。
  2. 在 {{site.data.keyword.Bluemix_notm}} 控制台中，打开服务实例的仪表板。
  3. 单击**管理 > 配置**。
  4. 在 **GCM/FCM 推送凭证**字段中，输入“发送方标识”和“服务器密钥”。

## 第 2 步：使 Android 应用程序能发送推送通知

1. 配置项目级别 `build.gradle` 和模块级别 `build.gradle` 文件：

  * 将 SDK 依赖关系添加到项目级别 `build.gradle` 文件：
  
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

  * 将以下依赖关系添加到模块级别 `build.gradle` 文件：
  
  ```
dependencies {
classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * 将 Google Play 服务依赖关系添加到模块级别 `build.gradle` 文件末尾的 dependencies 后面：
  
  ```
apply plugin: 'com.google.gms.google-services'
	```
  {: codeblock}
  
  * 将以下许可权添加到应用程序的 `AndroidManifest.xml` 文件：
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.USE_CREDENTIALS" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
```
  {: codeblock}
  
  * 添加活动的通知意向设置。 
  
  此设置会在用户单击通知区域中收到的通知时启动应用程序。将 `<yourAndroidPackageName>` 替换为应用程序中使用的应用程序的程序包名。
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * 针对 `RECEIVE` 和 `REGISTRATION` 事件通知，更新 FCM 意向服务和意向过滤器：
  
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
  
2. 在 Android Studio 中打开应用程序，然后将 `google-services.json` 文件添加到应用程序模块根目录。

3. 初始化核心 SDK 和推送 SDK。 

在 Android 应用程序中，通常会将初始化代码放置在主活动的 onCreate() 方法中。

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... 其中，`<bluemixRegionSuffix>` 是托管应用程序的位置。可以使用以下任一值：


  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID 是推送应用程序 GUID 值，clientSecret 是推送客户机私钥值。 

## 第 3 步：向 {{site.data.keyword.mobilepushshort}} 实例注册 Android 设备

1. 运行应用程序。

2. 使用 MFPPush.register() API 注册设备以启用基于用户的通知。

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
 
 
 userId 用于传递注册推送通知所需的唯一用户标识值。确保同时提供 clientSecret 值。
 {: tip}
 
 ## 第 4 步：发送基本推送通知
 
 1. 在 {{site.data.keyword.Bluemix_notm}} 控制台中，转至服务实例的仪表板。
 2. 单击**管理 > 发送通知**。
 3. 从**发送至**菜单中选择 Android 设备。
 4. 输入您的消息，然后单击**发送**。 
 
