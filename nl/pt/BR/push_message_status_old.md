---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Status de entrega de notificação de mensagem
{: #tag_based_notifications}
Última atualização: 21 de agosto de 2017
{: .last-updated}


Com o serviço {{site.data.keyword.mobilepushshort}}, é possível visualizar o status de cada notificação que foi enviada para o serviço. 

Uma mensagem que foi enviada pode ter o status a seguir:

- **Aceito**: a mensagem foi aceita para entrega pelo serviço Push Notifications.
- **Processando**: a mensagem está sendo processada para ser despachada para o gateway do provedor de notificação. Uma notificação que está sendo processada também pode retornar uma falha com o status **O processamento falhou**.
- **Despachando**: a notificação foi recebida pelo provedor de notificação - APNs, FCM ou Web - e está prestes a ser despachada. Uma notificação que está no processo de ser despachada também pode retornar uma falha com o status **O despacho falhou**.
- **Despachada**: a notificação foi despachada pelo provedor de notificação.
- **Desconhecido**: o status da notificação não pode ser determinado.

A guia Mensagens do serviço {{site.data.keyword.mobilepushshort}} exibe o status de notificação.

![notifications status](images/notification_status_new.png)

1. A opção **Visualizar** exibe o status de entrega das notificações despachadas. É possível visualizar informações com base nos aspectos a seguir:

 - Categoria: Todos, Mobile, Web<! --- e HTTP --- >.
 - Status da mensagem: Enviado, Visto, Aberto e Inválido. 

![notifications status](images/message_delivery_status_new.png)

2. Clique em **Opções** para obter o **Status de entrega detalhado da mensagem**. Um status de entrega detalhado pode ser rastreado selecionando o `Device Id` ou o `User Id` no menu suspenso. Um status detalhado para um usuário específico ou um dispositivo pode ser buscado.

![detailed status](images/detailed_message_delivery.png)


Em qualquer ponto específico de tempo, o serviço exibe o status apenas das 10 mensagens mais recentes disponíveis em um período de 90 dias.

**Nota**: o recurso é ativado apenas para usuários que optaram pelo `Advanced Pricing Plan`. Selecione **Planejar** no console do serviço {{site.data.keyword.mobilepushshort}} para [fazer upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)
