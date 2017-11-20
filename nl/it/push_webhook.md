---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Ricezione di avvisi sugli eventi webhook
{: #webhook_event_based_notifications}
Ultimo aggiornamento: 8 settembre 2017
{: .last-updated}


Con il servizio {{site.data.keyword.mobilepushshort}}, puoi scegliere di ricevere avvisi relativi alle modifiche apportate alle informazioni. Le modifiche alle informazioni aziendali creano degli eventi, per i quali puoi ricevere una notifica registrandoli come eventi webhook. Questi eventi webhook attivano un avviso. 

I webhook sono dei callback definiti dall'utente che vengono attivati da un evento, ad esempio la registrazione di un dispositivo o la sottoscrizione a una tag. Nel servizio {{site.data.keyword.mobilepushshort}}, puoi effettuare la registrazione per i seguenti webhook: 

- **onDeviceRegister**: un evento webhook viene attivato per i dispositivi registrati per il push.
- **onDeviceUpdate**: un evento webhook viene attivato quando vengono aggiornate le informazioni su un dispositivo registrato.
- **onDeviceUnregister**: un evento webhook viene attivato quando viene annullata la registrazione di un dispositivo. 
- **onSubscribe**: un evento webhook viene attivato per la sottoscrizione dell'utente a una tag.
- **onUnsubscribe**: un evento webhook viene attivato per l'annullamento della sottoscrizione dell'utente a una tag.
- **onNotificationStatusChange**: un evento webhook viene attivato per per ogni notifica e indica lo stato come SENT, FAILED, OPEN o SEEN.


**Nota**: gli invii delle notifiche vengono effettuati in batch. L'invio di un messaggio può avere più eventi webhook, che possono includere sia errori che esiti positivi. 
Gli eventi webhook hanno lo stesso messageID del messaggio inviato. 

Per ulteriori informazioni sui webhook, vedi [IBM Push Notifications REST API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console-regional.stage1.ng.bluemix.net/apidocs/800){: new_window}.

## Ricezione di avvisi sugli eventi webhook
{: #webhook_alert_event}

I sottoscrittori possono scegliere di ricevere gli avvisi sugli eventi webhook in forma di file JSON. La struttura degli eventi e il payload di esempio sono i seguenti:

- Registrazione di un dispositivo
	```
		{ type: 'onDeviceRegister',
		entity:
		{ id: 1,
		deviceId: 'device1',
		applicationId: 'app1',
		userId: 'user1',
		token: 'token1',
		platform: 'G' },
		applicationId: 'app1',
		eventTimeStamp: 1487523766958 }
	```
		{: codeblock}

- Aggiornamento di un dispositivo

	```
		{
		  "type": 'onDeviceUpdate',
		  entity : 
			{
		    "deviceId" : 'device1',
		    "userId" : 'user1',
		    "token" : 'token1'
		  	platform: 'G' },
		  "applicationId" : 'app1',
		  "eventTimeStamp" : 1497006049244 }
	```
		{: codeblock}

- Annullamento della registrazione di un dispositivo
	```
		{ type: 'onDeviceUnregister',
		entity:
		{ id: 1,
		deviceId: 'device1',
		applicationId: 'app1',
		userId: 'user1',
		token: 'token1',
		platform: 'G' },
		applicationId: 'app1',
		eventTimeStamp: 1487523841874 }
	```
		{: codeblock}

- Sottoscrizione a una tag
	```
		{ type: 'onSubscribe',
		entity:
		{ device:
		{ id: 18,
		deviceId: 'device1',
		applicationId: 'app1',
		userId: 'user1',
		token: 'token1',
		platform: 'G' },
		tagName: 'tag1',
		subscriptionId: 'b0246677bfa655385fbc2b5532f6443f' },
		applicationId: 'app1',
		eventTimeStamp: 1487755527470 }
	```
		{: codeblock}

- Annullamento della sottoscrizione a una tag
	```
		{ type: 'onUnsubscribe',
		entity:
		{ device:
		{ id: 18,
		deviceId: 'device1',
		applicationId: 'app1',
		userId: 'user1',
		token: 'token1',
		platform: 'G' },
		tagName: 'tag1',
		deviceId: 'device1',
		subscriptionId: 'b0246677bfa655385fbc2b5532f6443f' },
		applicationId: 'app1',
		eventTimeStamp: 1487755581059 }
	```
		{: codeblock}

- Invio di una notifica
	```
		{ type: 'onNotificationStatusChange',
		entity:
		{ deviceIds:
		[ 'device1',
		'device2'],
		platform: 'A',
		msgStatus: 'SENT', `FAILED`, `SEEN`, `OPEN`
		messageId: '55cb688' },
		applicationId: 'app1',
		eventTimeStamp: 1487524517353 }
	```
		{: codeblock}

- Errore di notifica
	```
		{ type: 'onNotificationFailure',
		entity:
		{ applicationId: 'app1',
		deviceIds: [ 'device1' ],
		platform: 'G',
		msgStatus: 'failure',
		failureReason: 'InvalidRegistration',
		messageId: '55cb688' },
		applicationId: 'app1',
		eventTimeStamp: 1487524519453 }
	```
		{: codeblock}

