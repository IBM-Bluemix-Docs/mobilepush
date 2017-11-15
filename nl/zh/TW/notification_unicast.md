---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 單點播送通知
{: #notification_unicast}


單點播送通知是指以特定裝置或使用者為目標的訊息。以裝置為目標的單點播送通知不需要任何額外的設定，而且預設會在應用程式啟用 {{site.data.keyword.mobilepushshort}} 時予以啟用。

不過，以使用者為目標的單點播送通知需要在登錄用戶端行動裝置或 Web 瀏覽器或 Chrome Apps and Extensions for {{site.data.keyword.mobilepushshort}} 時，關聯使用者 ID 與裝置。   

一般而言，用戶端應用程式會先執行鑑別週期，在此鑑別週期，會針對鑑別服務（例如 [Mobile Client Access](docs/services/mobileaccess/index.html)）鑑別行動應用程式使用者。鑑別成功時，接著會將已鑑別使用者 ID 傳遞至「推送裝置登錄 API」。 

若要透過 REST API 傳送單點播送通知，請確定在公佈至訊息資源時已提供 deviceId 或 userId。
