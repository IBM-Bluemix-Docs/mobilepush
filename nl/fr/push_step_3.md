---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, setup client sdk, android application, cordova application, iOS application, web browser

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Etape 4 : Configuration du SDK du client du service
{: #push_step_3}

Vérifiez que vous avez [obtenu vos données d'identification de notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) et [configuré une instance de service](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2). Vous devez alors configurer l'application pour utiliser le service Push Notifications pour enregistrement, abonnement et réception de notifications push. 

Pour configurer le SDK du client du service, procédez comme suit en fonction de votre type d'application.

## Sur des applications Android
{: #push_step_3_Android}

Vous pouvez activer des applications Android pour recevoir des notifications push sur vos appareils. Android Studio, qui est un prérequis, est la méthode recommandée pour générer des projets Android. Une connaissance de base d'Android Studio est essentielle.

Vérifiez que vous avez exécuté la procédure [Obtention des données d'identification de votre fournisseur d'identification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) pour mettre en place le projet FCM et obtenir vos données d'identification.

Exécutez les étapes pour le [SDK Push Notifications pour Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) pour permettre aux applications Android de recevoir des notifications push envoyées par le service. 

1. Ouvrez l'application dans Android Studio. Copiez le fichier `google-services.json` que vous avez créé lors de l'[étape 2 : Obtention de vos données d'identification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) dans le répertoire racine de votre module d'application Android. Vous pouvez constater que le fichier `google-service.json` inclut les noms de packages que vous avez ajouté.

    ![Ajout du fichier json au répertoire racine de votre application](images/FCM_7.jpg "Ajout du fichier json au répertoire racine de votre application")

2. Dans la fenêtre Add Firebase to your Android app, cliquez sur **Continuer**, puis sur **Terminer**. 
3. Générez et exécutez votre application. Si la génération aboutit, le message "`Gradle build finished`" devrait apparaître.
4. Incluez le SDK Push du client avec Gradle.
	1. Configurez votre fichier [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle). 
	2. Configurez le fichier [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest).
	3. Ajoutez le fichier `google-services.json` au répertoire racine de votre module d'application Android.
5. Initialisez les SDK. Voir [Initialisation du SDK principal et du SDK Push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
6. Générez l'application.
7. Vous pouvez l'enregistrer auprès du service Push Notifications en cliquant sur le bouton Enregistrement de l'appareil sur l'application ou en suivant la procédure [Enregistrement auprès du service à l'aide du SDK Push pour Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

L'étape suivante consiste à [envoyer une notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Sur les applications Cordova
{: #push_step_3_Cordova}

Cordova est une plateforme permettant de construire des applications hybrides avec JavaScript, CSS et HTML. Le service Push Notifications prend en charge le développement d'applications iOS et Android basées Cordova.

Pour permettre aux applications Cordova de recevoir des notifications push sur vos appareils, vous devez configurer le [SDK Push du plug-in Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

Après avoir configuré le SDK Push du plug-in Cordova, l'étape suivante consiste à [envoyer une notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Sur les applications iOS
{: #push_step_3_iOS}

Pour permettre aux applications iOS de recevoir des {{site.data.keyword.mobilepushshort}} sur vos appareils, vous devez configurer le [SDK iOS pour le service Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

Après avoir configuré le SDK iOS, l'étape suivante consiste à [envoyer une notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Sur les navigateurs Web
{: #push_step_3_web}

Pour permettre à vos applications de navigateur de recevoir des notifications push, vous devez configurer le [SDK Web pour le service Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

Après avoir configuré le SDK Web, l'étape suivante consiste à [envoyer une notification](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

