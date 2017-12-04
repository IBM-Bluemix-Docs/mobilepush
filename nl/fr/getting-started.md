---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Tutoriel Initiation
{: #getting-started-with-push}

Ce tutoriel d'initiation à {{site.data.keyword.mobilepushfull}} vous guide dans la procédure d'activation d'une application Android pour réception de notifications push et d'envoi d'une notification push élémentaire à un appareil.
{:shortdesc}

<div id="prerequisites"></div>

## Avant de commencer
{: #prereqs}

Vous aurez besoin d'un [compte IBM Cloud](https://console.bluemix.net/registration/), d'une instance du service
{{site.data.keyword.mobilepushshort}}, et des outils et prérequis suivants :

  * API Android 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Exemple d'application Android helloPush ](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * SDK [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} et
[BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} installés à l'aide
d'Android Studio ou de Gradle

## Etape 1: Configuration de votre instance {{site.data.keyword.mobilepushshort}} pour appareils Android

1. Copiez le nom de package depuis l'exemple de fichier `AndroidManifest.xml`.

2. Créez une application FCM et ajoutez le nom de package de votre application Android :
  1. Dans la [console Firebase](https://console.firebase.google.com){: new_window}, cliquez sur **Ajouter un projet**, indiquez un nom de projet, puis cliquez sur **Créer un projet**.
  2. Cliquez sur **Ajouter Firebase à votre application Android**, entrez le nom du package d'application et cliquez sur **Enregistrer l'application**. Vous pouvez sauter les deux prochaines invites en cliquant sur
**Continuer > Terminer**. 

3. Ajoutez les données d'identification FCM à votre instance {{site.data.keyword.mobilepushshort}} :
  1. Dans la console Firebase, accédez à **Paramètres > Paramètres du projet > Cloud Messaging**, et copiez la clé du serveur et l'ID d'émetteur.
  2. Dans la console {{site.data.keyword.Bluemix_notm}}, ouvrez le tableau de bord de votre instance de service.
  3. Cliquez sur **Gérer > Configurer**.
  4. Entrez l'ID d'émetteur et la clé du serveur dans la zone **Données d'identification push GCM/FCM**.

## Etape 2: Activation de votre application Android pour envoi de notifications push

1. Configurez les fichiers `build.gradle` de niveau de projet et `build.gradle` de niveau de module :

  * Ajoutez la dépendance du SDK au fichier `build.gradle` du niveau de projet :
  
  ```
  dependencies {
  ........
  compile group: 'com.ibm.mobilefirstplatform.clientsdk.android',
      name: 'push',
      version: '3.+',
      ext: 'aar',
      transitive: true
  .......
	      }
  ```
  {: codeblock}

  * Ajoutez les dépendances suivantes au fichier `build.gradle` de niveau de module :
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * Ajoutez la dépendance au service Google Play à la fin du fichier `build.gradle` de niveau de modèle, après les dépendances :
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * Ajoutez les autorisations suivantes au fichier `AndroidManifest.xml` de votre application :
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
  <uses-permission android:name="android.permission.GET_ACCOUNTS" />
  <uses-permission android:name="android.permission.USE_CREDENTIALS" />
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  ```
  {: codeblock}
  
  * Ajoutez les paramètres d'intention de notification pour l'activité. 
  
  Ce paramètre lance l'application lorsque l'utilisateur clique sur la notification reçue depuis la zone de notification. Remplacez
`<yourAndroidPackageName>` par le nom du package d'application utilisé dans votre application.
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * Mettez à jour le service d'intention FCM et les filtres d'intention pour les notifications d'événement `RECEIVE` et `REGISTRATION`:
  
  ```
  <service android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushIntentService"
    android:exported="true" >
  <intent-filter>
     <action android:name="com.google.firebase.MESSAGING_EVENT" />
  </intent-filter>
  </service>
  <service
  android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPush"android:exported="true" >
  <intent-filter>
   <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
  </intent-filter>
  </service>
  ```
  {: codeblock}
  
2. Ouvrez l'application dans Android Studio et ajoutez le fichier `google-services.json` au répertoire racine du module d'application.

3. Initialisez le SDK principal et le SDK Push. 

Le code d'initialisation est placé fréquemment dans la méthode onCreate() de l'activité principale de votre application Android :

```
// Initialisation du SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialisation du SDK client Push
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... où `<bluemixRegionSuffix>` correspond à l'emplacement où l'application est hébergée. Vous pouvez utiliser l'une des valeurs suivantes :

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID est la valeur de l'identificateur global unique de l'application push et clientSecret, la valeur confidentielle du client push. 

## Etape 3: Enregistrement de votre appareil Android auprès de votre instance {{site.data.keyword.mobilepushshort}}

1. Exécutez votre application.

2. Utilisez l'API MFPPush.register() pour enregistrer votre appareil et activer les notifications basées utilisateur.

```
//Enregistrez votre appareil auprès de l'instance de service Push Notifications
 push.registerDeviceWithUserId("userId",new MFPPushResponseListener<String>() {
 @Override
		public void onSuccess(String response) {
 //Traitement après réussite de l'enregistrement de l'appareil
 }
 @Override
    public void onFailure(MFPPushException ex) {
 //Traitement après échec de l'enregistrement de l'appareil
 }
 });
 ```
 {: codeblock}
 
 
 userId est utilisé pour transmettre la valeur d'ID utilisateur unique pour enregistrement de notifications push. Prenez soin de soumettre également la valeur de clientSecret.
 {: tip}
 
 ## Etape 4: Envoi d'une notification push élémentaire
 
 1. Dans la console {{site.data.keyword.Bluemix_notm}}, accédez au tableau de bord de votre instance de service.
 2. Cliquez sur **Gérer > Envoyer des notifications**.
 3. Sélectionnez Appareils Android dans le menu **Envoyer à**.
 4. Entrez votre message, puis cliquez sur **Envoyer**. 
 
