---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifications Rich Media (média enrichi)
{: #interactive-notifications}
Dernière mise à jour : 13 juillet 2017
{: .last-updated}


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
