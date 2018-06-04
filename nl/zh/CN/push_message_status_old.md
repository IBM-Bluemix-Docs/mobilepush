---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 消息通知传递状态
{: #tag_based_notifications}
上次更新时间：2017 年 8 月 21 日
{: .last-updated}


使用 {{site.data.keyword.mobilepushshort}} 服务，您可以查看已提交给服务的每个通知的状态。 

已提交的消息可能具有以下状态：

- **已接受**：Push Notifications 服务已接受消息进行传递。
- **正在处理**：正在处理消息以分派给通知提供程序网关。正在处理的通知也可能返回失败，状态为**处理失败**。
- **正在分派**：通知提供程序（APNs、FCM 或 Web）已收到通知，并且即将分派通知。处于分派过程中的通知也可能返回失败，状态为**分派失败**。
- **已分派**：通知提供程序已分派通知。
- **未知**：无法确定通知的状态。

{{site.data.keyword.mobilepushshort}} 服务的“消息”选项卡显示通知状态。

![通知状态](images/notification_status_new.png)

1. **查看**选项显示分派的通知的传递状态。可以查看基于以下方面的信息：

 - 类别：全部、移动、Web<!---and HTTP--->。
 - 消息状态：已发送、已查看、已打开和无效。 

![通知状态](images/message_delivery_status_new.png)

2. 单击**选项**以获取**详细消息传递状态**。可通过从下拉菜单中选择`设备标识`或`用户标识`来跟踪详细传递状态。可访存特定用户或设备的详细信息状态。

![详细状态](images/detailed_message_delivery.png)


在任意给定时刻，服务仅显示在 90 天内可用的最近 10 条消息的状态。

**注**：此功能仅对选择`高级价格套餐`的用户启用。在 {{site.data.keyword.mobilepushshort}} 服务控制台中选择**套餐**以进行[升级](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)
