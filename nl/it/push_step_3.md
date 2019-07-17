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

# Passo 4: configura l'SDK client del servizio
{: #push_step_3}

Assicurati di aver [ottenuto le tue credenziali del servizio](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) e aver [configurato un'istanza del servizio push](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2). Devi quindi configurare l'applicazione per utilizzare il servizio Push Notifications per registrare, sottoscrivere e ricevere le notifiche push. 

Per configurare l'SDK client del servizio, utilizza i seguenti passi in base al tuo tipo di applicazione.

## Nelle applicazioni Android
{: #push_step_3_Android}

Puoi abilitare le applicazioni Android a ricevere le notifiche di push ai tuoi dispositivi. Android Studio è un prerequisito ed è il metodo raccomandato per creare progetti Android. La conoscenza di base di Android Studio è fondamentale.

Assicurati di aver consultato [Ottieni le tue credenziali del provider della notifica](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) per configurare il progetto FCM e ottenere le tue credenziali.

Completa le istruzioni in [SDK Android Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) per abilitare le applicazioni Android a ricevere le notifiche push inviate dal servizio. 

1. Apri l'applicazione in Android Studio. Copia il file `google-services.json` che hai creato al [Passo 2: ottieni le tue credenziali](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) nella directory root del modulo della tua applicazione Android. Nota che il file `google-service.json` include i nomi dei pacchetti aggiunti.

    ![Aggiunta del file json alla directory root della tua applicazione](images/FCM_7.jpg "Aggiunta del file json alla directory root della tua applicazione")

2. Nella finestra Aggiungi Firebase alla tua applicazione Android, fai clic su **Continua** e quindi su **Fine**. 
3. Crea ed esegui la tua applicazione. Dopo una corretta creazione, dovrebbe essere visualizzato il messaggio `Build Gradle terminata`.
4. Includi il Push SDK client con Gradle
	1. Configura il tuo file [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle). 
	2. Configura il file [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest).
	3. Aggiungi il file `google-services.json` nella directory root del modulo della tua applicazione Android.
5. Inizializza le SDK. Consulta [Initializing the Core SDK and the Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
6. Crea l'applicazione.
7. Puoi scegliere di eseguire la registrazione al servizio Push Notifications facendo clic sul pulsante Registra dispositivo sull'applicazione o tramite [Registering to the service using the Push Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

Il tuo prossimo passo è di [Inviare una notifica](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Nelle applicazioni Cordova
{: #push_step_3_Cordova}

Cordova è una piattaforma per creare applicazioni ibride con JavaScript, CSS e HTML. Il servizio Push Notifications supporta lo sviluppo di applicazioni Android e iOS basate su Cordova.

Per abilitare le applicazioni Cordova a ricevere le notifiche di push ai tuoi dispositivi, devi configurare [Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

Dopo aver configurato Cordova Plugin Push SDK, il tuo prossimo passo è di [Inviare una notifica](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Nelle applicazioni iOS
{: #push_step_3_iOS}

Per abilitare le applicazioni iOS a ricevere {{site.data.keyword.mobilepushshort}} ai tuoi dispositivi, devi configurare [iOS SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

Dopo aver configurato iOS SDK, il tuo prossimo passo è di [Inviare una notifica](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Nei browser web
{: #push_step_3_web}

Per abilitare le applicazioni browser a ricevere le notifiche push, devi configurare il [Servizio Web SDK for Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

Dopo aver configurato Web SDK, il tuo prossimo passo è di [Inviare una notifica](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

