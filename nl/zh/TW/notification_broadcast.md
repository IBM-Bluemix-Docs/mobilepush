---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 播送通知 
{: #broadcast_notifications}

播送通知是訊息，以針對 {{site.data.keyword.mobilepushshort}} 服務跨行動裝置、瀏覽器或者實作為 Chrome 應用程式或延伸規格實例安裝及配置的所有應用程式實例為目標。任何已啟用 {{site.data.keyword.mobilepushshort}} 的應用程式預設都會啟用播送通知。

用戶端應用程式向 {{site.data.keyword.mobilepushshort}} 服務登錄自己後，就可以開始接收播送。啟用 {{site.data.keyword.mobilepushshort}} 服務的應用程式都會有 Push.ALL 標籤的預先定義訂閱，伺服器會使用此標籤將通知訊息播送給所有裝置。若要傳送使用 Push REST API 的播送通知，請確定在公佈至訊息資源時，"target" 是空的 JSON 檔案。
