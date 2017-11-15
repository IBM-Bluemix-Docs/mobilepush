---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 广播通知 
{: #broadcast_notifications}

广播通知是向跨移动设备、浏览器安装，或实现为 Chrome 应用程序或扩展实例，以及针对 {{site.data.keyword.mobilepushshort}} 服务配置的所有应用程序实例发送的消息。缺省情况下，已启用 {{site.data.keyword.mobilepushshort}} 的任何应用程序都已启用广播通知。

当客户机应用程序在向 {{site.data.keyword.mobilepushshort}} 服务进行注册时即可开始接收广播。启用了 {{site.data.keyword.mobilepushshort}} 服务的应用程序都具有预定义的 Push.ALL 标记预订，服务器使用该标记来向所有设备广播通知消息。要使用 REST Push API 发送广播通知，请确保发布到消息资源时，“目标”是一个空的 JSON 文件。
