---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Etapa 3: Configurar uma instância de serviço 
{: #push_step_2}
Última atualização: 27 de junho de 2017
{: .last-updated}

Assegure-se de que tenha passado por [Obter suas credenciais de notificação](push_step_1.html).


## Para Android e Apps Chrome e Extensões
{: #push_step_2_Android}


Assegure-se de que tenha passado por [Obter suas credenciais de provedor de notificação](push_step_1.html) para configurar o projeto FCM e obter suas credenciais.

Para configurar as credenciais do FCM para aplicativos Android e Apps Google Chrome e Extensões, conclua as etapas a seguir:

1. Abra seu catálogo do IBM Cloud e, em seguida, clique na instância de serviço do {{site.data.keyword.mobilepushfull}} que você criou. 
2. Clique em **Gerenciar** > **Configurar**. 
3. Escolha uma das seguintes opções: 
	- Para Android: selecione **Dispositivo móvel** e, em seguida, atualize a guia Credenciais de push do FCM com o ID do emissor/Número do projeto e a Chave API. 
	- Para Apps Google Chrome e Extensões: selecione **Web** e, em seguida, atualize a guia Apps Chrome e Extensões com o ID do emissor/Número do projeto e Chave API. 
4. Clique em **Salvar**. Agora o serviço Push Notifications está configurado.

Sua próxima etapa é [configurar os SDKs do cliente de serviço Push](push_step_3.html).


## Para aplicativos Cordova 
{: #push_step_2_b}


Cordova é uma plataforma para criar aplicativos híbridos
com JavaScript, CSS e HTML. O serviço {{site.data.keyword.mobilepushshort}} suporta o desenvolvimento
de aplicativos iOS e Android baseados em Cordova.

Para permitir que os aplicativos Cordova recebam notificações push para seus dispositivos, passe por [Cordova Plugin Push SDK de Notificações push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).



## Para aplicativos iOS e navegador Safari 
{: #enable-push-ios-notifications}


Para usar o serviço {{site.data.keyword.mobilepushshort}} para enviar notificações, faça upload dos certificados `.p12` que você tinha criado na Etapa 1:[Obter suas credenciais de provedor de notificação](push_step_1.html). Esse certificado contém a chave privada e os certificados SSL que são necessários para construir e publicar seu aplicativo. A API REST também pode ser
usada para fazer upload de um certificado APNs.

**Nota**: depois que o arquivo `.cer` estiver
em seu acesso de cadeia de chaves, exporte-o para seu computador para criar um
certificado `.p12`.

Para obter mais informações sobre o uso de APNs, veja [iOS Developer Library: Local and Push Notification Programming Guide ![Ícone de link externo](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1){: new_window}.

Para configurar o APNs no console de serviços de Notificação push, conclua as etapas:

1. Selecione **Configurar** no console de serviços de Notificação push.
2. Escolha a opção **Móvel** para atualizar
as informações no formulário **Credenciais push de
APNs**.
3. Escolha uma das seguintes opções:
	- Para **Mobile** opção
		1. Selecione **Ambiente de simulação** (desenvolvimento) ou **Produção** (distribuição), conforme apropriado e, em seguida, faça upload do certificado `p.12` que você criou.
    ![Configurar o console de notificações push](images/wizard.jpg)

		1. No campo **Senha**, insira a senha que está
associada ao arquivo de certificado `.p12`; em seguida, clique em
**Salvar**.
	- Para a opção **web**
		- Na seção Push do Safari, atualize o formulário com as informações necessárias. 
		- **Nome do website**: este é o nome que você forneceu no centro de notificação.
		- **ID de push do website**: atualize com a sequência de domínio reversa para seu
ID de push do website. Por exemplo, web.com.acmebanks.www.
		- **URL do website**: forneça a URL do website que deve ser inscrita para
notificações push. Por exemplo, https://www.acmebanks.com.
		- **Domínios permitidos**: este é parâmetro opcional. Esta é a lista de websites
que solicitam permissão do usuário. Certifique-se de que as URLs sejam valores separados por vírgula. Observe
que o valor na URL do website será usado se isso não for fornecido. 
		- **Sequência de formatações de URL**: a URL a ser resolvida quando a notificação é clicada. Por exemplo, [ "https: //www.acmebanks.com " ]. Assegure-se de que a URL use o esquema HTTPS ou HTTP.
		-**Certificado de push da web do Safari**: faça upload do certificado .p12 e forneça a senha.
4. Clique em **Salvar**.	
![Console de Notificações push](images/push_configure_safari.jpg)	

Depois de ter configurado o serviço para aplicativos iOS, será necessário [Configurar os SDKs do cliente de serviço Push](push_step_3.html).


## Para navegadores Chrome e Firefox 
{: #push_step2_chromefirefox}

1. No console de Notificações push, selecione **Configurar**.
2. Selecione a guia Web.
	![Configurações de WebPush](images/webpush_configure.jpg)
3. Configure a chave API do FCM e a URL de seu website que será registrada para receber notificações push.
4. Clique em **Salvar**.
5. Depois de ter configurado o serviço, será necessário [Configurar os SDKs do cliente de serviço Push](push_step_3.html).
