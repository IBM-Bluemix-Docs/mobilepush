---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Passo 3: configura l'SDK client del servizio
{: #push_step_3}
Ultimo aggiornamento: 12 giugno 2017
{: .last-updated}

Assicurati di aver [ottenuto le tue credenziali del servizio](push_step_1.html) e aver [configurato un'istanza del servizio push](push_step_2.html). Devi quindi configurare l'applicazione per utilizzare il servizio Push Notifications per registrare, sottoscrivere e ricevere le notifiche push. 

Per configurare l'SDK client del servizio, utilizza i seguenti passi in base al tuo tipo di applicazione.

## Nelle applicazioni Android
{: #push_step_3_Android}

Puoi abilitare le applicazioni Android a ricevere le notifiche di push ai tuoi dispositivi. Android Studio è un prerequisito ed è il metodo raccomandato per creare progetti Android. La conoscenza di base di Android Studio è fondamentale.

Assicurati di aver consultato [Ottieni le tue credenziali del provider della notifica](push_step_1.html) per configurare il progetto FCM e ottenere le tue credenziali.

Completa le istruzioni in [SDK Android Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) per abilitare le applicazioni Android a ricevere le notifiche push inviate dal servizio. 

Completa la seguente procedura utilizzando la console FCM (Firebase Cloud Messaging).

1. Nella console Firebase, fai clic sull'icona **Impostazioni progetto**.
    
	![Impostazioni progetto Firebase](images/FCM_settings_6.jpg)

3. Seleziona **AGGIUNGI APPLICAZIONE** o l'icona **Aggiungi Firebase alla tua applicazione Android** dalla scheda Generale nel pannello Tue applicazioni.
    
4. Nella finestra Aggiungi Firebase alla tua applicazione Android, aggiungi **com.ibm.mobilefirstplatform.clientsdk.android.push** come nome pacchetto. Il campo Nome alternativo applicazione è facoltativo. Fai clic su **AGGIUNGI APPLICAZIONE**. 
    
	![Aggiunta di Firebase alla tua finestra Android](images/FCM_1.jpg)

5. Includi il nome pacchetto della tua applicazione immettendolo nella finestra Aggiungi Firebase alla tua applicazione Android. Il campo Nome alternativo applicazione è facoltativo. Fai clic su **REGISTRA APPLICAZIONE**. 

	![Aggiunta del nome del pacchetto alla tua applicazione](images/FCM_settings_4.jpg)

6. Viene generato il file `google-services.json`. 
7. Apri l'applicazione in Android Studio. Copia il file `google-services.json` nella directory root del modulo della tua applicazione Android. Nota che il file `google-service.json` include i nomi dei pacchetti aggiunti.

    ![Aggiunta del file json alla directory root della tua applicazione](images/FCM_7.jpg)

5. Nella finestra Aggiungi Firebase alla tua applicazione Android, fai clic su **Continua** e quindi su **Fine**. 
6. Crea ed esegui la tua applicazione. Dopo una corretta creazione, dovrebbe essere visualizzato il messaggio `Build Gradle terminata`.
7. Includi il Push SDK client con Gradle
	1. Configura il tuo file [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle). 
	1. Configura il file [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest).
	1. Aggiungi il file `google-services.json` nella directory root del modulo della tua applicazione Android. 
9. Inizializza le SDK. Consulta [Initializing the Core SDK and the Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
10. Crea l'applicazione.
11. Puoi scegliere di eseguire la registrazione al servizio Push Notifications facendo clic sul pulsante Registra dispositivo sull'applicazione o tramite [Registering to the service using the Push Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

Il tuo prossimo passo è di [Inviare una notifica](push_step_4.html).


## Nelle applicazioni Cordova
{: #push_step_3_Cordova}

Cordova è una piattaforma per creare applicazioni ibride con JavaScript, CSS e HTML. Il servizio Push Notifications supporta lo sviluppo di applicazioni Android e iOS basate su Cordova. 

Per abilitare le applicazioni Cordova a ricevere le notifiche di push ai tuoi dispositivi, devi configurare [Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

Dopo aver configurato Cordova Plugin Push SDK, il tuo prossimo passo è di [Inviare una notifica](push_step_4.html). 


## Nelle applicazioni iOS
{: #push_step_3_iOS}

Per abilitare le applicazioni iOS a ricevere {{site.data.keyword.mobilepushshort}} ai tuoi dispositivi, devi configurare [iOS SDK for Push Notifications service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

Dopo aver configurato iOS SDK, il tuo prossimo passo è di [Inviare una notifica](push_step_4.html).


## Nei browser web
{: #push_step_3_web}

Per abilitare le applicazioni browser a ricevere le notifiche push, devi configurare il [Servizio Web SDK for Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

Dopo aver configurato Web SDK, il tuo prossimo passo è di [Inviare una notifica](push_step_4.html).
