---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, user-based, register device with user ID, synchronize user login and logout

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 基于用户的通知
{: #user_based_notifications}

基于用户标识的 {{site.data.keyword.mobilepushshort}} 针对具有定制消息的移动应用程序用户。使用基于用户的通知，您可以根据首选项选择通知特定个人。

## 使用用户标识注册设备
{: #register_device_wh_userid}

要按用户标识向目标推送通知，确保您在设置了用户标识字段的情况下注册设备。     

用户标识可以是应用程序提供给设备注册 API 的任何字符串。通常，移动应用程序首先会运行认证周期，在这期间会针对认证服务（如 {{site.data.keyword.amafull}}）认证移动应用程序用户。在成功认证之后，已认证的用户标识会传递至推送设备注册 API。 

要注册基于用户标识的通知，请完成以下步骤：

- [注册 Android 应用程序](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [注册 iOS 应用程序](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [注册 Cordova 应用程序](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [注册 Web 应用程序](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## 使用基于用户标记的通知 
{: #using_userid}

基于用户标识的通知是针对特定用户的通知消息。一个用户可注册多个设备。以下步骤描述了如何发送基于用户标识的通知。

1. 在 **Push Notification** 控制台中，选择**发送通知**选项。
2. 在**发送至**选项列表中，选择**用户标识**。
3. 在**用户标识**字段中，搜索要使用的用户标识，并单击 **+添加**。![通知屏幕](images/user_notification.jpg "显示“用户标识”字段的“添加”按钮的 Push Notification 控制台")
4. 在**消息**字段中，输入要在通知中发送的文本。
5. 单击**发送**。


## 同步用户登录和注销 
{: #sync_login_logout}

您可以选择仅在用户登录时发送通知。 

例如，假设设备由工作团队的成员共享，而您需要寻址到特定用户。在此用例中，将会有用户登录和注销序列。此认证机制允许应用程序跟踪应用程序当前用户的身份。这样确保针对特定用户的通知始终由该用户接收。成功登录之后，调用传递登录用户的用户标识的设备注册 API。同样，在注销之前，调用设备`注销` API。使用登录和注销对这些 Push API 进行序列化可确保针对特定用户的通知仅会发送到该用户。
