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

# Parametrizar notificações
{: #template_based_notifications}

É possível parametrizar e enviar notificações customizadas criando variáveis e chamando-as em seus modelos de notificação.

Seu modelo de notificação pode -

 - Combinar elementos estáticos e dinâmicos em suas notificações
 - Personalizar notificações para cada destinatário, incluindo variáveis
 - Pode incluir múltiplas variáveis em sua notificação 

Passar variáveis como objetos JSON em seu código do aplicativo durante a inicialização -

    
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


Quando as variáveis estiverem definidas, elas poderão ser chamadas em seu modelo de mensagem.

1. No console do {{site.data.keyword.mobilepushshort}}, selecione a guia **Mensagens**.

2. Componha uma mensagem escolhendo uma opção **Enviar para**.

3. No campo **Mensagem**, componha sua mensagem.  Chame as variáveis definidas no modelo de mensagem. Clique em **Enviar**.

![modelo de mensagem](images/message_template.png "Página de mensagem mostrando um modelo de mensagem com o campo Enviar para configurado como Todos os dispositivos, campo de Mensagem com mensagem de exemplo sobre um saldo de conta de banco de um usuário e campo de Carga útil adicional com o atributo "key":"value" incluído.")

Sua mensagem de notificação customizada será enviada buscando os dados variáveis -

![exemplo de mensagem](images/message_template_example.jpg "Notificação de exemplo com base no modelo de mensagem")

Nota: o recurso é ativado apenas para usuários que optaram pelo `Advanced Plan`. Selecione **Planejar** no console do serviço {{site.data.keyword.mobilepushshort}} para [fazer upgrade](https://cloud.ibm.com/docs/account?topic=account-changing#changing).

## Limitações
{: #limitations}

 - Atualmente, esse recurso não é suportado no Safari
 - As variáveis no modelo de notificação poderão não funcionar se um app for forçado a encerrar no iOS. A limitação não está no controle de SDK, mas vem do iOS.

