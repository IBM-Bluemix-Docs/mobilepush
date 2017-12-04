---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifications basées sur les balises
{: #tag_based_notifications}
Dernière mise à jour : 30 juin 2017
{: .last-updated}

Les messages de notifications basées sur les balises sont envoyés à tous les appareils abonnés à une balise particulière. Elles permettent la segmentation des notifications en fonction de domaines ou de rubriques. Les destinataires des notifications peuvent choisir de ne recevoir les notifications que si elles concernent un sujet ou une rubrique qui les intéresse. Par conséquent, les notifications en fonction d'une balise constituent un moyen de segmenter les destinataires. Cette fonction permet de définir des balises, puis d'envoyer et de recevoir des messages en fonction des balises. Un message n'est ciblé que vers les instances d'application client (sur un appareil mobile, un navigateur ou une extension) qui sont abonnées à la balise. Vous devez d'abord créer des balises pour l'application, configurer les abonnements aux balises puis initier les notifications basées sur une balise. Pour envoyer une notification basée sur une balise qui utilise l'API REST, vérifiez que les éléments "tagNames" sont fournis lors de l'envoi à la ressource de message.

Vous pouvez définir des balises, puis envoyer et recevoir des messages en fonction des balises. Vous devez d'abord créer les balises pour l'application, créer des abonnements, puis initier les
notifications en fonction d'une balise. Pour envoyer une notification basée sur les balises à l'aide de l'[API REST](https://mobile.{DomainName}/imfpush/){: new_window}, vérifiez que les éléments "tagNames" sont fournis lors de l'envoi à la ressource de message.


## Gestion des balises
{: #manage_tags}

Utilisez la console {{site.data.keyword.mobilepushshort}} afin de créer et de supprimer des balises pour votre application, puis d'initier des notifications basées sur des balises. Ces notifications basées sur des balises sont reçues sur les appareils abonnés à ces balises.


### Création de balises
{: #create_tags}

Les notifications basées sur les balises sont des messages qui sont ciblés vers tous les appareils abonnés à une balise
particulière. Chaque appareil peut s'abonner à un nombre illimité de balises. 

1. Sur la console {{site.data.keyword.mobilepushshort}}, sélectionnez l'onglet **Balises**.
1. Cliquez sur le bouton + **Créer une balise**.   
   1. Dans la zone **Nom**, entrez le nom de la balise. Exemple : "coupons".
   1. Dans la zone **Description**, entrez la description de la balise.
   1. Cliquez sur **Sauvegarder**.

1. Dans la zone **Fragments de code**, sélectionnez la plateforme pour votre application mobile.
1. Modifiez les fragments de code pour traiter les erreurs, puis copiez-les pour chaque balise dans votre application mobile.

### Suppression de balises
{: #delete_tags}

1. Dans l'onglet **Balise**, sélectionnez la balise que vous voulez supprimer puis cliquez sur l'icône **Supprimer**.
1. Cliquez sur **OK**.

Quand une balise est supprimée, les informations qui lui sont associées, y compris ses abonnés et les appareils, sont supprimées. Un désabonnement automatique n'est pas nécessaire car cette balise n'existe plus. Aucune autre action supplémentaire n'est nécessaire côté client.

### Edition d'une description de balise
{: #edit_tags}

1. Dans l'onglet **Balise**, sélectionnez la balise à éditer.
1. Cliquez sur l'icône **Editer**.
1. Editez la description de la balise, puis cliquez sur le bouton **Sauvegarder**.

## Obtention des balises
{: #get_tags}

Les balises permettent d'envoyer des notifications ciblées aux utilisateurs en fonction de leurs intérêts, à la différence des diffusions
générales qui sont envoyées à toutes les applications. Vous pouvez les créer et les gérer à l'aide de l'onglet Balises de la console {{site.data.keyword.mobilepushshort}} ou utiliser des API REST. Vous pouvez utiliser des fragments de code pour gérer et interroger vos abonnements aux balises pour votre application mobile. Vous pouvez utiliser les fragments de code pour extraire les abonnements, vous abonner ou annuler l'abonnement à une balise, ou obtenir la liste des balises disponibles. Copiez ces fragments de code dans votre application mobile.


- Pour Android, voir l'API `getTags` et l'API `getSubscriptions` dans [Push Notification get tags on Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

- Pour Cordova, voir l'API `retrieveAvailableTags()` et l'API `retrieveSubscriptions()` dans [Push Notifications get tags on Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Pour iOS, voir l'API `retrieveAvailableTagsWithCompletionHandler` dans [Push Notifications get tags on Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags).

- Pour les navigateurs Web, voir l'API `retrieveAvailableTags()` dans [Push Notifications get tag on web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).


## Abonnement à des balises
{: #Subscribe_tags}

Utilisez l'API suivante pour permettre à vos appareils d'extraire des balises, de s'abonner à des balises, d'extraire la liste des abonnements et d'annuler l'abonnement à une balise.

- Pour Android, utilisez les API `getTags`, `subscribe`, `getSubscriptions` et `unsubscribeFromTags`. Voir [Push Notifications subscribe tags for Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags).

- Pour Cordova, utilisez les API `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` et `unsubscribe()`. Voir [Push Notifications subscribe tags for Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Pour iOS, utilisez les API `retrieveAvailableTagsWithCompletionHandler`, `subscribeToTags`, `retrieveSubscriptionsWithCompletionHandler` et `unsubscribeFromTags`. Voir [Push Notifications subscribe tags for Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags).

- Pour les navigateurs Web, utilisez les API `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` et `unSubscribe()`. Voir [Push Notifications subscribe tags for web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).

## Utilisation de notifications basées sur les balises
{: #using_tags}

Les messages de notifications basées sur les balises sont envoyés à tous les appareils abonnés à une balise particulière. Chaque appareil peut s'abonner à un nombre illimité de balises. Cette rubrique explique comment envoyer des notifications basées sur des balises. Les abonnements sont gérés par l'instance de service IBM Cloud {{site.data.keyword.mobilepushshort}}. Quand une balise est supprimée, toutes les informations qui lui sont associées, y compris ses abonnés et appareils, sont supprimées. Aucun désabonnement automatique n'est requis pour cette balise car elle n'existe plus et aucune action supplémentaire n'est requise depuis le côté client.

Créez des balises sur l'écran **Tag**. Pour plus d'informations sur la création de balises,
voir [Création de balises](t_manage_tags.html).

1. Dans la console **Push Notification**, cliquez sur **Envoyer des notifications**.
1. Sélectionnez l'option **Appareil par étiquette** dans la liste déroulante **Envoyer à**.
1. Recherchez les balises que vous désirez utiliser et sélectionnez-les.
![Ecran Notifications](images/tag_notification.jpg)
1. Dans la zone **Texte du message**, entrez le texte qui sera envoyé en tant que notification aux destinataires abonnés.
1. Cliquez sur **Envoyer**.
