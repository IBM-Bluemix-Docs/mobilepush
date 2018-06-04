---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 第 4 步：设置服务客户机 SDK
{: #push_step_3}
上次更新时间：2017 年 6 月 27 日
{: .last-updated}

确保已[获取通知凭证](push_step_1.html)并已[配置 Push 服务实例](push_step_2.html)。然后，需要设置应用程序，以使用 Push Notifications 服务来注册、预订和接收推送通知。 

要设置服务客户机 SDK，请根据应用程序类型完成以下步骤。

## 在 Android 应用程序上
{: #push_step_3_Android}

您可以让 Android 应用程序具有向您的设备接收推送通知的能力。Android Studio 是必备软件，也是构建 Android 项目的建议方法。必须具有 Android Studio 的基本知识。

确保您已经完成[获取通知提供程序凭证](push_step_1.html)的操作来设置 FCM 项目并获取凭证。

完成 [Push Notifications Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) 的步骤，使 Android 应用程序能接收从该服务发送的推送通知。 

1. 在 Android Studio 中打开应用程序。将通过[第 2 步：获取凭证](push_step_1.html)创建的 `google-services.json` 文件复制到 Android 应用程序模块根目录。请注意，`google-service.json` 文件包括添加的程序包名。

    ![将 JSON 文件添加到应用程序的根目录](images/FCM_7.jpg)

2. 在“将 Firebase 添加到您的 Android 应用”窗口中，单击**继续**然后单击**完成**。 
3. 构建并运行应用程序。成功构建后，将显示 `Gradle build finished` 消息。
4. 使用 Gradle 包含客户机推送 SDK。
	1. 配置 [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) 文件。 
	2. 配置 [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) 文件。
	3. 将 `google-services.json` 文件添加到 Android 应用程序模块根目录。
5. 初始化 SDK。请参阅[初始化核心 SDK 和推送 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk)。
6. 构建应用程序。
7. 可以选择通过以下任一方法注册 Push Notifications 服务：单击应用程序上的“注册设备”按钮，或完成[使用推送 Android SDK 注册服务](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice)的操作。

下一步是[发送通知](push_step_4.html)。


## 在 Cordova 应用程序上
{: #push_step_3_Cordova}

Cordova 是一种平台，用于通过 JavaScript、CSS 和 HTML 构建混合应用程序。Push Notifications 服务支持开发基于 Cordova 的 iOS 和 Android 应用程序。

要使 Cordova 应用程序能接收向设备发送的推送通知，需要配置 [Cordova 插件推送 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)。

设置 Cordova 插件推送 SDK 后，下一步是[发送通知](push_step_4.html)。


## 在 iOS 应用程序上
{: #push_step_3_iOS}

要使 iOS 应用程序能接收向设备发送的 {{site.data.keyword.mobilepushshort}}，需要配置 [Push Notifications 服务的 iOS SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application)。 

设置 iOS SDK 后，下一步是[发送通知](push_step_4.html)。


## 在 Web 浏览器上
{: #push_step_3_web}

要使浏览器应用程序能接收推送通知，需要配置 [Push Notifications 服务的 Web SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md)。

设置 Web SDK 后，下一步是[发送通知](push_step_4.html)。
