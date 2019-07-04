---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, rich media notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 複合式多媒體通知
{: #rich-media-notifications}

您可以在 iOS 10 及更新版本啟用「複合式多媒體 {{site.data.keyword.mobilepushshort}}」。可以使用「音訊」、「視訊」、GIF 及影像傳送「推送」通知。 

若要設定應用程式，以在 iOS 10 上接收複合式推送，請完成下列步驟：  

1. 在 Xcode 中，選取**檔案** > **新建** > **目標** > **通知服務延伸**。
2. 在 `UNNotificationServiceExtension` 中的 `didReceive()` 方法上，新增程式碼。
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

若要從 Push 主控台傳送「複合式多媒體」{{site.data.keyword.mobilepushshort}}，請確定您已指定訊息、標題、子標題，及 attachmentURL 欄位。
