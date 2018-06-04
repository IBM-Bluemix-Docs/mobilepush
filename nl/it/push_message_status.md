---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Stato di consegna del messaggio 
{: #tag_based_notifications}
Ultimo aggiornamento: 21 agosto 2017
{: .last-updated}


Con il servizio {{site.data.keyword.mobilepushshort}}, puoi visualizzare lo stato di consegna di ogni notifica che è stata inviata al servizio. 

Una volta che il messaggio è stato inviato, puoi tracciare le informazioni di consegna di un messaggio controllando il suo stato di consegna. Per ogni punto temporale, il servizio visualizza lo stato soltanto degli ultimi 10 messaggi disponibili in un periodo di 90 giorni.

La scheda **Messaggi** del servizio {{site.data.keyword.mobilepushshort}} visualizza lo stato della notifica.

![stato notifiche](images/notification_status_new.png)

1. **ID messaggio** -  un identificativo univoco per identificare un messaggio.

2. **Testo messaggio** - un modello del messaggio che è stato inviato agli utenti dell'applicazione.

3. **Data** - la data e l'ora in cui è stato inviato il messaggio al servizio.

4. **Stato** - fornisce un breve riepilogo dello stato di un messaggio. A seconda dello stato del messaggio, potresti visualizzare uno dei seguenti stati:

 - Accettato: il messaggio è stato accettato per la consegna dal servizio Push Notifications.
   
 - In distribuzione: la notifica è stata ricevuta dal provider di notifica - APNs, FCM o Web e sta per essere distribuito. Una notifica che sta per essere distribuita può anche restituire un errore con lo stato **Distribuzione non riuscita**.
 
 - Distribuito: la notifica è stata distribuita dal provider di notifica.
 
 - In elaborazione: il messaggio sta venendo elaborato, per essere distribuito al gateway del provider di notifica. Una notifica che sta venendo elaborata può anche restituire un errore con lo stato **Elaborazione non riuscita**.
 
 - Sconosciuto: lo stato della notifica non può essere determinato.
 
5. **Visualizza** - Visualizza lo stato di consegna delle notifiche che vengono distribuite. Puoi visualizzare le informazioni in base ai seguenti aspetti:

 - Categoria: Tutto, Mobile, Web<!---and HTTP--->.
 
 - Stato messaggio: Inviato, Visualizzato, Aperto e Non valido. 

![stato notifiche](images/message_delivery_status_new.png)

6. **Opzioni** - Fornisce uno stato dettagliato di una notifica. Lo stato può essere tracciato selezionando l'`ID dispositivo` o l'`ID utente` dal menu a discesa. L'ottenimento del messaggio di stato dettagliato specifico per dispositivo/utente può essere utile quando stai tracciando un messaggio di errore.

![stato dettagliato](images/detailed_message_delivery.png)

**Nota**: la funzione è abilitata solo per gli utenti che hanno scelto il `Piano avanzato`. Seleziona **Piano** nella console del servizio {{site.data.keyword.mobilepushshort}} per l'[upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)


