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

# Rich Media-Benachrichtigungen
{: #rich-media-notifications}

Sie können Rich Media {{site.data.keyword.mobilepushshort}} iOS 10 und höher aktivieren. Push-Benachrichtigungen können mit Audio, Video, GIFs und Bildern gesendet werden. 

Führen Sie die folgenden Schritte aus, um Ihre Anwendungen unter iOS 10 für den Empfang von Rich Push-Benachrichtigungen einzurichten:  

1. Wählen Sie in Xcode **File** > **New** > **Target** > **Notification Service Extension** aus.
2. Fügen Sie in der Methode `didReceive()` in `UNNotificationServiceExtension` den folgenden Code hinzu.
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

Geben Sie zum Senden einer Rich Media-Push-Benachrichtigung über die Push-Konsole unbedingt Daten in die Felder für Nachricht, Titel, Untertitel und attachmentURL ein.
