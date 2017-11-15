---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Alerts für Webhookereignisse empfangen
{: #webhook_event_based_notifications}
Letzte Aktualisierung: 08. September 2017
{: .last-updated}


Mit dem {{site.data.keyword.mobilepushshort}}-Service können Sie sich für das Empfangen von Alerts zu Informationen, die sich geändert haben, entscheiden. Änderungen an Unternehmensinformationen erzeugen Ereignisse, zu denen Sie Benachrichtigungen erhalten können, indem Sie sie als Webhook-Ereignisse registrieren. Diese Webhook-Ereignisse lösen einen Alert aus. 

Webhooks sind benutzerdefinierte Callbacks, die durch ein Ereignis ausgelöst werden, beispielsweise das Registrieren eines Geräts oder das Subskribieren eines Tags. Mit dem {{site.data.keyword.mobilepushshort}}-Service können Sie sich für die folgenden Webhook-Ereignisse registrieren: 

- **onDeviceRegister**: Ein Webhook-Ereignis wird für Geräte ausgelöst, die für Push-Operationen registriert werden.
- **onDeviceUpdate**: Ein Webhook-Ereignis wird ausgelöst, wenn Informationen zu einem registrierten Gerät aktualisiert werden.
- **onDeviceUnregister**: Ein Webhook-Ereignis wird ausgelöst, wenn die Registrierung eines Geräts aufgehoben wird. 
- **onSubscribe**: Ein Webhook-Ereignis wird ausgelöst, wenn ein Benutzer einen Tag subskribiert.
- **onUnsubscribe**: Ein Webhook-Ereignis wird ausgelöst, wenn ein Benutzer die Subskription eines Tags aufhebt.
- **onNotificationStatusChange**: Ein Webhook-Ereignis wird für jede Benachrichtigung ausgelöst und gibt den Status als SENT, FAILED, OPEN oder SEEN an.


**Anmerkung**: Das Versenden von Benachrichtigungen erfolgt in Stapeln. Dieselbe Nachrichtenversendung kann mehrere Webhook-Ereignisse umfassen, wobei es sich sowohl um fehlgeschlagene als auch um erfolgreiche handeln kann. 
Die Webhook-Ereignisse haben dieselbe Nachrichten-ID (messageID) wie die versandte Nachricht. 

Weitere Informationen zu Webhooks finden Sie in der [IBM Push Notifications-REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console-regional.stage1.ng.bluemix.net/apidocs/800){: new_window}.

## Alerts für Webhookereignisse empfangen
{: #webhook_alert_event}

Subskribenten können festlegen, dass sie Alerts für Webhookereignisse als JSON-Dateien erhalten möchten. Die Ereignisstruktur und die Beispielnutzdaten lauten wie folgt:

- Gerät registrieren
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

- Gerät aktualisieren

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

- Registrierung für ein Gerät aufheben
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

- Tag subskribieren
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

- Subskription eines Tags aufheben
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

- Benachrichtigung senden
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

- Fehlgeschlagene Benachrichtigung
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

