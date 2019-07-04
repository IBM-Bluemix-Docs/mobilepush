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

# Notifications Rich Media (média enrichi)
{: #rich-media-notifications}

Vous pouvez activer Rich Media {{site.data.keyword.mobilepushshort}} dans iOS 10 et versions ultérieures. Les notifications Push peuvent être
envoyées avec un contenu audio, vidéo, des GIF et des images. 

Pour configurer votre application pour recevoir des contenus push enrichis dans iOS 10, procédez comme suit :  

1. Dans Xcode, sélectionnez **Fichier** > **Nouveau ** > **Cible** > **Extension de
service de notification**.
2. Sur la méthode `didReceive()` dans `UNNotificationServiceExtension`, ajoutez le code.
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

Pour envoyer une {{site.data.keyword.mobilepushshort}} Rich Media depuis la console Push, prenez soin de renseigner les zones message, titre, sous-titre, et attachmentURL (URL de pièce jointe).
