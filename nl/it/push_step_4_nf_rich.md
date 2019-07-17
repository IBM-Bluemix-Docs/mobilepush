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

# Notifiche Rich Media
{: #rich-media-notifications}

Puoi abilitare Rich Media {{site.data.keyword.mobilepushshort}} in iOS 10 e versioni successive. Le notifiche di push possono essere inviate con audio, video, GIF e immagini. 

Per configurare la tua applicazione per ricevere rich push su iOS 10, completa la procedura:  

1. In Xcode, seleziona **File** > **New** > **Target** > **Notification Service Extension**.
2. Sul metodo `didReceive()` in `UNNotificationServiceExtension`, aggiungi il codice.
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

Per inviare un Rich Media {{site.data.keyword.mobilepushshort}} dalla console Push, assicurati di specificare i campi relativi a messaggio, titolo, sottotitolo e URL allegato.
