---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 基于标记的通知
{: #tag_based_notifications}
上次更新时间：2017 年 6 月 30 日
{: .last-updated}

基于标记的通知是针对预订了特定标记的所有设备的消息。基于标记的通知允许根据主题区域或主题对通知进行细分。通知接收方可以选择仅接收关于所关注主题的通知。因此，基于标记的通知提供了一种对接收方进行细分的方法。此功能可以定义标记，然后按标记发送和接收消息。消息的目标对象只包括已预订某标记的客户机应用程序实例（在移动、浏览器上或作为应用程序或扩展）。必须首先为应用程序创建标记，设置标记预订，然后再启动基于标记的通知。要使用 REST API 发送基于标记的通知，请确保发布到消息资源时提供了“tagNames”。

您可以定义标记，然后使用标记发送和接收消息。必须首先为应用程序创建标记，创建预订，然后再启动基于标记的通知。要使用 [REST API](https://mobile.{DomainName}/imfpush/){: new_window} 发送基于标记的通知，请确保发布到消息资源时提供了“tagName”。


## 管理标记
{: #manage_tags}

使用 {{site.data.keyword.mobilepushshort}} 控制台，可以创建和删除应用程序的标记，然后发起基于标记的通知。预订了标记的设备会收到基于标记的通知。


### 创建标记
{: #create_tags}

基于标记的通知是针对预订了特定标记的所有设备的消息。每个设备都可以预订任意数量的标记。 

1. 在 {{site.data.keyword.mobilepushshort}} 控制台上，选择**标记**选项卡。
1. 单击 + **创建标记**按钮。   
   1. 在**名称**字段中，输入标记的名称。例如，“coupons”。
   1. 在**描述**字段中，输入标记描述。
   1. 单击**保存**。

1. 在**代码片段**区域中，选择移动应用程序的平台。
1. 修改代码片段以处理错误，然后将每个标记的代码片段复制到移动应用程序中。

### 删除标记
{: #delete_tags}

1. 从**标记**选项卡，选择要删除的标记，并单击**删除**图标。
1. 单击**确定**。

删除标记时，与该标记关联的信息（包括其订户和设备）都会一并删除。不需要自动取消预订，因为该标记不存在。客户端不需要任何进一步操作。

### 编辑标记描述
{: #edit_tags}

1. 在**标记**选项卡中，选择要编辑的标记。
1. 单击**编辑**图标。
1. 编辑标记描述，然后单击**保存**按钮。

## 获取标记
{: #get_tags}

不同于发送给所有应用程序的一般性广播，通过标记，可以根据用户的兴趣发送有针对性的通知。您可以使用 {{site.data.keyword.mobilepushshort}} 控制台上的“标记”选项卡或使用 REST API 来创建和管理标记。您可以使用代码片段来管理和查询移动应用程序的标记预订。可以使用代码片段来获取预订，预订标记，取消预订标记，或者获取可用标记的列表。将这些代码片段复制到移动应用程序中。


- 对于 Android，请参阅 [Push Notification get tags on Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app) 中的 `getTags` API 和 `getSubscriptions` API。

- 对于 Cordova，请参阅 [Push Notifications get tags on Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags) 中的 `retrieveAvailableTags()` API 和 `retrieveSubscriptions()` API。

- 对于 iOS，请参阅 [Push Notifications get tags on Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags) 中的 `retrieveAvailableTagsWithCompletionHandler` API。

- 对于 Web 浏览器，请参阅 [Push Notifications get tag on web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags) 中的 `retrieveAvailableTags()` API。


## 预订标记
{: #Subscribe_tags}

使用以下 API 可允许设备检索标记，预订标记，检索预订以及取消预订标记。

- 对于 Android，请使用 `getTags`、`subscribe`、`getSubscriptions` 和 `unsubscribeFromTags` API。请参阅 [Push Notifications subscribe tags for Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags)。

- 对于 Cordova，请使用 `retrieveAvailableTags()`、`subscribe()`、`retrieveSubscriptions()` 和 `unsubscribe()` API。请参阅 [Push Notifications subscribe tags for Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags)。

- 对于 iOS，请使用 `retrieveAvailableTagsWithCompletionHandler`、`subscribeToTags`、`retrieveSubscriptionsWithCompletionHandler` 和 `unsubscribeFromTags` API。请参阅 [Push Notifications subscribe tags for Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags)。

- 对于 Web 浏览器，请使用 `retrieveAvailableTags()`、`subscribe()`、`retrieveSubscriptions()` 和 `unSubscribe()` API。请参阅 [Push Notifications subscribe tags for web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags)。

## 使用基于标记的通知
{: #using_tags}

基于标记的通知是针对预订了特定标记的所有设备的消息。每个设备都可以预订任意数量的标记。本主题描述了如何发送基于标记的通知。预订通过 {{site.data.keyword.mobilepushshort}} 服务 Bluemix 实例进行维护。删除标记时，与该标记关联的所有信息（包括其订户和设备）都会一并删除。无需对此标记自动取消预订，因为此标记不再存在，因此也不需要从客户机端执行进一步的操作。

在**标记**屏幕上创建标记。有关如何创建标记的信息，请参阅[创建标记](t_manage_tags.html)。

1. 在 **Push Notification** 控制台中，选择**发送通知**。
1. 在**发送到**下拉列表中，选择**按标记列出设备**选项。
1. 搜索要使用的标记并将其选中。![通知屏幕](images/tag_notification.jpg)
1. 在**消息文本**字段中，输入将作为通知发送给订阅受众的文本。
1. 单击**发送**。
