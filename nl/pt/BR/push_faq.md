---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, faq, frequently asked questions

subcollection: mobile-pushnotification

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Perguntas mais freqüentes 
{: #faq}

### Por que meus tokens ser invalidadas.
{: #faq-tokens}	

Para registros de dispositivo, navegador, Apps Chrome e Extensões, o serviço Push Notifications mantém uma referência exclusiva para tokens emitidos por meio de provedores de notificação - APNs para Apple ou FCM para Google. Os tokens podem ser invalidados pelo provedor de notificação de serviço por vários motivos. 

Um exemplo é durante a desinstalação de um app no dispositivo. Nesse cenário, quando a entrega de uma notificação for tentada com base na resposta dos provedores de que o dispositivo está invalidado, o serviço {{site.data.keyword.mobilepushshort}} removerá os registros do dispositivo ou do navegador da web. Isso, por sua vez, restringiria tentativas subsequentes de enviar a notificação a esses dispositivos invalidados. 

Você também poderá ter o problema se tiver removido o registro de um dispositivo.

Assegure-se de que obtenha uma Chave API do servidor e um ID do emissor válidos para continuar. Consulte [Obtenha suas credenciais de provedor de notificação](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1).

### Por que recebo *A notificação não está funcionando para WEB_Chrome.*, ao tentar inicializar o SDK do push da web?
{: #faq-web-chrome}	

Você pode ter mudado suas credenciais do FCM para SDK de push da web e a entrega da mensagem poderá falhar para o navegador Chrome. Assegure-se de chamar
*bmsPush.unRegisterDevice* para evitar falha.

### Eu recebo a mensagem *Trabalhadores de serviço não são suportados neste navegador* ao tentar inicializar o SDK for Web Push. O que pode ser o problema? 
{: #faq-service-workers}	

Siga as etapas mencionadas na [Etapa 3: Configurar os SDKs do cliente de serviço de Push](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3). Também assegure que:

1. Você usa o método de início correto. 
2. Inclua o arquivo `manifest.json` na pasta raiz.
3. Host do seu website. De preferência, crie um iniciador `node.js` no IBM Cloud para experimentá-lo. Por exemplo: https://<mysamplewebsite>.cloud.ibm.com/.	

### Como resolver erros de configuração da web de push da Web?
{: #faq-web-config-errors}	

Os erros de push da web do `BMSPushSDK.js` contêm informações sobre a falha. Consulte [Troubleshooting](/docs/services/mobilepush?topic=mobile-pushnotification-errors).	

### As notificações persistirão se os dispositivos estiverem off-line?
{: #faq-notification-persist}	

Esse recurso depende do provedor de notificação.	

### O messageID é exclusivo para um aplicativo e qual é o seu tamanho?
{: #faq-messageid}	

O messageID é exclusivo para um aplicativo e está limitado a oito caracteres. Pode ser alfanumérico.

### Quais são os limites para Notificações push, em termos de tamanho de carga útil?
{: #faq-limits-push-payload-size}	

O tamanho da carga útil da mensagem do {{site.data.keyword.mobilepushshort}} depende das restrições estabelecidas pelos Gateways (FCM, APNs) e plataformas do cliente. 

Para o iOS 8 e mais recente, o tamanho máximo permitido é de 4 kilobytes. Observe que o APNs não envia notificações que excedam esse limite. Para o Android, o navegador Firefox, o navegador Chrome e os Apps Chrome e Extensões, há uma limitação de 4 kilobytes como o tamanho máximo permitido de carga útil da mensagem.	

### As notificações enviadas são armazenadas em servidores BMS?
{: #faq-bms-servers}	

Sim, as notificações são armazenadas por um período de noventa dias. Recomenda-se não enviar nenhuma mensagem confidencial como notificação.

### Posso enviar notificação para dispositivos no modo Doze?
{: #faq-doze-mode}	

Este recurso não é suportado.	

### Quais são os diferentes planos de precificação disponíveis para o serviço Push Notifications?
{: #faq-pricing-plans}	

* <b>Plano avançado</b>: isso está disponível para US$ 100,00/Instância, US$ 0,50/Milhão de mensagens digitais e US$ 0,50/Milhão de dispositivos endereçáveis. Com o plano avançado, é possível enviar notificações de push para 1 milhão de dispositivos endereçáveis e 100 milhões de mensagens digitais. O plano avançado inclui recursos como mensagens de Parametrização e de rastreamento de ciclo de vida de mensagem de ponta a ponta.

* <b>Plano básico</b>: está disponível para US$ 1,00 USD/Milhão de mensagens digitais. Com o plano básico, é possível enviar notificações push para um dispositivo exclusivo, um navegador, terminais ou um evento baseado em webhook. 

* <b>Plano Lite</b>: é um plano grátis que apresenta cem mil mensagens digitais gratuitas por mês. No entanto, os serviços do plano Lite são excluídos após 30 dias de inatividade.	

### Onde posso localizar mais informações, como tutoriais ou o que há de novo?
{: #faq-what-is-new}	

Examine os [vídeos](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA) de serviço de Notificações de push.	

### Há diferença entre uma notificação e uma mensagem?
{: #faq-diff-notification-message}	

Sim. Uma _mensagem_ é o que o usuário está enviando para o serviço {{site.data.keyword.mobilepushshort}}. O serviço despacha isso como uma _notificação_ para o gateway de notificação (APNs/FCM) e será entregue para o dispositivo ou o navegador da web.

Para cada mensagem enviada para o serviço, o público desejado recebe uma notificação.	

### O painel de monitoramento de Notificações push exibe algum status para as mensagens enviadas?
{: #faq-push-monitor-dashboard}	

O utilitário de monitoramento exibe o status para cada mensagem enviada. As mensagens podem estar no estado a seguir:
	
* Enviada: o número de dispositivos para os quais as notificações são enviadas.
* Vista: o número de dispositivos nos quais as notificações chegaram.
* Aberta: o número de dispositivos no quais a notificação foi aberta.
* Inválida: o número de dispositivos nos quais o token é inválido.

Para obter mais informações, veja o relatório de mensagens GET em [API de REST do IBM Push Notifications](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).	

### A notificação push monitora a entrega de notificação push até o dispositivo do usuário final? Para ambos Android e iOS?
{: #faq-end-user-device}	

As notificações push são monitoradas com base no número de notificações vistas ou abertas no dispositivo do usuário final. Isso está disponível para o Android e o iOS. ID do Dispositivo baseado em monitoramento não é suportado. 

### Eu recebo a mensagem de que o servidor atualmente não é capaz de manipular solicitações? Como posso resolver isso?
{: #faq-server-unable-to-handle-requests}	

É possível ver o erro com o código de erro FPWSE0025E. Isso pode ser em razão de muitas solicitações para o servidor manipular. É possível tentar reenviar a solicitação posteriormente.	

### Estou enviando uma notificação por tags, mas tenho uma longa lista de tags que podem ser difíceis de incluir manualmente. 
{: #faq-tag-based-notification}	

É possível usar as APIs de REST para automatizar as adições de tags. Consulte [POST mensagens em massa](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).

### Como posso filtrar a entrega de notificação push por informações armazenadas no dispositivo móvel do usuário?
{: #faq-filter-device}	

Isso deve ser manipulado no contexto de desenvolvimento de aplicativo.

### Posso customizar ainda mais o monitoramento de notificação push para incluir relatório customizado, como relatório de entrega por segmentação?
{: #faq-customize-delivery-report}	

Este recurso não é suportado.

### Posso criar um segmento para usuário ou usuários de novo app que não tenham acessado o app móvel por algum tempo?
{: #faq-create-segment}	

Isso deve ser manipulado no contexto de desenvolvimento de aplicativo.
	
### Posso registrar/atualizar dispositivos móveis em massa usando as APIs de REST?
{: #faq-register-mobile-devices}	

Conforme o design, o registro/a atualização de um dispositivo é chamada por meio dos aplicativos móveis usando o SDK. Os registros/as atualizações em massa por meio de APIs de REST não são suportados. Se muitos registros/muitas atualizações de dispositivo forem chamados simultaneamente usando as APIs de REST, isso pode levar muito tempo ou pode falhar.	

### Como eu envio Notificações de push ou uso as APIs de REST quando não tenho o appSecret?
{: #faq-rest-api-appsecret}	

À medida que o serviço do {{site.data.keyword.mobilepushshort}} tiver adotado o IAM, uma `apiKey` será exibida em vez do `appSecret` quando o usuário criar as credenciais de serviço.

Para usar quaisquer APIs de REST, deve-se gerar o token de acesso usando o comando curl a seguir:

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```

```
{
 "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```
{: codeblock}

Ao gerar o token de acesso usando o comando curl anterior, agora é possível operar as APIs de REST passando o `Bearer <value of access_token>` no cabeçalho de Autorização.

Por exemplo:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
