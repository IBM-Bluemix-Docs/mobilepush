---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 平台型通知
{: #notification_platform}


可以設定通知的目標以送達特定的裝置平台。例如，只能將通知只傳送給所有 Android 使用者或 Google Chrome 使用者。若要傳送使用 REST API 的平台型通知，請確定在公佈至訊息資源時已提供目標平台。請將平台指定為陣列。支援的平台如下：

* A (Apple)
* G (Google)
* WEB_CHROME（Google Chrome 瀏覽器 Web 推送）
* WEB_FIREFOX（Mozilla Firefox 瀏覽器 Web 推送）
* WEB_SAFARI（Safari 瀏覽器 Web 推送）
* APPEXT_CHROME (Google Chrome Apps & Extensions)
