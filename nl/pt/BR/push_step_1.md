
---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Etapa 2: Obter suas credenciais do provedor de notificações
{: #push_step_1}
Última atualização: 27 de junho de 2017
{: .last-updated}

Para configurar o serviço {{site.data.keyword.mobilepushshort}}, é necessário obter as credenciais necessárias com o provedor de notificação push. 

## Para Android
{: #push_step_1_android}

O Firebase Cloud Messaging (FCM) é o gateway usado para entregar notificações push para dispositivos Android, navegador Google Chrome e Apps Chrome e Extensões. Para configurar o serviço {{site.data.keyword.mobilepushshort}} no console, é necessário obter suas credenciais do FCM (ID do emissor e chave API). 

A chave API é armazenada com segurança e usada pelo serviço {{site.data.keyword.mobilepushshort}} para se conectar ao servidor FCM e o ID do emissor
(número do projeto) é usado pelo SDK do Android e o SDK do JS para Google Chrome e Mozilla Firefox no lado do cliente. 

Para configurar o FCM e obter suas credenciais, conclua as etapas:

1. Visite o [console do Firebase ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.firebase.google.com/?pli=1){: new_window}. Uma conta do usuário do Google é necessário. 
2. Selecione **Incluir projeto**. 
3. Na janela Criar um projeto, forneça um nome do projeto, escolha um país/região e clique em **Criar projeto**.
3. Na área de janela de navegação, selecione **Configurações** > **Configurações do projeto**.
4. Escolha a guia Cloud Messaging para obter suas credenciais do projeto - Chave API do servidor e um ID do emissor. Observe que a Chave do servidor listada no FCM é a mesma Chave de API do servidor.
   
	![Obtendo credenciais de FCM](images/FCM_settings_2.jpg)

Também seria necessário gerar o arquivo `google-services.json`. Conclua as etapas
a seguir:

1. No console do Firebase, clique no ícone **Configurações de projeto**.
    
	![Configurações de projeto do Firebase](images/FCM_settings_6.jpg)

3. Selecione o ícone **INCLUIR APP** ou **Incluir o Firebase em seu app Android** na guia Geral na área de janela Seus apps.
    
4. Na janela Incluir Firebase no seu app Android, inclua **com.ibm.mobilefirstplatform.clientsdk.android.push** como o Nome do pacote. O campo de apelido App é opcional. Clique em **INCLUIR APP**. 
    
	![Janela Incluindo o Firebase em seu Android](images/FCM_1.jpg)

5. Inclua o nome do pacote do seu aplicativo inserindo o nome do pacote na janela Incluir Firebase no seu app Android. O campo de apelido App é opcional. Clique em **REGISTER APP**. 

	![Incluindo o nome do pacote de seu aplicativo](images/FCM_settings_4.jpg)

6. O arquivo `google-services.json` é gerado. 


Depois de obter suas credenciais FCM e gerar o arquivo `google-services.json`, a próxima etapa será [Criar uma instância de serviço](push_step_2.html).

**Nota**: FCM é a nova versão do Google Cloud Messaging (GCM). Assegure-se de usar as credenciais do FCM para novos apps. Apps existentes continuarão a funcionar com configurações do GCM.

## Para iOS
{: #push_step_1_ios}

Para dispositivos e aplicativos iOS, o Apple Push Notification Service (APNs) permite que os desenvolvedores de aplicativos enviem notificações remotas da instância do serviço {{site.data.keyword.mobilepushshort}} no Bluemix (o provedor) para dispositivos e aplicativos iOS. Mensagens são enviadas para um aplicativo de
destino no dispositivo. 

É necessário obter e configurar suas credenciais do APNs. Os certificados do APNs são gerenciados com segurança pelo serviço {{site.data.keyword.mobilepushshort}} e usados para se conectar ao servidor APNs como um provedor.


### Registrando um ID de app
{: #push_step_1_ios_2}

O ID de app (o identificador de pacote configurável) é um
identificador exclusivo que identifica um aplicativo específico. Cada
aplicativo requer um ID de app. Serviços, como o serviço {{site.data.keyword.mobilepushshort}}, são configurados para o ID do app.

Assegure-se de que tenha uma conta do [Apple Developers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.apple.com/){: new_window}. Esse é um pré-requisito obrigatório.

2. Acesse o portal [Apple Developer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.apple.com){: new_window}, clique em **Member Center** e selecione **Certificados, Identificadores e Perfis**.
3. Acesse **Identificadores** > **IDs do Aplicativo seção**.
3. Na página **Registrando IDs do app**, forneça o nome do app no campo Nome da descrição do ID do app. Por exemplo: ACME Notificações push.
4. Forneça uma sequência para o Prefixo ID do app.  
4. Para o Sufixo de ID de app, escolha **ID de app explícito** e forneça um valor de ID de pacote. Recomenda-se fornecer uma sequência de estilo de nome de domínio reverso. Por exemplo: `com.ACME.push`.
5. Marque a caixa de seleção **Notificações push** e clique em **Continuar**.
6. Percorra as configurações e clique em **Registrar** > **Pronto**.

Seu app ID agora está registrado. 

   ![Registro AppID](images/push_ios_register_appid.jpg)
  

### Crie um certificado SSL de APNs de desenvolvimento e distribuição
{: #push_step_1_ios_3}

Antes de obter um certificado APNs, deve-se primeiro gerar uma solicitação de assinatura de certificado (CSR) e enviá-la para Apple, a autoridade de certificação (CA). A CSR contém informações que identificam sua empresa e suas chaves pública e privada usadas para assinar suas notificações push da Apple. Depois, gere o certificado SSL no
            portal de Desenvolvedor de iOS. O certificado, junto com
seu público e chave privada, é armazenado no Keychain Access.

É possível usar APNs de dois modos: 

* Modo de ambiente de simulação para desenvolvimento e teste.
* Modo de produção ao distribuir aplicativos por meio da App Store (ou outros mecanismos de distribuição da empresa).

É necessário obter certificados separados para
seus ambientes de desenvolvimento e distribuição. Os certificados são
associados a um ID de app para o app que é o destinatário das
notificações remotas. Para produção, é possível criar até dois
certificados. O Bluemix usa os certificados para estabelecer uma
conexão SSL com APNs.

<!-- Create a development and distribution SSL certificate. -->

1. Acesse o website [Apple Developer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.apple.com){: new_window}, clique em **Centro de membros** e selecione **Certificados, Identificadores e Perfis**.
2. Na área **Identificadores**, clique em
**IDs de app**.
3. Na lista de IDs de app, selecione o ID do app e, em seguida, selecione **Editar**.
4. Marque a caixa de seleção **Notificações push** e, em seguida:
	-  Na área de janela de certificado SSL de desenvolvimento, clique em **Criar certificado..**.
	-  Na área de janela de certificado SSL de produção, clique em **Criar certificado..**.

	![Certificados SSL de notificação push](images/certificate_createssl.jpg)

5. Quando a **tela Sobre a criação de uma solicitação de assinatura
de certificado (CSR)** for exibida, inicie o aplicativo
**Keychain Access** em seu Mac para criar uma solicitação de
assinatura de certificado (CSR). Clique em **Continuar**.
6. Para a opção de arquivo Fazer upload de CSR, clique em **Escolher arquivo** e selecione o arquivo `CertificateSigningRequest.certSigningRequest`. 
7. Clique em **Continuar**.
8. Na área de janela Fazer download, instalar e fazer backup, clique em **Download**. O `aps_development.cer` arquivo é transferido por download.
	
	![Fazer download de certificado](images/push_certificate_download.jpg)	
	
6. No menu, selecione **Keychain Access > Assistente de certificado > Solicitar um certificado de uma autoridade de certificação…** 
7. Em **Informações de certificado**, insira o endereço de
e-mail associado à sua conta de Desenvolvedor de app e um nome comum. Forneça um nome
significativo que ajude a identificar se é um certificado para desenvolvimento (ambiente
de simulação) ou distribuição (produção); por exemplo,
_sandbox-apns-certificate_ ou _production-apns-certificate_.
8. Selecione **Salvar no disco** para fazer download do arquivo
`.certSigningRequest` para sua área de trabalho e, em seguida, clique em
**Continuar**.
9. Na opção de menu **Salvar como**, nomeie o arquivo
`.certSigningRequest` e clique em **Salvar**.
10. Clique em **Pronto**. Agora você tem uma
CSR.
11. Retorne para a janela **Sobre como criar uma solicitação de
assinatura de certificado (CSR)** e clique em **Continuar**. 
12. Na tela **Gerar**, clique em
**Escolher arquivo ... **e selecione o arquivo CSR
salvo em sua área de trabalho. Em seguida, clique em **Gerar**.

	![Gerar certificado](images/generate_certificate.jpg)
13. Quando seu certificado estiver pronto, clique em
**Concluído**.
14. Na tela **Notificações push**, clique em
**Fazer download** para fazer download do seu certificado e depois
clique em **Concluído**. 
	
	![Fazer download de certificado](images/certificate_download.jpg)

15. No Mac, acesse **Keychain Access > Meus certificados** e
localize seu certificado recém-instalado. Dê um clique duplo no certificado
para instalá-lo no Keychain Access.
16. Selecione o certificado e a chave privada; em seguida, selecione
**Exportar** para converter o certificado no formato de troca de
informações pessoais (formato `.p12`).

	![Exportar certificado e chaves](images/keychain_export_key.jpg)
17. No campo **Salvar como**, dê um nome significativo para o certificado. Por
exemplo, `sandbox_apns.p12_certifcate` ou
`production_apns.p12`; em seguida, clique em **Salvar**.
	
	![Exportar certificado e chaves](images/certificate_p12v2.jpg)
18. No campo **Inserir uma senha**, insira
uma senha para proteger os itens exportados e clique em **OK**. É possível usar essa senha para configurar as definições do APNs no console do serviço Push Notifications.
	
	![Exportar certificado e chaves](images/export_p12.jpg)
19. O **Key Access.app** solicita que
você exporte sua chave da tela **Keychain**. Insira sua senha
administrativa para seu Mac para permitir que o sistema exporte esses itens; em seguida,
selecione a opção **Sempre permitir**. Um certificado
`.p12` é gerado em sua área de trabalho.


### Criando um perfil de fornecimento de desenvolvimento
{: #create-push-credentials-dev-profile}

O perfil de fornecimento funciona com o ID de app para
determinar quais dispositivos podem instalar e executar seu app e
quais serviços seu app pode acessar. Para cada ID de app, você cria
dois perfis de fornecimento: um para desenvolvimento e outro para
distribuição. Xcode usa o perfil de fornecimento de desenvolvimento
para determinar quais desenvolvedores podem criar o aplicativo e
quais dispositivos podem ser testados no aplicativo.

Certifique-se de registrar um ID de app, de ativá-lo para o serviço {{site.data.keyword.mobilepushshort}} e de configurá-lo para
usar um certificado SSL APNs de desenvolvimento e produção.

Crie um perfil de fornecimento de desenvolvimento, da seguinte forma:

1. Acesse o portal [Apple Developer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.apple.com){: new_window}, clique em **Member Center** e selecione **Certificados, Identificadores e Perfis**.
2. Acesse a [Mac Developer Library ![Ícone de link externo](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com/library/mac/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW62site){: new_window}, role até a seção **Creating Development Provisioning Profiles** e siga as instruções para criar um perfil de desenvolvimento.
**Nota**: Ao configurar um perfil de provisão de
desenvolvimento, selecione as opções a seguir:
	* **iOS App Development**
	* **Para apps iOS e watchOS **


### Criando um perfil de fornecimento de distribuição de
armazenamento
{: #create-push-credentials-apns-distribute_profile}

Use o perfil de fornecimento de armazenamento para
enviar seu app para distribuição para a App Store.

1. Acesse o portal [Apple Developer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.apple.com){: new_window}, clique em **Member Center** e selecione **Certificados, Identificadores e Perfis**.
2. Dê um clique duplo no perfil de fornecimento
transferido por download para instalá-lo em Xcode.

Depois de obter as credenciais, a próxima etapa será [Configurar uma instância de serviço](push_step_2.html).

## Para navegadores da web e Apps Chrome e Extensões
{: #configure-credential-for-browsers}

O serviço IBM {{site.data.keyword.mobilepushshort}} estende os recursos para enviar notificações para seu navegador e também para os Apps Chrome e Extensões.

A URL do website ou o nome de domínio de seu website é requerido pelo serviço {{site.data.keyword.mobilepushshort}} para identificar as solicitações que precisam ser permitidas. 

Por exemplo: `https://www.acmebanks.com`

Uma instância do serviço {{site.data.keyword.mobilepushshort}} suporta somente um nome de domínio por vez. Portanto, assegure-se de que o mesmo valor seja configurado para o Chrome, Firefox e Safari. Os navegadores Chrome e Safari requerem configuração adicional para push da web. Você precisaria de uma chave de API do FCM, pois um terminal do FCM é usado para entregar mensagens no Chrome. 

Para configurar o serviço para os navegadores Chrome, Firefox e para Apps e extensões do Chrome, veja [Configurar uma instância de serviço](push_step_2.html).


### Configurando para push da web do Safari 
{: #configure-safari}

A versão suportada para o serviço {{site.data.keyword.mobilepushshort}} no Safari é 10.0. É necessário gerar um certificado por meio de sua conta do Apple Developer, antes de poder configurar o navegador para receber notificações.

#### Gerando um certificado
{: #certificate-generation}

Assegure-se de ter uma conta do Apple Developer. É necessário
registrar um ID de push do website e gerar um certificado para
configurar o seu navegador Safari para receber notificações. As
etapas a seguir ajudarão na introdução.

1. No centro de Membro de desenvolvedor Apple, clique em
**Certificados, ID e perfis**. 
2. Clique em **Identificadores** e, sem
seguida, **IDs de push do website**.
3. Escolha criar uma nova entrada, selecionando o ícone de mais.
  ![Console de Notificações push](images/safari_1.jpg)

4. No painel Registrar ID de push do website, forneça uma
descrição do ID de push do website e um ID do identificador
apropriados. Recomenda-se que estejam no formato de nome de domínio reverso, começando com `web`. Por exemplo: `web.com.acmebanks`.
5. Registre o ID de push do website. Agora, você tem seu ID de push do website. 
6. Selecione **Editar** para criar um certificado a ser usado pelo ID de push do
website.
7. Na janela Assistente de certificado, forneça seu ID do
e-mail e um nome comum. Deixe o endereço de e-mail da Autoridade
de certificação em branco.
8. Clique em **Salvar em disco** e
selecione **Continuar**.
9. Escolha para salvar o certificado em uma pasta
apropriada.
10. Escolha `.certSigningRequest` criado no disco, quando solicitado, no assistente
para gerar o certificado. Certifique-se de fazer download do certificado de push do website criado no
formato `.cer`.
11. Abra o certificado na ferramenta KeyChain Access. Clique com o botão direito e exporte
como um certificado p12. Observe a senha fornecida durante a geração do certificado p12.

Depois de gerar um certificado, a próxima etapa será [Configurar uma instância de serviço](push_step_2.html).

