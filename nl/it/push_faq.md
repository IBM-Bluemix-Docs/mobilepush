---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Domande frequenti (FAQ) 
{: #faq}


1. Perché i miei token sono stati invalidati?
	
	Per le registrazioni del dispositivo, del browser, delle applicazioni Chrome e delle estensioni, il servizio Push Notifications conserva un riferimento univoco ai token emessi dai provider di notifica - APNs per Apple o FCM per Google. I token possono essere annullati dal provider di notifica del servizio per molti motivi.  

	Ad esempio, durante la disinstallazione dell'applicazione sul dispositivo. In questo scenario, quando viene tentato l'invio di una notifica in base ai provider, la risposta del dispositivo viene annullata, il servizio {{site.data.keyword.mobilepushshort}} rimuoverà le registrazioni del dispositivo o del browser web. Ciò impedirà i seguenti tentativi di invio della notifica ai dispositivi annullati. 

	Potresti inoltre riscontrare il problema se stai annullando la registrazione di un dispositivo.

	Assicurati di disporre di un ID mittente e di una chiave API server per continuare. Consulta [Ottieni le tue credenziali del provider della notifica](push_step_1.html).


2. Perché ricevo "La notifica non funziona per WEB_Chrome.", quando provo ad inizializzare l'SDK di push web?

	Potresti aver modificato le tue credenziali FCM/GCM per l'SDK di push web e la ricezione dei messaggi potrebbe non riuscire per il browser Chrome. Assicurati di richiamare "bmsPush.unRegisterDevice" per evitare errori.

3. Ricevo il messaggio "I worker del servizio non sono supportati in questo browser" quando provo ad inizializzare l'SDK per il push web. Quale potrebbe essere il problema? 

	Segui le istruzioni menzionate in [Passo 3: configura l'SDK client del servizio push](push_step_3.html).	Assicurati inoltre che:
 
	1. Stai utilizzando il metodo di avvio corretto. 
	1. Includi il file `manifest.json` nella cartella root.
	1. Ospiti il tuo sito web. Hai preferibilmente creato uno starter `node.js` in Bluemix per provarlo. Ad esempio: https://<mysamplewebsite>.mybluemix.net/.	

4. Come posso risolvere gli errori di configurazione web del push web?

	Gli errori push web dal `BMSPushSDK.js` contengono informazioni sull'errore.  Consulta [Risoluzione dei problemi](push_troubleshooting.html).	

5. Le notifiche vengono conservate se i dispositivi sono offline?

	Questa funzione dipende dal provider di notifica.	

6. messageID è univoco per un'applicazione e quale ne è la dimensione?

	messageID è univoco per un'applicazione ed è limitato a otto caratteri. Può essere alfanumerico.

7. Quali sono i limiti per le notifiche push, in termini di dimensione del payload?

	La dimensione del payload del messaggio di {{site.data.keyword.mobilepushshort}} dipende dai vincoli disposti dai gateway (FCM/GCM, APNs) e dalle piattaforme client. 

	Per iOS 8 e successivi, la dimensione massima consentita è 2 kilobyte. Tieni presente che le APNs non inviano notifiche che superano questo limite. Per Android, i browser Firefox e Chrome e le estensioni e applicazioni Chrome, esiste una limitazione di 4 kilobyte come massimo consentito per la dimensione del payload del messaggio. 	

8. Le notifiche inviate vengono archiviate nei server BMS?

	Sì, le notifiche vengono archiviate per un periodo di sette giorni. Ti raccomandiamo di non inviare alcun messaggio confidenziale come notifica.

9. Posso inviare una notifica ai dispositivi nella modalità Doze?

	Questa funzione non è supportata.	

10. Quali sono i differenti piani dei prezzi disponibili per il servizio Push Notifications?

	**Piano di base**: è disponibile per $1.00 USD/Milione di messaggi digitali. Con il piano di base, puoi inviare le notifiche push a un solo dispositivo, browser, endpoint o a un evento basato su un webhook. 

		
	**Piano Lite**: è un piano gratuito che fornisce centomila messaggi digitali gratuiti al mese. Tuttavia, i servizi del piano Lite vengono eliminati dopo 30 giorni di inattività.	

11. Dove posso trovare ulteriori informazioni come le esercitazioni o le novità?

	Vai al [blog](http://push-notification-service.mybluemix.net/) del servizio Push Notifications.	

12. Esiste una differenza tra una notifica e un messaggio?

	Sì. Un _messaggio_ è il contenuto di cosa l'utente sta inviando al servizio {{site.data.keyword.mobilepushshort}}. Il servizio lo invia come una _notifica_ al gateway di notifica (APNs/FCM) e viene distribuito al dispositivo o al browser web.

	Per ogni messaggio che invii al servizio, i destinatari previsti ricevono una notifica.	

13. Il dashboard di monitoraggio di Push Notifications visualizza tutti gli stati dei messaggi inviati?

	Il programma di utilità di monitoraggio visualizza lo stato di ogni messaggio inviato. Il messaggio potrebbe essere nel seguente stato:

	- Inviato: il numero di dispositivi a cui è stata inviata la notifica.
	- Visualizzato: il numero di dispositivi che hanno ricevuto la notifica.
	- Aperto: il numero di dispositivi in cui la notifica è stata aperta.
	- Non valido: il numero di dispositivi in cui il token non è valido.

	Per ulteriori informazioni, vedi il report dei messaggi GET in [IBM Push Notifications REST API](https://mobile.ng.bluemix.net/imfpush/).	

14. La notifica push monitora la consegna al dispositivo dell'utente finale? Sia per Android che per iOS?

	Le notifiche push sono monitorate in base al numero di notifiche visualizzate o aperte dal dispositivo dell'utente finale. È disponibile sia per Android che per iOS. Il monitoraggio basato sull'ID del dispositivo non è supportato. 

15. Ricevo un messaggio che il server non è attualmente in grado di gestire le richieste? Come posso risolverlo?

	Questo potrebbe essere soltanto un problema temporaneo. Reinvia la richiesta in un secondo momento. 	

16. Sto inviando la notifica per tag, ma ho un elenco molto lungo di tag che potrebbe essere difficile aggiungere manualmente. 
	
	Puoi utilizzare le API REST per automatizzare l'aggiunta di tag. Consulta [POST bulk messages](https://mobile.ng.bluemix.net/imfpush/).

17. Come posso filtrare la consegna delle notifiche push per le informazioni archiviate nel dispositivo mobile dell'utente?

	Questo dovrebbe essere gestito nel contesto di sviluppo dell'applicazione.

18. Posso personalizzare il monitoraggio della notifica push per aggiungere un report personalizzato come il report di consegna per segmentazione?

	Questa funzione non è supportata.

19.  Posso creare un segmento per utenti della nuova applicazione a cui non hanno eseguito l'accesso per un breve periodo di tempo?

	Questo dovrebbe essere gestito nel contesto di sviluppo dell'applicazione.

20. Ricevo l'errore che il "server non è attualmente in grado di gestire la richiesta".

	Potresti visualizzare l'errore con il codice FPWSE0025E. Potrebbe essere dovuto al fatto che il server gestisce troppe richieste. Puoi tentare di reinviare la richiesta in un secondo momento.




	


	
	




	


