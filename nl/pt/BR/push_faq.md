---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Perguntas mais freqüentes 
{: #faq}


1. Por que meus tokens ser invalidadas.
	
	Para registros de dispositivo, navegador, Apps Chrome e Extensões, o serviço Push Notifications mantém uma referência exclusiva para tokens emitidos por meio de provedores de notificação - APNs para Apple ou FCM para Google. Os tokens podem ser invalidados pelo provedor de notificação de serviço por vários motivos. 

	Um exemplo é durante a desinstalação de um app no dispositivo. Nesse cenário, quando a entrega de uma notificação for tentada com base na resposta dos provedores de que o dispositivo está invalidado, o serviço {{site.data.keyword.mobilepushshort}} removerá os registros do dispositivo ou do navegador da web. Isso,
por sua vez, restringiria tentativas subsequentes de enviar a notificação a esses dispositivos invalidados. 

	Você também poderá ter o problema se tiver removido o registro de um dispositivo.

	Assegure-se de que obtenha uma Chave API do servidor e um ID do emissor válidos para continuar. Consulte [Obtenha suas credenciais de provedor de notificação](push_step_1.html).


2. Por que recebo "A notificação não está funcionando para WEB_Chrome."ao tentar inicializar o Web Push SDK?.

	É possível que você tenha mudado suas credenciais do FCM/GCM do Web Push SDK e a entrega da mensagem possa falhar para o navegador Chrome. Assegure-se de chamar "bmsPush.unRegisterDevice" para evitar falha.

3. Eu recebo a mensagem "Trabalhadores de serviço não são suportados neste navegador" ao tentar inicializar o SDK for Web Push. O que pode ser o problema? 

	Siga as etapas mencionadas na [Etapa 3: Configurar os SDKs do cliente de serviço de Push](push_step_3.html).	Também assegure que:
 
	1. Você usa o método de início correto. 
	1. Inclua o arquivo `manifest.json` na pasta raiz.
	1. Host do seu website. Crie, de preferência, um iniciador `node.js` no IBM Cloud para experimentá-lo. Por exemplo: https:// < mysamplewebsite> .mybluemix.net/.	

4. Como resolver erros de configuração da web de push da Web?

	Os erros de push da web do `BMSPushSDK.js` contêm informações sobre a falha.  Consulte [Troubleshooting](push_troubleshooting.html).	

5. As notificações persistirão se os dispositivos estiverem off-line?

	Esse recurso depende do provedor de notificação.	

6. O messageID é exclusivo para um aplicativo e qual é o seu tamanho?

	O messageID é exclusivo para um aplicativo e está limitado a oito caracteres. Pode ser alfanumérico.

7. Quais são os limites para Notificações push, em termos de tamanho de carga útil?

	O tamanho da carga útil da mensagem de {{site.data.keyword.mobilepushshort}} depende das restrições estabelecidas pelos Gateways (FCM/GCM, APNs) e
pelas plataformas do cliente. 

	Para o iOS 8 e mais recente, o tamanho máximo permitido é de 4 kilobytes. Observe que o APNs não envia notificações que excedam esse limite. Para o Android, o navegador Firefox, o navegador Chrome e os Apps Chrome e Extensões, há uma limitação de 4 kilobytes como o tamanho máximo permitido de carga útil da mensagem.	

8. As notificações enviadas são armazenadas em servidores BMS?

	Sim, as notificações são armazenadas por um período de sete dias. Recomenda-se não enviar nenhuma mensagem confidencial como notificação.

9. Posso enviar notificação para dispositivos no modo Doze?

	Este recurso não é suportado.	

10. Quais são os diferentes planos de precificação disponíveis para o serviço Push Notifications?

	Plano básico: está disponível por US$ 1/milhão de mensagens digitais. Com o plano básico, é possível enviar notificações push para um dispositivo exclusivo, um navegador, terminais ou um evento baseado em webhook. 

	Plano Lite: esse é um plano grátis que oferece cem mil mensagens digitais gratuitas por mês. No entanto, os serviços do plano Lite são excluídos após 30 dias de inatividade.	

11. Onde posso localizar mais informações, como tutoriais ou o que há de novo?

	Passe pelo [blog](http://push-notification-service.mybluemix.net/) do serviço Push Notifications.	

12. Há diferença entre uma notificação e uma mensagem?

	Sim. Uma _mensagem_ é o que o usuário está enviando para o serviço {{site.data.keyword.mobilepushshort}}. O serviço despacha isso como uma _notificação_ para o gateway de notificação (APNs/FCM) e será entregue para o dispositivo ou o navegador da web.

	Para cada mensagem enviada para o serviço, o público desejado recebe uma notificação.	

13. O painel de monitoramento de Notificações push exibe algum status para as mensagens enviadas?

	O utilitário de monitoramento exibe o status para cada mensagem enviada. As mensagens podem estar no estado a seguir:
	
	- Enviada: o número de dispositivos para os quais as notificações são enviadas.
	- Vista: o número de dispositivos nos quais as notificações chegaram.
	- Aberta: o número de dispositivos no quais a notificação foi aberta.
	- Inválida: o número de dispositivos nos quais o token é inválido.

	Para obter mais informações, veja o relatório de mensagens GET em [API de REST do IBM Push Notifications](https://mobile.ng.bluemix.net/imfpush/).	

14. A notificação push monitora a entrega de notificação push até o dispositivo do usuário final? Para ambos Android e iOS?

	As notificações push são monitoradas com base no número de notificações vistas ou abertas no dispositivo do usuário final. Isso está disponível para o Android e o iOS. ID do Dispositivo baseado em monitoramento não é suportado. 

15. Eu recebo a mensagem de que o servidor atualmente não é capaz de manipular solicitações? Como posso resolver isso?

	É possível ver o erro com o código de erro FPWSE0025E. Isso pode ser em razão de muitas solicitações para o servidor manipular. É possível tentar reenviar a solicitação posteriormente.	

16. Estou enviando uma notificação por tags, mas tenho uma longa lista de tags que podem ser difíceis de incluir manualmente. 
	
	É possível usar as APIs de REST para automatizar as adições de tags. Consulte [POST mensagens em massa](https://mobile.ng.bluemix.net/imfpush/).

17. Como posso filtrar a entrega de notificação push por informações armazenadas no dispositivo móvel do usuário?

	Isso deve ser manipulado no contexto de desenvolvimento de aplicativo.

18. Posso customizar ainda mais o monitoramento de notificação push para incluir relatório customizado, como relatório de entrega por segmentação?

	Este recurso não é suportado.

19.  Posso criar um segmento para usuário ou usuários de novo app que não tenham acessado o app móvel por algum tempo?

	Isso deve ser manipulado no contexto de desenvolvimento de aplicativo.


	


	
	




	


