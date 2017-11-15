---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 第 5 步：发送通知
{: #push_step_4}
上次更新时间：2017 年 6 月 27 日
{: .last-updated}


开发应用程序后，可以发送基本推送通知。

要发送基本推送通知，请完成以下步骤：

1. 选择**发送通知**，并通过选择**发送至**选项编辑消息。支持的选项有**按标记列出设备**、**设备标识**、**用户标识**、**Android 设备**、**iOS 设备**、**Web 通知**和**所有设备**。
**注**：选择**所有设备**选项时，预订了 {{site.data.keyword.mobilepushshort}} 的所有设备都会收到通知。
	
	![“通知”屏幕](images/tag_notification.jpg)

2. 在**消息**字段中，编辑您的消息。根据需要，选择配置可选设置。
3. 单击**发送**。
3. 验证设备或浏览器是否已收到通知。

以下屏幕快照显示了在 Android 设备上前台处理推送通知的警报框。


	![Android 上的前台推送通知](images/Android_Screenshot.jpg)
以下屏幕快照显示了 Android 后台的推送通知。

	![Android 上的后台推送通知](images/background.jpg)
## 可选 Android 设置 
{: #push_step_4_Android}

对于向 Android 设备发送通知的 {{site.data.keyword.mobilepushshort}} 设置，您可以进一步定制。 


![Android 定制设置](images/android_custom_settings.jpg)

支持以下可选的定制选项：

- 折叠键：折叠键附加在通知上。如果设备脱机时多个通知使用相同的折叠键按顺序抵达，那么将折叠通知。在设备联机时，将从 FCM/GCM 服务器接收通知，并只显示带有相同折叠键的最新通知。如果没有设置折叠键，将存储新和旧的消息，以在以后传递。
- 声音：指示在接收通知时播放声音片段。支持缺省值或应用程序中绑定的声音资源的名称。
- 图标：指定要针对通知显示的图标名称。请确保您已使用客户机应用程序，在 `res/drawable` 文件夹中包装了该图标。
- 优先级：指定将向消息分配传递优先级的选项。 
	- `high` 或 `max` 优先级将生成顶部弹出通知。
	- `low` 或 `default` 优先级不会打开睡眠设备上的网络连接。 
- 可视性：您可以选择将通知可视性选项设置为 `public` 或 `private`。 
	- 
`private` 选项限制公共查看，如果您的设备已通过锁定或模式保护，您可以选择启用该选项，通知设置将设置为**隐藏敏感的通知内容**。当可视性设置为 `private` 时，必须注意 `redact` 字段。仅 `redact` 字段中指定的内容会在设备的安全锁屏上显示。 
	- `public` 选项将使通知可供自由阅读。
- 生存时间：此值以秒为单位进行设置。如果未指定此参数，FCM/GCM 服务器将把消息存储 4 周时间并将尝试传递。4 周后有效性到期。值可以为 0 至 2,419,200 秒之间的值。
- 空闲时延迟：可以将此选项设置为以下任一值：
	- `true` 指示 FCM/GCM 服务器在设备空闲时不传递通知。 
	- `false` 确保即使在设备空闲时也传递通知。
- 同步：通过将此选项设置为 `true`，将同步所有已注册设备的通知。如果某个用户名的用户在多个设备上安装了相同的应用程序，那么在一个设备上读取通知将确保删除其他设备上的通知。要使此选项生效，您需要确保已使用用户标识向 {{site.data.keyword.mobilepushshort}} 服务进行注册。
- 其他有效内容：为您的通知指定定制的有效内容值。
- 可展开通知：此功能允许客户选择展开带有更多信息的通知，而在通知折叠时可以看到基本通知。支持以下选项：
	- 大图片通知：可以选择在展开通知时包含图片。确保提供图片的标题文本和 URL。
	- 大文本通知：可以选择包含带有标题的其他文本。确保提供“大文本”消息和“标题”文本信息。
	- 收件箱样式通知：可以发送样式为收件箱通知的通知。请在“标题”中提供文本，并在“行”中提供消息。	 

## 可选 iOS 设置 
{: #push_step_4_ios}

可以定制用于将通知发送至 iOS 设备的 {{site.data.keyword.mobilepushshort}} 设置。支持以下可选的定制选项。

- **角标**：指示在应用程序角标上显示的数字。缺省值为零 (0)，这样不会显示角标。 
- **声音**：指示在接收通知时播放声音片段。支持缺省值或应用程序中绑定的声音资源的名称。
- **其他有效内容**：为您的通知指定定制的有效内容值。

您还可以选择启用[交互式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications)和[富媒体通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications)。

## 监视传递的通知 
{: #push_step_4_monitor}

{{site.data.keyword.mobilepushshort}} 服务提供监视实用程序，以帮助您检查已发送消息的状态。要配置监视实用程序，请完成以下任一选项：

- [启用 Android 应用程序监视](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring)。
- [启用 iOS 应用程序监视](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring)。
