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


# FAQ 
{: #faq}

### Perché i miei token sono stati invalidati?
{: #faq-tokens}	

Per le registrazioni del dispositivo, del browser, delle applicazioni Chrome e delle estensioni, il servizio Push Notifications conserva un riferimento univoco ai token emessi dai provider di notifica - APNs per Apple o FCM per Google. I token possono essere annullati dal provider di notifica del servizio per molti motivi. 

Ad esempio, durante la disinstallazione dell'applicazione sul dispositivo. In questo scenario, quando viene tentato l'invio di una notifica in base ai provider, la risposta del dispositivo viene annullata, il servizio {{site.data.keyword.mobilepushshort}} rimuoverà le registrazioni del dispositivo o del browser web. Ciò impedirà i seguenti tentativi di invio della notifica ai dispositivi annullati. 

Potresti inoltre riscontrare il problema se stai annullando la registrazione di un dispositivo.

Assicurati di disporre di un ID mittente e di una chiave API server per continuare. Consulta [Ottieni le tue credenziali del provider della notifica](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1).

### Perché ricevo il messaggio *La notifica non funziona per WEB_Chrome.*, quando provo ad inizializzare l'SDK di push web?
{: #faq-web-chrome}	

Potresti aver modificato le tue credenziali FCM per l'SDK di push web e la ricezione dei messaggi potrebbe non riuscire per il browser Chrome. Assicurati di richiamare *bmsPush.unRegisterDevice* per evitare errori.

### Ricevo il messaggio *I nodi di lavoro del servizio non sono supportati in questo browser* quando provo ad inizializzare l'SDK per il push web. Quale potrebbe essere il problema? 
{: #faq-service-workers}	

Segui le istruzioni menzionate in [Passo 3: configura l'SDK client del servizio push](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3). Assicurati inoltre che:

1. Stai utilizzando il metodo di avvio corretto. 
2. Includi il file `manifest.json` nella cartella root.
3. Ospiti il tuo sito web. Hai preferibilmente creato uno starter `node.js` in IBM Cloud per provarlo. Ad esempio: https://<mysamplewebsite>.cloud.ibm.com/.	

### Come posso risolvere gli errori di configurazione web del push web?
{: #faq-web-config-errors}	

Gli errori push web dal `BMSPushSDK.js` contengono informazioni sull'errore. Consulta [Risoluzione dei problemi](/docs/services/mobilepush?topic=mobile-pushnotification-errors).	

### Le notifiche vengono conservate se i dispositivi sono offline?
{: #faq-notification-persist}	

Questa funzione dipende dal provider di notifica.	

### messageID è univoco per un'applicazione e quale ne è la dimensione?
{: #faq-messageid}	

messageID è univoco per un'applicazione ed è limitato a otto caratteri. Può essere alfanumerico.

### Quali sono i limiti per le notifiche push, in termini di dimensione del payload?
{: #faq-limits-push-payload-size}	

La dimensione del payload del messaggio di {{site.data.keyword.mobilepushshort}} dipende dai vincoli disposti dai gateway (FCM, APNs) e dalle piattaforme client. 

Per iOS 8 e successivi, la dimensione massima consentita è 4 kilobyte. Tieni presente che le APNs non inviano notifiche che superano questo limite. Per Android, i browser Firefox e Chrome e le estensioni e applicazioni Chrome, esiste una limitazione di 4 kilobyte come massimo consentito per la dimensione del payload del messaggio.	

### Le notifiche inviate vengono archiviate nei server BMS?
{: #faq-bms-servers}	

Sì, le notifiche vengono archiviate per un periodo di novanta giorni. Ti raccomandiamo di non inviare alcun messaggio confidenziale come notifica.

### Posso inviare una notifica ai dispositivi nella modalità Doze?
{: #faq-doze-mode}	

Questa funzione non è supportata.	

### Quali sono i differenti piani dei prezzi disponibili per il servizio Push Notifications?
{: #faq-pricing-plans}	

* <b>Piano avanzato</b>: disponibile per $100.00 USD/Istanza, $0.50 USD/Milione di messaggi digitali e $0.50 USD/Milione di dispositivi indirizzabili. Con il piano avanzato, puoi inviare le notifiche push a 1 milione di dispositivi indirizzabili e 100 milioni di messaggi digitali. Il piano avanzato include funzionalità come Impostazione parametri dei messaggi e Traccia del ciclo di vita del messaggio end-to-end.

* <b>Piano di base</b>: è disponibile per $1.00 USD/Milione di messaggi digitali. Con il piano di base, puoi inviare le notifiche push a un solo dispositivo, browser, endpoint o a un evento basato su un webhook. 

* <b>Piano Lite</b>: è un piano gratuito che fornisce centomila messaggi digitali gratuiti al mese. Tuttavia, i servizi del piano Lite vengono eliminati dopo 30 giorni di inattività.	

### Dove posso trovare ulteriori informazioni come le esercitazioni o le novità?
{: #faq-what-is-new}	

Vai ai [video](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA) del servizio Push Notifications.	

### Esiste una differenza tra una notifica e un messaggio?
{: #faq-diff-notification-message}	

Sì. Un _messaggio_ è il contenuto di cosa l'utente sta inviando al servizio {{site.data.keyword.mobilepushshort}}. Il servizio lo invia come una _notifica_ al gateway di notifica (APNs/FCM) e viene distribuito al dispositivo o al browser web.

Per ogni messaggio che invii al servizio, i destinatari previsti ricevono una notifica.	

### Il dashboard di monitoraggio di Push Notifications visualizza tutti gli stati dei messaggi inviati?
{: #faq-push-monitor-dashboard}	

Il programma di utilità di monitoraggio visualizza lo stato di ogni messaggio inviato. Il messaggio potrebbe essere nel seguente stato:
	
* Inviato: il numero di dispositivi a cui è stata inviata la notifica.
* Visualizzato: il numero di dispositivi che hanno ricevuto la notifica.
* Aperto: il numero di dispositivi in cui la notifica è stata aperta.
* Non valido: il numero di dispositivi in cui il token non è valido.

Per ulteriori informazioni, vedi il report dei messaggi GET in [IBM Push Notifications REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).	

### La notifica push monitora la consegna al dispositivo dell'utente finale? Sia per Android che per iOS?
{: #faq-end-user-device}	

Le notifiche push sono monitorate in base al numero di notifiche visualizzate o aperte dal dispositivo dell'utente finale. È disponibile sia per Android che per iOS. Il monitoraggio basato sull'ID del dispositivo non è supportato. 

### Ricevo un messaggio che il server non è attualmente in grado di gestire le richieste? Come posso risolverlo?
{: #faq-server-unable-to-handle-requests}	

Potresti visualizzare l'errore con il codice FPWSE0025E. Potrebbe essere dovuto al fatto che il server gestisce troppe richieste. Puoi tentare di reinviare la richiesta in un secondo momento.	

### Sto inviando la notifica per tag, ma ho un elenco molto lungo di tag che potrebbe essere difficile aggiungere manualmente. 
{: #faq-tag-based-notification}	

Puoi utilizzare le API REST per automatizzare l'aggiunta di tag. Consulta [POST bulk messages](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).

### Come posso filtrare la consegna delle notifiche push per le informazioni archiviate nel dispositivo mobile dell'utente?
{: #faq-filter-device}	

Questo dovrebbe essere gestito nel contesto di sviluppo dell'applicazione.

### Posso personalizzare il monitoraggio della notifica push per aggiungere un report personalizzato come il report di consegna per segmentazione?
{: #faq-customize-delivery-report}	

Questa funzione non è supportata.

### Posso creare un segmento per utenti della nuova applicazione a cui non hanno eseguito l'accesso per un breve periodo di tempo?
{: #faq-create-segment}	

Questo dovrebbe essere gestito nel contesto di sviluppo dell'applicazione.
	
### Posso registrare/aggiornare i dispositivi mobili in blocco tramite le API REST?
{: #faq-register-mobile-devices}	

Come da progettazione, la registrazione/l'aggiornamento di un dispositivo viene richiamato dalle applicazioni mobili tramite l'SDK. Le registrazioni/gli aggiornamenti in blocco tramite le API REST non sono supportati. Se molti aggiornamenti/registrazioni vengono richiamati contemporaneamente utilizzando le API REST, potrebbe essere necessario molto tempo o potrebbero avere esito negativo.	

### Come invio le notifiche push o utilizzo le API REST quando non dispongono dell'appSecret?
{: #faq-rest-api-appsecret}	

Dal momento che il servizio {{site.data.keyword.mobilepushshort}} ha iniziato ad utilizzare IAM, viene visualizzata un'`apiKey` invece dell'`appSecret` quando l'utente crea le credenziali del servizio.

Per utilizzare tutte le API REST, devi generare il token di accesso tramite il seguente comando curl:

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

Nel momento in cui generi il token di accesso tramite il precedente comando curl, puoi utilizzare le API REST passando `Bearer <value of access_token>` nell'intestazione dell'autorizzazione.

Ad esempio:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
