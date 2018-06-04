---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-28"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Foire aux questions 
{: #faq}


1. Pourquoi les jetons deviennent-ils invalidés ?
	
	Pour les appareils, navigateurs, applications et extensions Chrome, le service de notifications Push conserve une référence unique aux jetons émis par des fournisseurs de notification - APN pour Apple ou FCM pour Google. Les jetons peuvent être invalidés par le fournisseur de service de notification pour diverses raisons. 

	Ceci peut survenir, par exemple, lors de la désinstallation d'une application sur l'appareil. Dans un tel scénario, quand une tentative de distribution d'une notification est effectuée et reçoit une réponse des fournisseurs indiquant que l'appareil est invalidé, le service {{site.data.keyword.mobilepushshort}} retire les enregistrements de l'appareil ou du navigateur Web, ce qui aura pour effet d'empêcher d'autres tentatives d'envoi de notifications à l'appareil invalidé. 

	Ce problème peut également survenir si vous avez annulé l'enregistrement d'un appareil.

	Prenez soin d'obtenir une clé d'API de serveur et un ID d'émetteur valides pour continuer. Voir [Obtention de vos données d'identification du fournisseur de notification](push_step_1.html).


2. Pourquoi reçois-je le message "La notification ne fonctionne pas pour WEB_Chrome." lors de la tentative d'initialisation du SDK Web Push ?

	Il se peut que vous ayez changé vos données d'identification FCM pour le SDK Web push et que la remise du message échoue pour le navigateur Chrome. Prenez soin d'appeler "bmsPush.unRegisterDevice" pour éviter un échec.

3. Je reçois le message "Les agents de service ne sont pas pris en charge dans ce navigateur" lors de la tentative d'initialisation du SDK pour Web Push. Quel peut être le problème ? 

	Suivez la procédure décrite dans [Etape 3 : Configuration du SDK client du service Push](push_step_3.html).	Prenez soin également de :
 
	1. Utiliser la méthode de lancement correcte. 
	1. Inclure le fichier `manifest.json` dans le dossier racine.
	1. Héberger votre site Web. De préférence, créez un module de démarrage `node.js` dans IBM Cloud pour vous exercer. Par exemple : https://<mysamplewebsite>.mybluemix.net/.	

4. Comment résoudre les erreurs de configuration Web push ?

	Les erreurs Web push de
`BMSPushSDK.js` contiennent des informations sur l'échec.  Voir [Traitement des incidents](push_troubleshooting.html).	

5. Les notifications restent-elles persistantes si les unités sont hors ligne ?

	Cette fonction dépend du fournisseur de notification.	

6. L'ID de message (messageID) est-il unique à une application et quelle est sa taille ?

	L'ID de message (messageID) est spécifique à l'application et est limité à huit caractères. Il peut être alphanumérique.

7. Quelles sont les limites pour les notifications Push en termes de taille du contenu ?

	La taille d'un message de type {{site.data.keyword.mobilepushshort}} dépend des contraintes imposées par les passerelles (FCM, APNS) et les plateformes client. 

	Pour iOS 8 et ultérieur, la taille maximale autorisée est de 4 kilooctets. Notez que les APN n'envoient pas de notifications qui dépassent cette limite. Pour Android, le navigateur Firefox, le navigateur Chrome et les applications et extensions Chrome, la taille maximale du contenu de message est limitée à 4 kilooctets.	

8. Les notifications envoyées sont-elles stockées sur les serveurs BMS ?

	Oui, les notifications sont stockées pendant une période de sept jours. Il est recommandé de ne pas envoyer de messages confidentiels sous forme de notifications.

9. Puis-je envoyer une notification à des unités en mode Doze (somnolence) ?

	Cette fonction n'est pas prise en charge.	

10. Quels sont les différents plans de tarification pour le service Push Notifications ?

	Plan basique : disponible pour $1.00 USD/million de messages numériques. Ce plan vous permet d'envoyer des notifications à un seul appareil, à un navigateur, à des noeuds finaux ou à un événement basé webhook. 

	Plan Lite : plan gratuit permettant cent mille messages numériques gratuits par mois. Toutefois, les services du plan Lite sont supprimés au bout de 30 jours d'inactivité.	

11. Où puis-je trouver des informations supplémentaires, comme des tutoriels ou des indications sur les nouveautés ?

	Accédez au [blogue](http://push-notification-service.mybluemix.net/) du service Push Notifications.	

12. Existe-t-il une différence entre une notification et un message ?

	Oui. Un _message_ est ce que l'utilisateur soumet au service {{site.data.keyword.mobilepushshort}}. Le service l'envoie sous forme de _notification_ à la passerelle de notification (APN/FCM) et il est remis à l'appareil ou au navigateur Web.

	Le public visé reçoit une notification pour chaque message que vous soumettez au service.	

13. Le tableau de bord de surveillance du service Push Notifications signale-t-il le statut des messages envoyés ?

	L'utilitaire de surveillance affiche le statut de chaque message envoyé. Le statut du message peut être l'un des suivants :
	
	- Envoyé : nombre d'appareils auxquels les notifications ont été envoyées.
	- Vu : nombre d'appareils auxquels les notifications sont parvenues.
	- Ouvert : nombre d'appareils sur lesquels la notification a été ouverte.
	- Non valide : nombre d'appareils sur lesquels le jeton n'est pas valide.

	Pour plus d'informations, consultez le rapport de messages GET dans l'[API ReST d'IBM Push Notifications](https://imfpush.{DomainName}/imfpush/).	

14. La notification push suit-elle la remise de la notification push jusqu'à l'appareil de l'utilisateur final ? Pour Android et aussi pour iOS ?

	Les notifications Push sont suivies par le biais du nombre de notifications vues ou ouvertes sur l'appareil de l'utilisateur final. Ceci s'applique à Android tout comme à iOS. La surveillance basée sur l'ID de l'appareil n'est pas prise en charge. 

15. Un message m'avise que le serveur n'est pas disponible actuellement pour traiter les demandes. Comment résoudre ce problème ?

	Cette erreur peut être accompagnée du code d'erreur FPWSE0025E. Cela peut être dû à un nombre de demandes trop élevé pour que le serveur puisse les gérer. Essayez de soumettre à nouveau la demande ultérieurement.	

16. J'envoie des notifications d'après des balises, mais leur liste est longue et il peut être difficile de les ajouter manuellement. 
	
	Vous pouvez utiliser les API REST pour automatiser l'ajout de balises. Voir [Messages POST en bloc](https://imfpush.{DomainName}/imfpush/).

17. Comment filtrer la remise de notification push d'après les informations stockées sur l'appareil mobile de l'utilisateur ?

	Cet aspect doit être géré dans le cadre du développement de l'application.

18. Puis-je personnaliser la surveillance de notification push en ajoutant un rapport personnalisé, par exemple un rapport de remise par segmentation ?

	Cette fonction n'est pas prise en charge.

19.  Puis-je créer un segment pour les nouveaux utilisateurs de l'application ou pour les utilisateurs de l'application mobile qui n'y ont pas accédé depuis un certain temps ?

	Cet aspect doit être géré dans le cadre du développement de l'application.


	


	
	




	


