---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifiche basate sull'utente
{: #user_based_notifications}
Ultimo aggiornamento: 22 maggio 2017
{: .last-updated}

Le {{site.data.keyword.mobilepushshort}} basate su ID utente sono destinate agli utenti dell'applicazione mobile con messaggi personalizzati. Con le notifiche basate sull'utente, puoi scegliere di inviare la notifica a delle persone specifiche in base alle rispettive preferenze.

## Registrazione del dispositivo con l'ID utente
{: #register_device_wh_userid}

Per abilitare le notifiche di push indirizzate dall'ID utente, assicurati di aver registrato il dispositivo con un campo ID utente impostato.     

L'ID utente può essere una qualsiasi stringa fornita dall'applicazione all'API di registrazione del dispositivo. Normalmente, un'applicazione mobile prima eseguirà un ciclo di autenticazione in cui l'utente dell'applicazione mobile viene autenticato in un servizio di autenticazione come [{{site.data.keyword.amafull}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/docs/services/mobileaccess/index.html){: new_window}. Dopo la corretta autenticazione, l'ID dell'utente autenticato viene trasmesso all'API Push Device Registration. 

Per registrare la notifica basate sull'ID utente, utilizza:

- [Registering an Android application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [Registering an iOS application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Registering a Cordova application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Registering a web application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## Utilizzo delle notifiche basate sull'ID utente
{: #using_userid}

Le notifiche basate sull'ID utente sono messaggi di notifica destinati a uno specifico utente. Possono essere registrati con un utente molti dispositivi. I seguenti passi descrivono come inviare le notifiche basate sull'ID utente.

1. Dalla console **Push Notification**, seleziona l'opzione **Send Notifications**.
1. Seleziona **UserId** nell'elenco delle opzioni **Send to**.
1. Nel campo **User Id**, cerca gli ID utente che vuoi utilizzare e fai quindi clic su **+Add**.![Schermata notifiche](images/user_notification.jpg)
1. Nel campo **Message**, immetti il testo che vuoi inviare nella tua notifica.
1. Fai clic su **Send**.


## Sincronizzazione di accesso/disconnessione dell'utente 
{: #sync_login_logout}

Puoi scegliere di inviare le notifiche solo se l'utente ha effettuato l'accesso. 

Ad esempio, prendi in considerazione un dispositivo condiviso dai membri di un team di lavoro e che ci sia bisogno di indirizzare utenti specifici. In questo caso di utilizzo, dovrebbe esserci una sequenza di accesso e disconnessione utente. Questo meccanismo di autenticazione consente all'applicazione di tracciare l'identità dell'utente presente dell'applicazione. Questo assicura che le notifiche destinate a un'utente specifico siano sempre ricevute solo da tale utente. Dopo un accesso corretto, richiama l'API di registrazione del dispositivo trasmettendo l'ID utente dell'utente che ha eseguito l'accesso. Allo stesso modo, prima della disconnessione, richiama l'API `unregistration` del dispositivo. La sequenza di queste API push con accesso e disconnessione ti assicurerà che le notifiche pensate per un utente specifico siano inviate solo a tale utente.
