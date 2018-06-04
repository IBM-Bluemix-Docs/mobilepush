---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Stato di consegna della notifica del messaggio
{: #tag_based_notifications}
Ultimo aggiornamento: 21 agosto 2017
{: .last-updated}


Con il servizio {{site.data.keyword.mobilepushshort}}, puoi visualizzare lo stato di ogni notifica che è stata inviata al servizio.  

Un messaggio che è stato inviato potrebbe avere il seguente stato:

- **Accettato**: il messaggio è stato accettato per la consegna dal servizio Push Notifications.
- **In elaborazione**: il messaggio sta venendo elaborato, per essere distribuito al gateway del provider di notifica. Una notifica che sta venendo elaborata può anche restituire un errore con lo stato **Elaborazione non riuscita**.
- **In distribuzione**: la notifica è stata ricevuta dal provider di notifica - APNs, FCM o Web e sta per essere distribuito. Una notifica che sta per essere distribuita può anche restituire un errore con lo stato **Distribuzione non riuscita**.
- **Distribuito**: la notifica è stata distribuita dal provider di notifica.
- **Sconosciuto**: lo stato della notifica non può essere determinato.

La scheda Messaggi del servizio {{site.data.keyword.mobilepushshort}} visualizza lo stato della notifica.

![stato notifiche](images/notification_status_new.png)

1. L'opzione **Visualizza** visualizza lo stato di consegna delle notifiche che vengono distribuite. Puoi visualizzare le informazioni in base ai seguenti aspetti:

 - Categoria: Tutto, Mobile, Web<!---and HTTP--->.
 - Stato messaggio: Inviato, Visualizzato, Aperto e Non valido. 

![stato notifiche](images/message_delivery_status_new.png)

2. Fai clic su **Opzioni** per ottenere lo **Stato di consegna del messaggio dettagliato**.  Uno stato di consegna dettagliato può essere tracciato selezionando l'`ID dispositivo` o l'`ID utente` dal menu a discesa. Può essere richiamato uno stato dettagliato per un utente o un dispositivo specifico.

![stato dettagliato](images/detailed_message_delivery.png)


Per ogni punto temporale, il servizio visualizza lo stato soltanto degli ultimi 10 messaggi disponibili in un periodo di 90 giorni. 

**Nota**: la funzione è abilitata solo per gli utenti che hanno scelto il `Piano dei prezzi avanzato`. Seleziona **Piano** nella console del servizio {{site.data.keyword.mobilepushshort}} per l'[upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)
