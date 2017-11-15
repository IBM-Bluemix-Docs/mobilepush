---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 单点广播通知
{: #notification_unicast}


单点广播通知是针对特定设备或用户的通知消息。针对设备的单点广播通知不需要任何额外的设置，当应用程序启用了 {{site.data.keyword.mobilepushshort}} 时，缺省情况下就会启用单点广播通知。

但是，面向用户的单点广播通知要求在向 {{site.data.keyword.mobilepushshort}} 注册客户机移动设备或 Web 浏览器或 Chrome Apps and Extensions 时将用户标识与设备关联。   

通常，客户机应用程序首先会运行认证周期，在这期间会针对认证服务（如 [Mobile Client Access](docs/services/mobileaccess/index.html)）认证移动应用程序用户。在成功认证之后，已认证的用户标识会传递至推送设备注册 API。 

要通过 REST API 发送单点广播通知，请确保发布到消息资源时提供了 deviceId 或 userId。
