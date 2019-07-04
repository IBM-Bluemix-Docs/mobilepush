---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, faq, frequently asked questions

subcollection: mobile-pushnotification

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Foire aux questions 
{: #faq}

### Pourquoi les jetons deviennent-ils invalidés ?
{: #faq-tokens}	

Pour les appareils, navigateurs, applications et extensions Chrome, le service de notifications push conserve une référence unique aux jetons émis par des fournisseurs de notification - APN pour Apple ou FCM pour Google. Les jetons peuvent être invalidés par le fournisseur de service de notification pour diverses raisons. 

Ceci peut survenir, par exemple, lors de la désinstallation d'une application sur l'appareil. Dans un tel scénario, quand une tentative de distribution d'une notification est effectuée et reçoit une réponse des fournisseurs indiquant que l'appareil est invalidé, le service {{site.data.keyword.mobilepushshort}} retire les enregistrements de l'appareil ou du navigateur Web, ce qui aura pour effet d'empêcher d'autres tentatives d'envoi de notifications à l'appareil invalidé. 

Ce problème peut également survenir si vous avez annulé l'enregistrement d'un appareil.

Prenez soin d'obtenir une clé d'API de serveur et un ID d'émetteur valides pour continuer. Voir [Obtention de vos données d'identification du fournisseur de notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1).

### Pourquoi est-ce que je reçois le message *La notification ne fonctionne pas pour WEB_Chrome.* lorsque je tente d'initialiser le SDK Web Push ?
{: #faq-web-chrome}	

Il se peut que vous ayez changé vos données d'identification FCM pour le SDK Web push et que la remise du message échoue pour le navigateur Chrome. Prenez soin d'appeler *bmsPush.unRegisterDevice* pour éviter un échec.

### Je reçois le message *Les agents de service ne sont pas pris en charge dans ce navigateur* lorsque je tente d'initialiser le SDK pour Web Push. Quel peut être le problème ? 
{: #faq-service-workers}	

Suivez la procédure décrite dans [Etape 3 : Configuration du SDK client du service Push](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3). Prenez également soin :

1. d'utiliser la méthode de lancement correcte ; 
2. d'inclure le fichier `manifest.json` dans le dossier racine ;
3. d'héberger votre site Web. De préférence, créez un module de démarrage `node.js` dans IBM Cloud pour vous exercer. Par exemple : https://<mysamplewebsite>.cloud.ibm.com/.	

### Comment résoudre les erreurs de configuration Web push ?
{: #faq-web-config-errors}	

Les erreurs Web push de
`BMSPushSDK.js` contiennent des informations sur l'échec. Voir [Traitement des incidents](/docs/services/mobilepush?topic=mobile-pushnotification-errors).	

### Les notifications restent-elles persistantes si les unités sont hors ligne ?
{: #faq-notification-persist}	

Cette fonction dépend du fournisseur de notification.	

### L'ID de message (messageID) est-il unique à une application et quelle est sa taille ?
{: #faq-messageid}	

L'ID de message (messageID) est spécifique à l'application et est limité à huit caractères. Il peut être alphanumérique.

### Quelles sont les limites pour les notifications push en termes de taille du contenu ?
{: #faq-limits-push-payload-size}	

La taille d'un message de type {{site.data.keyword.mobilepushshort}} dépend des contraintes imposées par les passerelles (FCM, APNS) et les plateformes client. 

Pour iOS 8 et ultérieur, la taille maximale autorisée est de 4 kilooctets. Notez que les APN n'envoient pas de notifications qui dépassent cette limite. Pour Android, le navigateur Firefox, le navigateur Chrome et les applications et extensions Chrome, la taille maximale du contenu de message est limitée à 4 kilooctets.	

### Les notifications envoyées sont-elles stockées sur les serveurs BMS ?
{: #faq-bms-servers}	

Oui, les notifications sont stockées pendant une période de quatre-vingt-dix jours. Il est recommandé de ne pas envoyer de messages confidentiels sous forme de notifications.

### Puis-je envoyer une notification à des unités en mode Doze (somnolence) ?
{: #faq-doze-mode}	

Cette fonction n'est pas prise en charge.	

### Quels sont les différents plans de tarification pour le service de notifications push ?
{: #faq-pricing-plans}	

* <b>Plan avancé</b> : ce plan est disponible pour 100$/instance, 0,50$/million de messages numériques et 0,50$/million de périphériques adressables. Il vous pouvez envoyer des notifications à 1 million de périphériques adressables et 100 millions de messages numériques. Ce plan inclut des capacités telles que le paramétrage des messages et le suivi du cycle de vie des messages de bout en bout.

* <b>Plan de base</b> : ce plan est disponible pour for 1$/million de messages numériques. Il vous permet d'envoyer des notifications à un seul appareil, à un navigateur, à des noeuds finaux ou à un événement basé webhook. 

* <b>Plan Lite</b> : plan gratuit permettant cent mille messages numériques gratuits par mois. Toutefois, les services du plan Lite sont supprimés au bout de 30 jours d'inactivité.	

### Où puis-je trouver des informations supplémentaires, comme des tutoriels ou des indications sur les nouveautés ?
{: #faq-what-is-new}	

Regardez les [vidéos](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA) du service de notifications push.	

### Existe-t-il une différence entre une notification et un message ?
{: #faq-diff-notification-message}	

Oui. Un _message_ est ce que l'utilisateur soumet au service {{site.data.keyword.mobilepushshort}}. Le service l'envoie sous forme de _notification_ à la passerelle de notification (APN/FCM) et il est remis à l'appareil ou au navigateur Web.

Le public visé reçoit une notification pour chaque message que vous soumettez au service.	

### Le tableau de bord de surveillance du service de notifications push signale-t-il le statut des messages envoyés ?
{: #faq-push-monitor-dashboard}	

L'utilitaire de surveillance affiche le statut de chaque message envoyé. Le statut du message peut être l'un des suivants :
	
* Envoyé : nombre d'appareils auxquels les notifications ont été envoyées.
* Vu : nombre d'appareils auxquels les notifications sont parvenues.
* Ouvert : nombre d'appareils sur lesquels la notification a été ouverte.
* Non valide : nombre d'appareils sur lesquels le jeton n'est pas valide.

Pour plus d'informations, consultez le rapport de messages GET dans l'[API ReST d'IBM Push Notifications](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).	

### La notification push suit-elle la remise de la notification push jusqu'à l'appareil de l'utilisateur final ? Pour Android et aussi pour iOS ?
{: #faq-end-user-device}	

Les notifications push sont suivies par le biais du nombre de notifications vues ou ouvertes sur l'appareil de l'utilisateur final. Ceci s'applique à Android tout comme à iOS. La surveillance basée sur l'ID de l'appareil n'est pas prise en charge. 

### Un message m'avise que le serveur n'est pas disponible actuellement pour traiter les demandes. Comment résoudre ce problème ?
{: #faq-server-unable-to-handle-requests}	

Cette erreur peut être accompagnée du code d'erreur FPWSE0025E. Cela peut être dû à un nombre de demandes trop élevé pour que le serveur puisse les gérer. Essayez de soumettre à nouveau la demande ultérieurement.	

### J'envoie des notifications d'après des étiquettes, mais leur liste est longue et il peut être difficile de les ajouter manuellement. 
{: #faq-tag-based-notification}	

Vous pouvez utiliser les API REST pour automatiser l'ajout d'étiquettes. Voir [Messages POST en bloc](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).

### Comment filtrer la remise de notification push d'après les informations stockées sur l'appareil mobile de l'utilisateur ?
{: #faq-filter-device}	

Cet aspect doit être géré dans le cadre du développement de l'application.

### Puis-je personnaliser la surveillance de notification push en ajoutant un rapport personnalisé, par exemple un rapport de remise par segmentation ?
{: #faq-customize-delivery-report}	

Cette fonction n'est pas prise en charge.

### Puis-je créer un segment pour les nouveaux utilisateurs de l'application ou pour les utilisateurs de l'application mobile qui n'y ont pas accédé depuis un certain temps ?
{: #faq-create-segment}	

Cet aspect doit être géré dans le cadre du développement de l'application.
	
### Puis-je enregistrer/mettre à jour des appareils mobiles en bloc à l'aide des API REST ?
{: #faq-register-mobile-devices}	

Compte tenu de la conception, l'enregistrement/la mise à jour d'un appareil s'effectue depuis les applications mobiles à l'aide du SDK. L'enregistrement/la mise à jour en bloc via les API REST ne sont pas pris en charge. Les appels simultanés d'enregistrements/de mises à jour d'un grand nombre d'appareils à l'aide d'API REST risquent de prendre très longtemps ou d'échouer.	

### Comment puis-je envoyer des notifications push ou utiliser des API REST lorsque je n'ai pas de valeur confidentielle d'application ?
{: #faq-rest-api-appsecret}	

Etant donné que le service {{site.data.keyword.mobilepushshort}} a adopté IAM, une clé d'API (`apiKey`) s'affiche à la place de la valeur confidentielle d'application (`appSecret`) lorsque l'utilisateur crée les données d'identification du service. 

Pour utiliser des API REST, vous devez générer le jeton d'accès à l'aide de la commande curl suivante :

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```

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
{: codeblock}

Une fois le jeton d'accès généré à l'aide de la commande curl précédente, vous pouvez utiliser les API REST en transmettant la valeur du jeton `Bearer <value of access_token>` dans l'en-tête d'autorisation.

Par exemple :

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
