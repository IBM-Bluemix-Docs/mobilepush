---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-05-30"

keywords: push notifications, notifications, rich media notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Rich Media notifications
{: #rich-media-notifications}

You can enable Rich Media {{site.data.keyword.mobilepushshort}} in iOS 10 and later. Push notifications can be sent with Audio, Video, GIFs and images. 

To set up your application to receive rich push on iOS 10, complete the steps:  

1. In Xcode, select **File** > **New** > **Target** > **Notification Service Extension**.
2. On the method `didReceive()` in the `UNNotificationServiceExtension`, add the  code.
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

To send a Rich Media {{site.data.keyword.mobilepushshort}} from the Push console, ensure that you specify the message, title, subtitle, and attachmentURL fields.