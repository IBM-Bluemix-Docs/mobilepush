---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, message delivery status

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Status de entrega de mensagens
{: #message-delivery-status}

Com o serviço {{site.data.keyword.mobilepushshort}}, é possível visualizar o status de entrega de cada notificação que foi enviada para o serviço. 

Depois que a mensagem é enviada, é possível rastrear informações de entrega de uma mensagem verificando seu status de entrega. Em qualquer ponto específico de tempo, o serviço exibe o status apenas das 10 mensagens mais recentes disponíveis em um período de 90 dias.

A guia **Mensagens** do serviço {{site.data.keyword.mobilepushshort}} exibe o status de notificação.

![status de notificações](images/notification_status_new.png "Página de mensagens mostrando o status de notificação")

1. **ID de mensagem** - um identificador exclusivo para identificar uma mensagem.

2. **Texto da mensagem** - um modelo de mensagem que foi enviado aos usuários do app.

3. **Data** - Data e hora em que a mensagem foi enviada para o serviço.

4. **Status** - Fornece um status breve do resumo de uma mensagem. Dependendo do status de entrega da mensagem, é possível ver um dos status a seguir:

 - Aceito: a mensagem foi aceita para entrega pelo serviço Push Notifications.
   
 - Despachando: a notificação foi recebida pelo provedor de notificação - APNs, FCM ou Web - e está prestes a ser despachada. Uma notificação que está no processo de ser despachada também pode retornar uma falha com o status **O despacho falhou**.
 
 - Despachada: a notificação foi despachada pelo provedor de notificação.
 
 - Processando: a mensagem está sendo processada para ser despachada para o gateway do provedor de notificação. Uma notificação que está sendo processada também pode retornar uma falha com o status **O processamento falhou**.
 
 - Desconhecido: o status da notificação não pode ser determinado.
 
5. **Visualizar** - exibe o status de entrega das notificações despachadas. É possível visualizar informações com base nos aspectos a seguir:

 - Categoria: Todos, Mobile, Web<! --- e HTTP --- >.
 
 - Status da mensagem: Enviado, Visto, Aberto e Inválido. 

![status de notificações](images/message_delivery_status_new.png "Gráfico de status de mensagem mostrando o detalhamento de status aberto, enviado, visto e inválido")

6. **Opções** - Fornece um status detalhado de uma notificação. O status pode ser rastreado selecionando o `Device Id` ou o `User Id` no menu suspenso. Obter a mensagem de status detalhada específica do usuário/dispositivo pode ser útil quando você está rastreando uma mensagem com falha.

![status detalhado](images/detailed_message_delivery.png "Opções de status de entrega de mensagem detalhada com ID do usuário selecionado")

**Nota**: o recurso é ativado apenas para usuários que optaram pelo `Advanced Plan`. Selecione **Planejar** no console do serviço {{site.data.keyword.mobilepushshort}} para [fazer upgrade](https://cloud.ibm.com/docs/account?topic=account-changing#changing)

