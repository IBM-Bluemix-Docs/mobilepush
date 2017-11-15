---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Notifications de diffusion 
{: #broadcast_notifications}

Les notifications de diffusion sont des messages ciblés vers toutes les instances d'une application installée sur des appareils mobiles et des navigateurs ou implémentée en tant qu'application ou instance d'application Chrome et configurée pour le service {{site.data.keyword.mobilepushshort}} ; elles sont activées par défaut dans toute application activée pour {{site.data.keyword.mobilepushshort}}.

Quand une application client s'enregistre auprès du service {{site.data.keyword.mobilepushshort}}, elle peut commencer à recevoir des diffusions. Les applications activées pour le service {{site.data.keyword.mobilepushshort}} possèdent un abonnement prédéfini à la balise Push.ALL, qui est utilisé par le serveur pour diffuser des messages de notification de diffusion à tous les appareils. Pour envoyer une notification de diffusion qui utilise l'API REST Push, assurez-vous que la "cible" est un fichier JSON vide lors de l'envoi à la ressource de message.
