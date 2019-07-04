---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, service instance, cordova application

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 第 3 步：配置服务实例 
{: #push_step_2}

确保已经完成[获取通知凭证](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)的操作。

## 对于 Android 和 Chrome Apps & Extensions
{: #push_step_2_Android}

确保您已经完成[获取通知提供程序凭证](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)的操作来设置 FCM 项目并获取凭证。

要为 Android 应用程序和 Google Chrome Apps & Extensions 配置 FCM 凭证，请完成以下步骤：

1. 打开 IBM Cloud“目录”，然后单击已创建的 {{site.data.keyword.mobilepushfull}} 服务实例。 
2. 单击**管理** > **配置**。 
3. 选择以下任一选项： 
	- 对于 Android：选择**移动**，然后使用“发送方标识/项目号”和“API 密钥”更新“FCM 推送凭证”选项卡。 
	- 对于 Google Chrome Apps & Extensions：选择 **Web**，然后使用“发送方标识/项目号”和“API 密钥”更新 Chrome Apps and Extensions 选项卡。 
4. 单击**保存**。现在，Push Notifications 服务已配置。

下一步是[设置 Push 服务客户机 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)。


## 对于 Cordova 应用程序 
{: #push_step_2_b}


Cordova 是一种平台，用于通过 JavaScript、CSS 和 HTML 构建混合应用程序。{{site.data.keyword.mobilepushshort}} 服务支持开发基于 Cordova 的 iOS 和 Android 应用程序。

要使 Cordova 应用程序能接收向设备发送的推送通知，请浏览 [Push Notifications Cordova 插件推送 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)。



## 对于 iOS 应用程序和 Safari 浏览器 
{: #enable-push-ios-notifications}


要使用 {{site.data.keyword.mobilepushshort}} 服务发送通知，请上传在“第 1 步：[获取通知提供程序凭证](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)”中创建的 `.p12` 证书。此证书包含构建和发布应用程序所需的专用密钥和 SSL 证书。此外，也可以使用 REST API 来上传 APNs 证书。

**注**：当 `.cer` 文件出现在钥匙串访问中之后，请将其导出到您的计算机，以创建 `.p12` 证书。

有关使用 APNs 的更多信息，请参阅 [iOS Developer Library: Local and Push Notification Programming Guide ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1){: new_window}。

要在 Push Notifications 服务控制台上设置 APNs，请完成以下步骤：

1. 在 Push Notifications 服务控制台上选择**配置**。
2. 选择**移动**选项，以更新 **APNs 推送凭证**表单上的信息。
3. 选择以下任一选项：
	- 对于**移动**选项
		1. 相应地选择**沙箱**（开发）或**生产**（分发），然后上传已创建的 `p.12` 证书。
		  ![设置 Push Notifications 控制台](images/wizard.jpg "选择了“配置”导航选项的 Push Notifications 控制台，其中显示“移动”选项卡和 APN 推送凭证")

		1. 在**密码**字段中，输入与 `.p12` 证书文件相关联的密码，然后单击**保存**。
	- 对于 **Web** 选项
		- 在“Safari 推送”部分中，使用必要信息更新表单。 
		- **Web 站点名称**：这是您在通知中心中提供的名称。
		- **Web 站点推送标识**：使用 Web 站点推送标识的反向域字符串进行更新。例如，web.com.acmebanks.www。
		- **Web 站点 URL**：提供应该预订到推送通知的 Web 站点 URL。例如，https://www.acmebanks.com。
		- **允许的域**：这是可选参数。这是需要用户提供许可权的 Web 站点列表。请确保 URL 是以逗号分隔的值。请注意，如果未提供此列表，那么将使用 Web 站点 URL 中的值。 
		- **URL 格式字符串**：单击通知时解析的 URL。例如，["https://www.acmebanks.com"]。请确保 URL 使用 http 或 https 方案。-**Safari Web 推送证书**：上传 .p12 证书并提供密码。
4. 单击**保存**。	
![Push Notifications 控制台](images/push_configure_safari.jpg "Web 选项页面字段")	

为 iOS 应用程序设置了服务后，需要[设置 Push 服务客户机 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)。


## 对于 Chrome 和 Firefox 浏览器 
{: #push_step2_chromefirefox}

1. 在 Push Notifications 控制台上，选择**配置**。
2. 选择 Web 选项卡。
![WebPush 配置](images/webpush_configure.jpg "用于定义 Web 站点的 FCM API 密钥和 URL 的 Web Push 配置窗口")
3. 配置 FCM API 密钥和将注册以接收推送通知的 Web 站点的 URL。
4. 单击**保存**。
5. 设置了服务后，需要[设置 Push 服务客户机 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)。


