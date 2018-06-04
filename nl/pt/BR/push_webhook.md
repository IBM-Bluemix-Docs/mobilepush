---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Receber alertas em eventos de webhook
{: #webhook_event_based_notifications}
Última atualização: 8 de setembro de 2017
{: .last-updated}


Com o serviço {{site.data.keyword.mobilepushshort}}, é possível optar por receber alertas
sobre informações que foram mudadas. As mudanças nas informações corporativas criam eventos, para os quais é
possível ser notificado registrando-os como eventos webhook. Esses eventos webhook acionam um alerta. 

Webhooks são retornos de chamada definidos pelo usuário que são acionados por um evento, como
registrar-se em um dispositivo ou inscrever-se nas tags. No serviço {{site.data.keyword.mobilepushshort}},
é possível registrar-se para os eventos webhook a seguir: 

- **onDeviceRegister**: um evento webhook é acionado para dispositivos registrados
para push.
- **onDeviceUpdate**: um evento webhook é acionado quando informações sobre um
dispositivo registrado são atualizadas.
- **onDeviceUnregister**: um evento webhook é acionado quando um
dispositivo tem o registro cancelado. 
- **onSubscribe**: um evento webhook é acionado quando um usuário se inscreve em
uma tag.
- **onUnsubscribe**: um evento webhook é acionado quando um usuário remove a
assinatura de uma tag.
- **onNotificationStatusChange**: um evento webhook é acionado para cada notificação e indica o status como SENT, FAILED, OPEN ou SEEN.


**Nota**: a notificação é despachada em lotes. Um despacho de mensagem pode ter
múltiplos eventos webhooks, que podem incluir falhas e sucesso. 
Os eventos webhook têm o mesmo messageID que a mensagem despachada. 

Para obter mais informações sobre webhooks, veja a [API de REST de notificações push da IBM ![Ícone de link externo](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/apidocs/800-push-notifications){: new_window}.

## Recebendo alertas em eventos webhook
{: #webhook_alert_event}

Os assinantes podem optar por receber alertas sobre eventos webhook como arquivos JSON. A estrutura do evento e a carga útil de amostra são como a seguir:

- Registrando um Dispositivo
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

- Atualizando um dispositivo

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

- Cancelando o registro de um dispositivo
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

- Assinando uma identificação
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

- Cancelando a assinatura de uma tag
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

- Enviar uma notificação
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

- Falha de notificação
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

