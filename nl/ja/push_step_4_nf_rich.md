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

# リッチ・メディア通知
{: #rich-media-notifications}

iOS 10 以降でリッチ・メディアの {{site.data.keyword.mobilepushshort}} を有効にできます。 プッシュ通知は、音声、ビデオ、GIF、およびイメージとともに送信できます。 

iOS 10 でリッチ・プッシュを受信するようにアプリケーションをセットアップするには、以下を実行します。  

1. Xcode で、**「File」** > **「New」** > **「Target」** > **「Notification Service Extension」**を選択します。
2. `UNNotificationServiceExtension` 内のメソッド `didReceive()` に以下のコードを追加します。
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

リッチ・メディアの {{site.data.keyword.mobilepushshort}} を Push コンソールから送信するには、メッセージ、タイトル、サブタイトル、および attachmentURL の各フィールドを指定するようにしてください。
