----

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Segurança nas Notificações push 
{: #overview-push}
Última atualização: 27 de junho de 2017
{: .last-updated}


As APIs do {{site.data.keyword.mobilepushshort}} são protegidas por dois tipos de segredos:

- **appSecret**: o `appSecret` protege as APIs que são geralmente chamadas por aplicativos backend - como a API para enviar o {{site.data.keyword.mobilepushshort}} e a API para configurar definições.
- **clientSecret**: o `clientSecret` protege as APIs que são geralmente chamadas por aplicativos cliente móveis. Existe somente uma API relacionada para registro de um dispositivo com um ID de usuário associado que requer este `clientSecret`. Nenhuma das outras APIs chamadas de clientes móveis requer o `clientSecret`. 

O `appSecret` e o `clientSecret` são alocados para todas as instâncias de serviço no momento da ligação de um aplicativo ao serviço {{site.data.keyword.mobilepushshort}}. Consulte a documentação das [APIs de REST ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://mobile.{DomainName}/imfpush/) para obter informações sobre como os segredos devem ser passados e para quais APIs.

## appSecret 
{: #push-api-rest-secret}

Quando um aplicativo é ligado ao {{site.data.keyword.mobilepushshort}}, o serviço gera um appSecret (uma chave exclusiva) e passa-o no cabeçalho de resposta. Se
você estiver usando a API de REST do IBM {{site.data.keyword.mobilepushshort}} for IBM Cloud, use a referência da API de REST para obter informações sobre quais
APIs você precisa assegurar. Para obter informações, veja a [API de REST Push ![Ícone de link externo](../../icons/launch-glyph.svg "External link icon")](https://mobile.{DomainName}/imfpush/){: new_window}.

O cabeçalho da solicitação deve conter o appSecret. Caso contrário, o servidor retornará um código de erro 401 Desautorizado. Quando o {{site.data.keyword.mobilepushshort}} é incluído em um aplicativo, um AppID específico é criado. Como parte da resposta, você obtém um cabeçalho chamado appSecret que é usado para criar tags ou enviar
mensagens. A operação acontece por meio de serviços no catálogo ou do modelo.

Para obter o valor appSecret:

1. Clique no* app-name* que está ligado ao serviço de push.
2. Clique no link **Mostrar credenciais** para exibir o appSecret (AppID).

A tela **Mostrar credenciais** mostra informações sobre o AppSecret:
```
	{
    "imfpush_Dev": [
   {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://imfpush.ng.bluemix.net/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.ng.bluemix.net/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**Nota**: os aplicativos anteriores eram necessários para passar o clientSecret somente ao registrar ou atualizar dispositivos com o campo userId. Todas
as outras APIs chamadas por clientes móveis e do navegador não requerem o clientSecret. Esses aplicativos antigos podem continuar a usar o clientSecret opcionalmente
para registros de dispositivo ou chamadas de atualização. Entretanto, é
expressamente recomendado que a verificação do clientSecret seja imposta para todas as
chamadas de API do cliente. Para usar isso em aplicativos existentes, há uma nova API `verifyClientSecret` publicada.  Para novos aplicativos, a verificação do clientSecret será forçada em todas as chamadas API do cliente. Esse comportamento não pode mudar com a API `verifyClientSecret`.

Por padrão, a verificação do segredo do cliente é impingida apenas em novos apps. Os apps existentes e novos têm permissão para ativar ou desativar a verificação do segredo do cliente
usando a API de REST verifyClientSecret. Recomenda-se que você impinja a verificação do segredo do cliente para evitar
expor dispositivos para usuários que possam conhecer o ID do aplicativo e o ID do dispositivo.

Assegure-se de que o `clientSecret` seja mantido confidencial e nunca seja codificado permanentemente no app móvel. Há vários padrões de inicialização de aplicativo que podem ser usados para puxar o `clientSecret` dinamicamente durante o tempo de execução dos aplicativos. O diagrama de sequência é descrito nesse possível padrão.
![Enable_Push](images/init_client_secret.jpg) 



