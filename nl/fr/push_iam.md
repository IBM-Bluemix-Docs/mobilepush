---

copyright:
  years:  2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, service access, manage, user roles

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Gestion de l'accès au service
{: #service-access-management}

Avec {{site.data.keyword.mobilepushshort}} et {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM), les propriétaires de compte peuvent gérer l'accès utilisateur depuis leur compte.
{: shortdesc}

En tant que propriétaire de compte, vous pouvez définir des règles sur votre compte afin de créer des niveaux d'accès différents en fonction des utilisateurs. Par exemple, certains utilisateurs peuvent avoir un accès en **lecture seule** à une instance et un accès en **écriture** à une autre. Vous pouvez choisir qui est autorisé à créer, mettre à jour et supprimer des instances de {{site.data.keyword.mobilepushshort}}.

**Remarque :** étant donné que le service {{site.data.keyword.mobilepushshort}} a adopté IAM, la valeur confidentielle de l'application ne sera pas générée pour les nouvelles instances. A la place, vous devez utiliser les [clés d'API](https://cloud.ibm.com/docs/iam?topic=iam-manapikey).

## Rôles utilisateur
{: #roles}

La portée d'une règle d'accès dépend du rôle affecté à un utilisateur.
{: shortdesc}

Les règles permettent d'activer différents niveaux d'accès. Certaines des options sont les suivantes :
<ul><ul>
  <li>Accès à toutes les instances du service dans votre compte</li>
  <li>Accès à des instances de service individuelles dans votre compte</li>
  <li>Accès à une ressource spécifique d'une instance</li>
  <li>Accès à tous les services activés par IAM dans votre compte</li>
</ul></ul>

Les rôles de gestion de plateforme permettent aux utilisateurs d'effectuer des tâches sur des ressources de service au niveau de la plateforme. Par exemple, des rôles peuvent être affectés afin de déterminer qui peut créer ou supprimer des ID, créer des instances, ou encore lier des instances à des applications. Le tableau ci-dessous détaille la corrélation des actions aux rôles de gestion de plateforme.

<table>
  <tr>
    <th>Rôle de plateforme</th>
    <th>Droits</th>
    <th>Exemples d'action</th>
  </tr>
  <tr>
    <td><i>Afficheur</i></td>
    <td>Afficher des instances {{site.data.keyword.mobilepushshort}}.</td>
    <td>Vous pouvez afficher les données d'un utilisateur Cloud Directory ou la configuration du fournisseur d'identité.</td>
  </tr>
  <tr>
    <td><i>Editeur</i></td>
    <td>Afficher et lier des instances {{site.data.keyword.mobilepushshort}}.</td>
    <td>Vous pouvez lier des applications à une instance {{site.data.keyword.mobilepushshort}}.</td>
  </tr>
  <tr>
    <td><i>Opérateur</i></td>
    <td>Créer, supprimer, éditer, interrompre, reprendre, afficher ou lier des instances {{site.data.keyword.mobilepushshort}}.</td>
    <td>Vous pouvez créer ou supprimer une instance {{site.data.keyword.mobilepushshort}} du catalogue.</td>
  </tr>
  <tr>
    <td><i>Administrateur</i></td>
    <td>Toutes les actions de gestion pour tous les services du compte.</td>
    <td>Vous pouvez effectuer toutes les actions d'opérateur et vous avez la possibilité d'affecter des règles à d'autres utilisateurs.</td>
  </tr>
</table>

</br>
</br>Le tableau suivant décrit en détail les actions associées aux rôles d'accès au service. Les rôles d'accès au service permettent aux utilisateurs d'accéder à {{site.data.keyword.mobilepushshort}} et d'appeler l'API {{site.data.keyword.mobilepushshort}}.


<table>
  <tr>
    <th>Rôle de service</th>
    <th>Droits</th>
    <th>Exemples d'action</th>
  </tr>
  <tr>
    <td><i>Lecteur</i></td>
    <td>Afficher les données d'instance {{site.data.keyword.mobilepushshort}}.</td>
    <td>Peut afficher les détails de l'instance de service tels que les données utilisateur ou les informations relatives au fournisseur d'identité.</td>
  </tr>
  <tr>
    <td> <i>Auteur ou Gestionnaire</i></td>
    <td>Afficher et modifier une instance {{site.data.keyword.mobilepushshort}}.</td>
    <td>Peut effectuer toutes les actions du rôle Lecteur, telle l'édition de la configuration du fournisseur d'identité. </li></ul></td>
  </tr>
</table>

Pour plus d'informations sur l'affectation de rôles utilisateur dans l'interface utilisateur, voir [Gestion de l'accès à IAM](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser).


## Règles d'accès {{site.data.keyword.mobilepushshort}}
{: #access}

Vous devez affecter à chaque utilisateur qui accède au service {{site.data.keyword.mobilepushshort}} dans votre compte une règle d'accès avec un rôle utilisateur IAM défini. Cette règle détermine les actions que l'utilisateur peut effectuer dans le contexte du service ou de l'instance que vous sélectionnez.
{: shortdesc}

Les actions sont personnalisées et définies par le service {{site.data.keyword.Bluemix_notm}} en tant qu'opérations dont l'exécution est autorisée dans le service. Les actions sont ensuite mappées vers des rôles utilisateur IAM. Vous pouvez assurer le suivi de certaines des actions effectuées avec le service {{site.data.keyword.cloudaccesstrailshort}}. Dans le tableau ci-dessous, les actions et les droits requis pour {{site.data.keyword.mobilepushshort}} sont mappés.

|Action |Explication |Rôle requis |
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |Obtention de paramètres d'application |Gestionnaire, Auteur, Lecteur|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |Suppression de paramètres d'application |Gestionnaire|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |Mise à jour de paramètres d'application |Gestionnaire|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |Obtention d'appareils |Gestionnaire, Auteur, Lecteur|
|`POST /imfpush/v1/apps/{applicationId}/devices` |Enregistrement d'un appareil |Gestionnaire, Auteur|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Mise à jour d'un appareil |Gestionnaire, Auteur|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Suppression d'un appareil |Gestionnaire|
|`POST /imfpush/v1/apps/{applicationId}/messages` |Envoi de messages |Gestionnaire, Auteur|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |Envoi de messages en bloc |Gestionnaire, Auteur|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |Suppression d'un message |Gestionnaire|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |Obtention de messages |Gestionnaire, Lecteur, Auteur|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |Mise à jour de l'état de distribution des messages |Gestionnaire, Auteur|
|`POST /imfpush/v1/apps/{applicationId}/tags` |Création d'étiquettes |Gestionnaire, Auteur|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Mise à jour d'étiquette  |Gestionnaire, Auteur|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Suppression d'étiquette   |Gestionnaire|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |Obtention d'étiquettes |Gestionnaire, Lecteur, Auteur|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |Création d'abonnements |Gestionnaire, Auteur|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |Suppression d'abonnements |Gestionnaire|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |Obtention d'abonnements |Gestionnaire, Lecteur, Auteur|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |Création de webhook |Gestionnaire, Auteur|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Mise à jour de webhook |Gestionnaire, Auteur|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Suppression de webhook |Gestionnaire|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |Obtention de webhook |Gestionnaire, Lecteur, Auteur|-|

## Utilisation des clés d'API
{: #apikeys}

Au moment de la création des données d'identification de service, il est possible qu'une clé d'API s'affiche à la place de la valeur confidentielle d'application.

Pour utiliser des API REST, vous devez générer le jeton d'accès à l'aide de la commande curl suivante :

### Paramètres

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### Réponse

```
{
    "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```

Une fois le jeton d'accès généré à l'aide de la commande curl précédente, vous pouvez utiliser les API REST en transmettant la ‘<valeur de jeton d'accès> Bearer’ dans l'en-tête d'autorisation.

Par exemple :

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

Pour plus d'informations sur IAM, voir [Accès à IAM](https://cloud.ibm.com/docs/iam?topic=iam-userroles).
