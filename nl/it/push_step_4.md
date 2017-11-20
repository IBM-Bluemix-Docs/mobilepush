---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Passo 5: invio di una notifica
{: #push_step_4}
Ultimo aggiornamento: 27 giugno 2017
{: .last-updated}


Dopo che hai sviluppato le tue applicazioni, puoi inviare delle notifiche di push di base.

Per inviare notifiche di push di base, completa la seguente procedura:

1. Seleziona **Send Notifications** e componi un messaggio scegliendo l'opzione **Send to**. Le opzioni supportate sono **Device by Tag**, **Device Id**, **User Id**, **Android devices**, **iOS devices**, **Web Notifications** e **All Devices**.
**Nota**: quando selezioni l'opzione **All Devices**, tutti i dispositivi sottoscritti a {{site.data.keyword.mobilepushshort}} riceveranno le notifiche.
	
	![Schermata notifiche](images/tag_notification.jpg)

2. Nel campo **Message**, componi il messaggio. Scegli di configurare le impostazioni facoltative come richiesto.
3. Fai clic su **Send**.
3. Verifica che i tuoi dispositivi abbiano ricevuto la notifica.

Il seguente screenshot mostra una casella di avviso che gestisce una notifica push
in primo piano su un dispositivo Android.
	![Notifica push in primo piano su Android](images/Android_Screenshot.jpg)

Il seguente screenshot mostra una notifica push in background per Android.
	![Notifica push in background su Android](images/background.jpg)

## Impostazioni Android facoltative 
{: #push_step_4_Android}

Puoi anche personalizzare le impostazioni di {{site.data.keyword.mobilepushshort}} per inviare le notifiche ai dispositivi Android. 

![Impostazioni personalizzate Android](images/android_custom_settings.jpg)

Sono supportate le seguenti opzioni di personalizzazione facoltative:

- Chiave di compressione:  le chiavi di compressione solo allegate alle notifiche. Se più notifiche arrivano in sequenza con la stessa chiave di compressione quando il dispositivo è offline, esse vengono compresse. Quando un dispositivo va online, riceve le notifiche dal server FCM/GCM e visualizza solo l'ultima notifica rilevando la stessa chiave di compressione. Se la chiave di compressione non viene inviata, sia il nuovo che il vecchio messaggio vengono archiviati per una consegna successiva.
- Audio: indica un file audio da riprodurre alla ricezione di una notifica. Supporta il valore predefinito o il nome di una risorsa audio integrata nell'applicazione.
- Icona: specifica il nome dell'icona da visualizzare per la notifica. Assicurati di aver fornito l'icona nella cartella `res/drawable`, insieme all'applicazione client.
- Priorità: specifica le opzioni per l'assegnazione della priorità di consegna dei messaggi. 
	- Una priorità `high` o `max` creerà una notifica di avviso.
	- Una priorità `low` o `default` non aprirà le connessioni di rete in un dispositivo silenzioso. 
- Visibilità: puoi scegliere di impostare l'opzione di visibilità della notifica su `public` o `private`. 
	- L'opzione `private` limita la visualizzazione pubblica e puoi scegliere di abilitarla se il tuo dispositivo è protetto da un pattern o un pin e l'impostazione di notifica è impostata su **Hide sensitive notification content**. Quando la visibilità è impostata su `private`, è necessario menzionare un campo `redact`. Solo il contenuto specificato nel campo `redact` sarà visualizzato nella schermata di blocco sicura nel dispositivo. 
	- L'opzione `public` renderà possibile leggere le notifiche liberamente.
- TTL (Time to live): questo valore è impostato in secondi. Se questo parametro non viene specificato, il server FCM/GCM archivia il messaggio per quattro settimane e tenterà di consegnarlo. La validità scade dopo quattro settimane. L'intervallo di valori possibile è compreso tra 0 e 2,419,200 secondi.
- Ritarda quando inattivo: puoi impostare questa proprietà su uno dei seguenti valori:
	- `True` indica al server FCM/GCM di non consegnare la notifica se il dispositivo è inattivo. 
	- `False` assicura di consegnare la notifica anche se il dispositivo è inattivo.
- Sincronizzazione: impostando questa opzione su `true`, le notifiche vengono sincronizzate in tutti i tuoi dispositivi registrati. Se l'utente con un nome utente dispone di più dispositivi con la stessa applicazione installata, la lettura della notifica su un dispositivo assicura l'eliminazione delle notifiche negli altri dispositivi. Devi assicurarti di essere registrato con il servizio {{site.data.keyword.mobilepushshort}} con l'ID utente per questa opzione perché funzioni.
- Payload addizionale: specifica i valori di payload personalizzati per le tue notifiche.
- Notifica espandibile: fornisce ai clienti un'opzione per espandere una notifica con ulteriori informazioni, mentre una notifica di base sarà visualizzabile con la notifica compressa. Sono supportate le seguenti opzioni:
	- Notifiche di immagini di grandi dimensioni: puoi scegliere di includere un'immagine quando la notifica viene espansa. Assicurati di fornire un testo nel titolo e l'URL dell'immagine.
	- Notifiche di testo di grandi dimensioni: puoi scegliere di includere ulteriore testo con un titolo. Assicurati il messaggio di testo di grandi dimensioni e le informazioni sul testo del titolo siano forniti.
	- Notifiche di stile di posta in arrivo: puoi inviare la notifica nello stile di una notifica della posta in arrivo. Fornisci un test del titolo e il messaggio nelle righe.	 

## Impostazioni iOS facoltative 
{: #push_step_4_ios}

Puoi personalizzare le impostazioni di {{site.data.keyword.mobilepushshort}} per inviare le notifiche ai dispositivi iOS. Sono supportate le seguenti opzioni di personalizzazione facoltative.

- **Badge**:  indica il numero che viene visualizzato nel badge dell'applicazione. Il valore predefinito è zero (0) e ciò significa che non sarà visualizzato un badge. 
- **Audio**: indica un file audio da riprodurre al ricevimento di un notifica. Supporta il valore predefinito o il nome della risorsa audio integrata nell'applicazione.
- **Payload addizionale**: specifica i valori di payload personalizzati per le tue notifiche.

Puoi anche scegliere di abilitare le [notifiche interattive](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications) e le [notifiche delle risorse multimediali](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications).

## Monitoraggio delle notifiche distribuite 
{: #push_step_4_monitor}

Il servizio {{site.data.keyword.mobilepushshort}} fornisce un programma di utilità di monitoraggio per aiutarti a verificare lo stato dei messaggi che vengono inviati. Per configurare il tuo programma di utilità di monitoraggio, utilizza una delle seguenti opzioni:

- [Enable monitoring for Android applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
- [Enable monitoring for iOS applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
