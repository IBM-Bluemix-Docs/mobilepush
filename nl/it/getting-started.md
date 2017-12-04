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

# Esercitazione introduttiva
{: #getting-started-with-push}

In questa esercitazione introduttiva {{site.data.keyword.mobilepushfull}}, illustreremo il processo per abilitare un'applicazione Android a ricevere le notifiche push e inviare una notifica push di base a un dispositivo.
{:shortdesc}

<div id="prerequisites"></div>

## Prima di cominciare
{: #prereqs}

Avrai bisogno di un [account IBM Cloud](https://console.bluemix.net/registration/), un'istanza del servizio
{{site.data.keyword.mobilepushshort}} e i seguenti strumenti e requisiti:

  * Android API 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android helloPush sample app](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * Le SDK [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} e
  [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} installate utilizzando
  Android Studio o Gradle

## Passo 1: configura la tua istanza {{site.data.keyword.mobilepushshort}} per i dispositivi Android

1. Copia il nome del pacchetto dal file `AndroidManifest.xml` di esempio.

2. Crea un'applicazione FCM e aggiungi il nome del pacchetto della tua applicazione Android:
  1. Nella [Console Firebase](https://console.firebase.google.com){: new_window}, fai clic su **Aggiungi progetto**, fornisci
  un nome progetto e fai clic su **Crea progetto**.
  2. Fai clic su **Aggiungi Firebase alla tua applicazione Android**, immetti il nome del pacchetto dell'applicazione e fai clic su **Registra applicazione**. Puoi saltare le prossime due
  richieste facendo clic su **Continua > Fine**. 

3. Aggiungi le credenziali FCM alla tua istanza {{site.data.keyword.mobilepushshort}}:
  1. Nella consola, vai a **Impostazioni > Impostazioni progetto > Messaggistica cloud** e copia l'ID mittente e la chiave server.
  2. Nella console {{site.data.keyword.Bluemix_notm}}, apri il dashboard della tua istanza del servizio.
  3. Fai clic su **Gestisci > Configura**.
  4. Immetti l'ID mittente e la chiave server nel campo **Credenziali push GCM/FMC**.

## Passo 2: abilita la tua applicazione Android a inviare le notifiche push

1. Configura i file `build.gradle` del livello del progetto e `build.gradle` del livello del modulo:

  * Aggiungi la dipendenza SDK al file `build.gradle` del livello del progetto:
  
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

  * Aggiungi le seguenti dipendenze al file `build.gradle` del livello del modulo:
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * Aggiungi la dipendenza dei servizi Google play alla fine del file `build.gradle` del livello del modulo dopo le dipendenze:
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * Aggiungi le seguenti autorizzazioni al file `AndroidManifest.xml` della tua applicazione:
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.USE_CREDENTIALS" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  ```
  {: codeblock}
  
  * Aggiungi le impostazioni di intento di notifica per l'attività. 
  
  Questa impostazione avvia l'applicazione quando l'utente fa clic sulla notifica ricevuta dall'area di notifica. Sostituisci
  `<yourAndroidPackageName>` con il nome del pacchetto dell'applicazione utilizzato nella tua applicazione.
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * Aggiorna il servizio di intento FCM e i filtri di intento per le notifiche di evento `RECEIVE` e `REGISTRATION`:
  
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
  
2. Apri l'applicazione in Android Studio e aggiungi il file `google-services.json` alla directory root del modulo dell'applicazione.

3. Inizializza il core SDK e il Push SDK. 

Un posto comune dove inserire il codice di inizializzazione è nel metodo onCreate() dell'attività principale nella tua applicazione Android:

```
// Inizializza l'SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Inizializza il Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... dove `<bluemixRegionSuffix>` è l'ubicazione in cui è ospitata l'applicazione. Puoi utilizzare uno qualsiasi dei seguenti valori:

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID è il valore GUID dell'applicazione push e clientSecret è il valore del segreto client push. 

## Passo 3: registra il tuo dispositivo Android con la tua istanza {{site.data.keyword.mobilepushshort}}

1. Esegui la tua applicazione.

2. Utilizza l'API MFPPush.register() per registrare il tuo dispositivo per abilitare le notifiche basate sull'utente.

```
//Registra il dispositivo per l'istanza del servizio Push Notifications
 push.registerDeviceWithUserId("userId",new MFPPushResponseListener<String>() {
 @Override	
 public void onSuccess(String response) {
 //Gestisci esiti positivi qui
 }
 @Override
    public void onFailure(MFPPushException ex) {
 //Gestisci esiti negativi qui
 }
 });
 ```
 {: codeblock}
 
 
 userId viene utilizzato per trasmettere il valore ID utente univoco per la registrazione delle notifiche push. Assicurati di fornire anche il valore clientSecret.
 {: tip}
 
 ## Passo 4: invia una notifica push di base
 
 1. Nella console {{site.data.keyword.Bluemix_notm}} passa al dashboard della tua istanza del servizio.
 2. Fai clic su **Gestisci > Invia notifiche**.
 3. Seleziona Dispositivi Android dal menu **Invia a**.
 4. Immetti il tuo messaggio e fai clic su **Invia**. 
 
