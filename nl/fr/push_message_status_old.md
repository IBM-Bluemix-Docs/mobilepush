---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Statut de distribution des notifications de messages
{: #tag_based_notifications}
Dernière mise à jour : 21 août 2017
{: .last-updated}


Avec le service {{site.data.keyword.mobilepushshort}}, vous pouvez afficher le statut de chaque notification ayant été soumise au service. 

Un message ayant été soumis peut avoir les statuts suivants : 

- **Accepté** : Le message a été accepté pour sa distribution par le service Push Notifications.
- **En cours de traitement** : Le message est en cours de traitement, pour être réparti à la passerelle du fournisseur de notification. Une notification en cours de traitement peut également renvoyer un échec avec le statut **Echec du traitement**.
- **En cours de répartition** : La notification a été reçue par le fournisseur de notification (APNs, FCM, ou Web) et est sur le point d'être répartie. Une notification en cours de répartition peut également renvoyer un échec avec le statut **Echec de répartition**.
- **Réparti** : La notification a été répartie par le fournisseur de notification.
- **Inconnu** : Le statut de la notification est indéterminé.

L'onglet Messages du service {{site.data.keyword.mobilepushshort}} affiche le statut de notification.

![statut des notifications](images/notification_status_new.png)

1. L'option **Afficher** affiche l'état de distribution des notifications qui sont réparties. Vous pouvez afficher des informations basées sur les aspects suivants :

 - Catégorie : Tous, Mobile, Web<!---and HTTP--->.
 - Statut du message : Envoyés, Vus, Ouverts, Non valides. 

![statut des notifications](images/message_delivery_status_new.png)

2. Cliquez sur **Options** pour obtenir un **état détaillé de la distribution des messages**. Un état de distribution détaillé peut être obtenu en sélectionnant `ID de terminal` ou `ID utilisateur` dans le menu déroulant. Un état détaillé d'un utilisateur spécifique ou d'un périphérique peut être extrait.

![état détaillé](images/detailed_message_delivery.png)


Le service n'affiche à tout moment que l'état des 10 derniers messages disponibles sur une période de 90 jours.

**Remarque** : la fonction est uniquement activée pour les utilisateurs ayant opté pour le `plan de tarification avancé`. Sélectionnez **Plan** dans la console du service {{site.data.keyword.mobilepushshort}} pour effectuer une [mise à niveau](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)
