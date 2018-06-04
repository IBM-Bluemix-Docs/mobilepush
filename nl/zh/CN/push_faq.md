---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-28"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 常见问题 
{: #faq}


1. 为什么令牌会失效？
	
	对于设备、浏览器和 Chrome Apps & Extensions 注册，Push Notifications 服务会保持对通知提供程序颁发的令牌的唯一引用。对于 Apple，通知提供程序为 APNs；而对于 Google，则为 FCM。该服务通知提供程序可能出于几种原因使令牌失效。 

	例如，在设备上卸载应用程序期间。在这种情况下，如果有传递通知的尝试，通知提供者就会给出有关设备已失效的响应，{{site.data.keyword.mobilepushshort}} 服务会根据该响应来除去设备或 Web 浏览器注册。这样会抑制后续的尝试，阻止将通知发送给这些已失效的设备。 

	如果注销了设备，也可能会遇到此问题。

	确保获取有效的“服务器 API 密钥”和“发送方标识”以继续。请参阅[获取通知提供程序凭证](push_step_1.html)。


2. 尝试初始化 Web 推送 SDK 时，为什么会收到消息称“通知对 WEB_Chrome 无效”？

	您可能更改了用于 Web 推送 SDK 的 FCM 凭证，因此对于 Chrome 浏览器，消息传递可能会失败。请确保调用“bmsPush.unRegisterDevice”以避免失败。

3. 尝试初始化 Web 推送 SDK 时，收到消息“此浏览器中不支持服务工作程序”。问题可能出在哪里？ 

	执行[第 3 步：设置 Push 服务客户机 SDK](push_step_3.html) 中提到的步骤。另请确保：
 
	1. 使用正确的启动方法。 
	1. 将 `manifest.json` 文件包含在根文件夹中。
	1. 托管 Web 站点。最好在 IBM Cloud 中创建 `node.js` 入门模板以试用。例如：https://<mysamplewebsite>.mybluemix.net/。	

4. 如何解决 Web 推送 Web 配置错误？

	来自 `BMSPushSDK.js` 的 Web 推送错误包含失败的相关信息。请参阅[故障诊断](push_troubleshooting.html)。	

5. 如果设备脱机，通知会持久存储吗？

	此功能取决于通知提供程序。	

6. messageID 对于应用程序是否唯一，其大小是多少？

	messageID 对于应用程序唯一，其大小限制为 8 个字符。可以为字母数字。

7. Push Notifications 在有效内容大小方面有哪些限制？

	{{site.data.keyword.mobilepushshort}} 消息有效内容大小取决于网关（FCM、APNs）和客户机平台规定的约束。 

	对于 iOS 8 和更高版本，允许的最大大小为 4 KB。请注意，APNs 不会发送超过此限制的通知。对于 Android、Firefox 浏览器、Chrome 浏览器和 Chrome Apps & Extensions，允许的消息有效内容最大大小限制为 4 KB。	

8. 已发送的通知是存储在 BMS 服务器中吗？

	是的，通知会存储七天时间。建议不要将任何保密消息作为通知发送。

9. 能向打盹方式下的设备发送通知吗？

	不支持此功能。	

10. Push Notifications 服务有哪些可用的价格套餐？

	基本套餐：使用此套餐的价格是 1.00 美元/百万数字消息。使用基本套餐，可以向唯一的设备、浏览器、端点或基于 Webhook 的事件发送推送通知。 

	轻量套餐：这是免费套餐，每个月可以免费使用 10 万条数字消息。但是，轻量套餐服务在处于不活动状态 30 天后会被删除。	

11. 在哪里能找到诸如教程或新增内容之类的更多信息？

	请浏览 Push Notifications 服务[博客](http://push-notification-service.mybluemix.net/)。	

12. 通知和消息之间有差别吗？

	有。_消息_是用户向 {{site.data.keyword.mobilepushshort}} 服务提交的内容。该服务会将此内容作为_通知_分派给通知网关 (APNs/FCM)，然后此内容会传递到设备或 Web 浏览器。

	对于您提交给该服务的每条消息，目标受众都会收到一个通知。	

13. Push Notifications 监视仪表板针对所发送消息会显示任何状态吗？

	监视实用程序针对每条已发送消息都会显示状态。消息可能处于以下状态：
	
	- 已发送：向其发送通知的目标设备数。
	- 已显示：通知到达的目标设备数。
	- 已打开：已打开通知的设备数。
	- 无效：令牌在其中无效的设备数。

	有关更多信息，请参阅 [IBM Push Notifications REST API](https://imfpush.{DomainName}/imfpush/) 中的“通过 GET 操作获取消息报告”。	

14. 推送通知会监视推送通知传递至最终用户设备吗？对于 Android 和 iOS 都是这样吗？

	将基于最终用户设备中已显示或已打开的通知数监视推送通知。此功能对于 Android 和 iOS 均可用。不支持基于设备标识的监视。 

15. 我收到消息称，服务器当前无法处理请求。我该如何解决此问题？

	您可能会看到此错误及错误代码 FPWSE0025E。这可能是因为服务器要处理的请求太多。可以尝试稍后重新提交请求。	

16. 我要通过标记发送通知，但标记列表太长，手动添加可能很麻烦。 
	
	可以使用 REST API 来自动添加标记。请参阅[通过 POST 操作发布批量消息](https://imfpush.{DomainName}/imfpush/)。

17. 我该如何按用户移动设备中存储的消息来过滤推送通知传递？

	这应该在应用程序开发上下文中进行处理。

18. 我能进一步定制推送通知监视以添加定制报告（例如，按分段列出的传递报告）吗？

	不支持此功能。

19.  我能为新应用程序用户或有一段时间未访问移动应用程序的用户创建分段吗？

	这应该在应用程序开发上下文中进行处理。


	


	
	




	


