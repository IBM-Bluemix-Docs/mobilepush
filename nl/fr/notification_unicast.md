---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifications Unicast
{: #notification_unicast}


Les notifications Unicast sont des messages qui sont envoyés à un appareil ou utilisateur spécifique. Les notifications Unicast ciblant des appareils ne requièrent pas de configuration supplémentaire et sont activées par défaut lorsque l'application est activée pour {{site.data.keyword.mobilepushshort}}.

Toutefois, les notifications Unicast ciblées vers des utilisateurs nécessitent l'association d'un ID utilisateur à un appareil au moment de l'enregistrement de l'appareil mobile client, du navigateur Web ou des applications et extensions Chrome pour {{site.data.keyword.mobilepushshort}}.   

En général, une application client exécute d'abord un cycle d'authentification au cours duquel l'utilisateur d'application mobile est authentifié auprès d'un service d'authentification comme [Mobile Client Access](docs/services/mobileaccess/index.html). Si l'authentification aboutit, l'ID de l'utilisateur authentifié est transféré vers l'API d'enregistrement d'appareil Push. 

Pour envoyer une notifications Unicast via une API REST, veillez à ce que les ID d'appareil ou d'utilisateur soient fournis lors de l'envoi à une ressource de message.
