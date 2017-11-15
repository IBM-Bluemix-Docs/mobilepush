---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 交互式和静默通知  
{: #interactive-notifications}
上次更新时间：2017 年 5 月 22 日
{: .last-updated}

使用交互式通知，用户可以在不打开应用程序的情况下响应通知。当交互式通知到达时，设备会显示通知消息及相应的操作按钮。 

**注：**版本低于 8 的 iOS 设备上不支持交互式通知。 

## 发送交互式通知
{: #send_interactive_notifications}

使用 Push Notifications 控制台或使用 [REST API 文档](push_restapi.html)可发送交互式通知。

从 {{site.data.keyword.mobilepushshort}} 控制台： 

1. 在“通知”选项卡上，单击**发送通知**。 
2. 选择通知收件人，并单击**下一步**。 
3. 在编写通知页面上，可以通过将“类型”设置为“缺省值”或“混合”并在“高级选项”选项卡下指定“类别”值来发送交互式推送。 

## 处理交互式通知 
{: #handle_interactive_notifications}

- 对于 iOS，完成[启用和处理 Swift 应用程序上的交互式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications)的操作。
- 对于 Cordova，完成[启用和处理 Cordova 应用程序上的交互式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications)的操作。
- 对于 Android，完成[启用和处理 Android 应用程序上的交互式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications)的操作。


## 处理针对 iOS 的静默通知
{: #send_silent_notifications_for_ios}

静默通知不会显示在设备屏幕上，而是会由后台的应用程序接收。有关更多信息，请参阅 [iOS 设备上的静默通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification)。
