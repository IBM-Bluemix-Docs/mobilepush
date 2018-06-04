---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Etat de distribution des messages
{: #tag_based_notifications}
Dernière mise à jour : 21 août 2017
{: .last-updated}


Avec la fonction {{site.data.keyword.mobilepushshort}}, vous pouvez afficher l'état de distribution de toutes les notifications soumises au service. 

Une fois le message envoyé, vous pouvez suivre les informations de distribution d'un message en consultant son état de distribution. Le service affiche à tout moment l'état des 10 derniers messages disponibles sur une période de 90 jours.

L'onglet **Messages** du service {{site.data.keyword.mobilepushshort}} affiche le statut de notification.

![statut des notifications](images/notification_status_new.png)

1. **ID du message** -  Identificateur unique servant à identifier un message.

2. **Texte du message** - Modèle de message envoyé aux utilisateurs de l'application.

3. **Date** - Date et heure à laquelle le message a été envoyé au service.

4. **Statut** - Offre un bref résumé de l'état d'un message. Selon l'état de distribution du message, l'un des statuts suivants peut s'afficher :

 - Accepté : le message a été accepté pour une distribution par le service Push Notifications.
   
 - En cours de répartition : la notification a été reçue par le fournisseur de notification (APNs, FCM ou Web) et est sur le point d'être répartie. Une notification en cours de répartition peut également renvoyer un échec avec le statut **Echec de répartition**.
 
 - Réparti : la notification a été répartie par le fournisseur de notification.
 
 - En cours de traitement : le message est en cours de traitement, pour être réparti à la passerelle du fournisseur de notification. Une notification en cours de traitement peut également renvoyer un échec avec le statut **Echec du traitement**.
 
 - Inconnu : le statut de la notification est indéterminé.
 
5. **Afficher** - Affiche l'état de distribution des notifications qui sont réparties. Vous pouvez afficher des informations basées sur les aspects suivants :

 - Catégorie : Tous, Mobile, Web<!---and HTTP--->.
 
 - Statut du message : Envoyés, Vus, Ouverts, Non valides. 

![statut des notifications](images/message_delivery_status_new.png)

6. **Options** - Offre un état détaillé d'une notification. L'état peut être suivi en sélectionnant `ID de terminal` ou `ID utilisateur` dans le menu déroulant. Obtenir un message d'état détaillé spécifique à un utilisateur ou à un périphérique peut être utile lorsque vous effectuez le suivi d'un message d'échec.

![état détaillé](images/detailed_message_delivery.png)

**Remarque** : la fonction est uniquement activée pour les utilisateurs ayant opté pour le `plan avancé`. Sélectionnez **Plan** dans la console du service {{site.data.keyword.mobilepushshort}} pour effectuer une [mise à niveau](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)


