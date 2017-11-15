---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifications basées utilisateur
{: #user_based_notifications}
Dernière mise à jour : 22 mai 2017
{: .last-updated}

Les notifications de type {{site.data.keyword.mobilepushshort}} basées sur les utilisateurs sont envoyées vers les utilisateurs d'applications mobiles avec des messages personnalisés. Avec ce type de notifications, vous pouvez choisir de notifier certains individus spécifiques en fonction de leurs préférences.

## Enregistrement de l'appareil avec l'ID utilisateur
{: #register_device_wh_userid}

Pour activer les notifications push ciblées par ID utilisateur, prenez soin d'enregistrer l'appareil avec une zone ID utilisateur définie.     

L'ID utilisateur peut être toute chaîne fournie par l'application à l'API d'enregistrement d'appareil. Généralement, une application mobile exécute d'abord un cycle d'authentification au cours duquel l'utilisateur de l'application mobile s'authentifie auprès d'un service d'authentification tel que [{{site.data.keyword.amafull}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/docs/services/mobileaccess/index.html){: new_window}. Si l'authentification aboutit, l'ID de l'utilisateur authentifié est transféré vers l'API d'enregistrement d'appareil Push. 

Pour vous enregistrer pour une notification basée userId (ID utilisateur), voir :

- [Registering an Android application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [Registering an iOS application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Registering a Cordova application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Registering a web application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## Utilisation des notifications basées sur un ID utilisateur
{: #using_userid}

Les notifications basées sur un ID utilisateur sont des messages de notification qui sont ciblés vers un utilisateur spécifique. Plusieurs appareils différents peuvent être enregistrés avec un seul et même utilisateur. La procédure suivante décrit comment envoyer des notifications à base d'ID utilisateur.

1. Dans la console **Push Notification**, sélectionnez l'option **Envoyer des notifications**.
1. Sélectionnez **ID utilisateur** dans la liste des options **Envoyer à**.
1. Dans la zone **ID utilisateur**, recherchez l'ID utilisateur dont vous voulez vous servir puis cliquez sur **+Ajouter**.![Ecran d'envoi des notifications](images/user_notification.jpg)
1. Dans la zone **Message**, entrez le texte que vous voulez envoyer dans votre notification.
1. Cliquez sur **Envoyer**.


## Synchronisation de la connexion et de la déconnexion utilisateur 
{: #sync_login_logout}

Vous pouvez choisir de n'envoyer des notifications que si l'utilisateur est connecté. 

Supposez par exemple qu'un appareil est partagé par les membres d'une équipe au travail et qu'il est nécessaire de s'adresser uniquement à certains de ces utilisateurs. Dans un tel cas, il y aura une séquence de connexion/déconnexion. Ce mécanisme d'authentification permet à l'application d'effectuer un suivi de l'identité de l'utilisateur actuel de l'application, ce qui garantit que les notifications envoyées à un utilisateur spécifique ne sont toujours reçues que par cet utilisateur uniquement. Une fois la connexion effectuée, invoquez l'API d'enregistrement d'appareil en passant l'ID utilisateur de l'utilisateur connecté. De la même façon, avant de vous déconnecter, appelez l'API `unregistration` de l'appareil. Le séquencement de ces API Push avec les opérations de connexion et de déconnexion garantit que les notifications destinées à un utilisateur spécifique ne sont envoyées qu'à cet utilisateur uniquement.
