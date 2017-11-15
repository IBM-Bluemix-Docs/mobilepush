---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 基于平台的通知
{: #notification_platform}


可将通知定向发送到特定的设备平台。例如，可以只将通知发送给所有 Android 用户或 Google Chrome 用户。要使用 REST API 发送基于平台的通知，请确保发布到消息资源时提供了目标平台。将平台指定为数组。支持的平台如下所示：

* A (Apple) 
* G (Google)
* WEB_CHROME（Google Chrome 浏览器 Web 推送）
* WEB_FIREFOX（Mozilla Firefox 浏览器 Web 推送）
* WEB_SAFARI（Safari 浏览器 Web 推送）
* APPEXT_CHROME (Google Chrome Apps & Extensions)
