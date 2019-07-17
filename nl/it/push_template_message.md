---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, parameterize notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Imposta parametri notifiche
{: #template_based_notifications}

Puoi impostare i parametri ed inviare notifiche personalizzate creando variabili e richiamandole nei tuoi template di notifica.

Il tuo template di notifica può -

 - Combinare elementi dinamici e statici nelle tue notifiche
 - Personalizzare le notifiche di ogni destinatario aggiungendo le variabili
 - Puoi includere più variabili nella tua notifica 

Passa le variabili come oggetti JSON nel tuo codice dell'applicazione durante l'inizializzazione -

    
   ```
    MFPPushNotificationOptions options = new MFPPushNotificationOptions();

    JSONObject tempValue = new JSONObject();
        try {
        
		tempValue.put("username",userName);
        
        tempValue.put("amountSpent",amount);
		
        tempValue.put("currency",currency);
		
        tempValue.put("avilableBalance",balance);
        
		} catch (JSONException e) {
            e.printStackTrace();
        }
        options.setPushVariables(tempValue); 
	   
	   push = MFPPush.getInstance();

       push.initialize(getApplicationContext(),appGuid,clientSecret,options);
   ```
{: codeblock}


Una volta che sono state definite le variabili, possono essere richiamate nel tuo template del messaggio.

1. Nella console {{site.data.keyword.mobilepushshort}}, seleziona la scheda **Messages**.

2. Componi un messaggio scegliendo l'opzione **Send to**.

3. Nel campo **Message**, componi il messaggio.  Richiama le variabili nel template del messaggio. Fai clic su **Send**.

![message template](images/message_template.png "Pagina Message che mostra un modello di messaggio con Sent to field impostato su All devices, il campo Message con un messaggio di esempio del saldo del conto bancario di un utente e il campo Additional payload con l'attributo "key":"value" aggiunto.")

Il tuo messaggio di notifica personalizzato sarà inviato recuperando i dati della variabile -

![esempio di messaggio](images/message_template_example.jpg "Notifica di esempio basata su modello di messaggio")

Nota: la funzione è abilitata solo per gli utenti che hanno scelto il `Advanced Plan`. Seleziona **Plan** nella console del servizio {{site.data.keyword.mobilepushshort}} per l'[upgrade](https://cloud.ibm.com/docs/account?topic=account-changing#changing) .

## Limitazioni
{: #limitations}

 - Al momento, questa funzione non è supportata su Safari
 - Le variabili nel template di notifica non funzionano se è stata forzata l'uscita di un'applicazione su iOS. La limitazione non è sotto il controllo della SDK ma viene da iOS.

