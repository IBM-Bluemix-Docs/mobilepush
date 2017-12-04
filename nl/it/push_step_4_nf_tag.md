---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifiche basate sulle tag
{: #tag_based_notifications}
Ultimo aggiornamento: 30 giugno 2017
{: .last-updated}

Le notifiche basate sulle tag sono messaggi destinati a tutti i dispositivi sottoscritti a una particolare tag. Le notifiche basate sulle tag
                        consentono la segmentazione di notifiche sulla base di argomenti o di aree
                        oggetto. I destinatari della notifica possono scegliere di ricevere le notifiche solo
                        se sono relative a un oggetto o a un argomento a cui sono interessati. Pertanto,
                        la notifica basata sulle tag fornisce un mezzo per segmentare i destinatari. Questa funzione
                        consente di definire delle tag e quindi di inviare e ricevere messaggi in
                        base alle tag. Un messaggio viene indirizzato solo alle istanze dell'applicazione client (mobili, browser o come un'applicazione o estensioni) sottoscritte a una tag. Devi prima creare le tag per l'applicazione, impostare le sottoscrizioni di tag e iniziare quindi le notifiche basate sulle tag. Per inviare una notifica basata sulle tag che utilizza la API REST, assicurati che i "tagName" siano forniti all'inserimento nella risorsa messaggi.

Puoi definire le tag e quindi utilizzarle per
                        inviare e ricevere messaggi. Devi prima creare le tag per l'applicazione, creare le sottoscrizioni di tag e iniziare quindi le notifiche basate sulle tag. Per inviare una notifica basata sulle tag utilizzando la [API REST](https://mobile.{DomainName}/imfpush/){: new_window}, assicurati che i "tagName" siano forniti durante l'inserimento nella risorsa messaggi.


## Gestione delle tag
{: #manage_tags}

Utilizza la console {{site.data.keyword.mobilepushshort}} per creare ed eliminare tag per la tua applicazione e avviare quindi le notifiche basate sulle tag. La notifica basata sulle tag viene ricevuta dai dispositivi che hanno sottoscritto le tag.


### Creazione di tag
{: #create_tags}

Le notifiche basate sulle tag sono messaggi destinati a tutti i dispositivi sottoscritti a una particolare tag. Ciascun dispositivo può sottoscrivere qualsiasi numero di tag. 

1. Nella console {{site.data.keyword.mobilepushshort}} **Tags**.
1. Fai clic sul pulsante + **Crea tag**.   
   1. Nel campo **Nome**, immetti il nome della tag. Ad esempio, "coupons".
   1. Nel campo **Descrizione**, immetti una descrizione della tag.
   1. Fai clic su **Save**.

1. Nell'area **Frammenti di codice**, seleziona la piattaforma per la tua applicazione mobile.
1. Modifica i frammenti di codice per gestire gli errori e copiali quindi per ogni tag nella tua applicazione mobile.

### Eliminazione di tag
{: #delete_tags}

1. Dalla scheda **Tag**, seleziona la tag che vuoi eliminare e fai clic sull'icona **Elimina**.
1. Fai clic su **OK**.

Quando viene eliminata una tag, vengono eliminate anche le informazioni associate con tale tag, inclusi i relativi sottoscrittori e dispositivi. L'annullamento della sottoscrizione automatico non è obbligatorio, poiché la tag non esiste più. Non è richiesta alcuna ulteriore azione dal lato client.

### Modifica della descrizione di una tag
{: #edit_tags}

1. Dalla scheda **Tag**, seleziona la tag che vuoi modificare.
1. Fai clic sull'icona **Modifica**.
1. Modifica la descrizione della tag e fai quindi clic sul pulsante **Salva**.

## Ottieni le tag
{: #get_tags}

Le tag forniscono un modo per inviare notifiche mirate agli utenti sulla base dei loro interessi, a differenza dai broadcast generali che vengono inviati a tutte le applicazioni. Puoi creare e gestire le tag utilizzando la scheda Tags nella console {{site.data.keyword.mobilepushshort}}oppure utilizzare le API REST. Puoi utilizzare i frammenti di codice per gestire e sottoporre a query le tue sottoscrizioni di tag per la tua
            applicazione mobile. Puoi utilizzare i frammenti di codice per ottenere sottoscrizioni, sottoscrivere una tag, annullare la sottoscrizione a un tag o ottenere un elenco delle tag disponibili. Copia e incolla questi frammenti di codice nella tua applicazione mobile.


- Per Android, consulta le API `getTags` e `getSubscriptions` in  [Push Notification get tags on Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

- Per Cordova, consulta le API `retrieveAvailableTags()` e `retrieveSubscriptions()` in [Push Notifications get tags on Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Per iOS, consulta l'API `retrieveAvailableTagsWithCompletionHandler` in [Push Notifications get tags on Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags).

- Per i browser web, consulta l'API `retrieveAvailableTags()` in [Push Notifications get tag on web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).


## Sottoscrivi tag
{: #Subscribe_tags}

Utilizza la seguente API per consentire ai tuoi dispositivi di richiamare tag, sottoscrivere una tag, richiamare le sottoscrizioni e annullare la sottoscrizione a una tag.

- Per Android, utilizza le API `getTags`, `subscribe`, `getSubscriptions` e `unsubscribeFromTags`. Consulta [Push Notifications subscribe tags for Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags).

- Per Cordova, utilizza le API `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` e `unsubscribe()`. Consulta [Push Notifications subscribe tags for Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Per iOS, utilizza le API `retrieveAvailableTagsWithCompletionHandler`, `subscribeToTags`, `retrieveSubscriptionsWithCompletionHandler` e `unsubscribeFromTags`. Consulta [Push Notifications subscribe tags for Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags).

- Per i browser web, utilizza le API `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` e `unSubscribe()`. Consulta [Push Notifications subscribe tags for web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).

## Utilizzo delle notifiche basate sulle tag
{: #using_tags}

Le notifiche basate sulle tag sono messaggi destinati a tutti i dispositivi sottoscritti a una particolare tag. Ciascun dispositivo può essere sottoscritto a un qualsiasi numero di tag. Questo argomento descrive come inviare notifiche basate sulle tag. Le sottoscrizioni vengono gestite dall'istanza IBM Cloud del servizio {{site.data.keyword.mobilepushshort}}. Quando viene eliminata una tag, vengono eliminate anche tutte le informazioni associate con tale tag, inclusi i relativi sottoscrittori e dispositivi. Non è necessario un annullamento della sottoscrizione automatico per questa tag poiché non esiste più e non sono richieste ulteriori azioni dal lato client.

Crea le tag sulla schermata **Tag**. Per informazioni su come creare le tag, vedi [Creazione di tag](t_manage_tags.html).

1. Dalla console **Push Notification**, fai clic su **Send Notifications**.
1. Seleziona l'opzione **Device by Tag** nell'elenco a discesa **Send To**.
1. Cerca le tag che vuoi utilizzare e selezionale.
![Schermata notifiche](images/tag_notification.jpg)
1. Nel campo **Message Text**, immetti il testo che deve essere inviato come notifica ai destinatari sottoscritti.
1. Fai clic su **Send**.
