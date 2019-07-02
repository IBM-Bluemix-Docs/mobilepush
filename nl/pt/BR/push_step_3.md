---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, setup client sdk, android application, cordova application, iOS application, web browser

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Etapa 4: Configurar os SDKs do cliente de serviço
{: #push_step_3}

Assegure-se de que tenha [obtido suas credenciais de notificação](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) e tenha [configurado uma instância de serviço push](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2). Em seguida, será necessário configurar o aplicativo para usar o serviço Push Notifications para registrar, assinar e receber notificações push. 

Para configurar o SDK do cliente de serviço, passe pelas etapas a seguir com base em seu tipo de aplicativo.

## Em aplicativos Android
{: #push_step_3_Android}

É possível ativar os aplicativos do Android para receber notificações push para os seus dispositivos. O Android Studio é um pré-requisito e é o método recomendado para construir projetos Android. É essencial um conhecimento básico do Android Studio.

Assegure-se de que tenha passado por [Obter suas credenciais de provedor de notificação](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) para configurar o projeto FCM e obter suas credenciais.

Conclua as etapas para [Android SDK de Notificações push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) para permitir que apps Android recebam notificações push enviadas do serviço. 

1. Abra o app no Android Studio. Copie o arquivo `google-services.json` que você criou por meio da [Etapa 2: Obter suas credenciais](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) em seu diretório raiz do módulo do aplicativo Android. Observe que o arquivo `google-service.json` inclui os nomes de pacote adicionados.

    ![Incluindo o arquivo json no diretório raiz de seu aplicativo](images/FCM_7.jpg "Incluindo o arquivo json no diretório raiz de seu aplicativo")

2. Na janela Incluir Firebase no seu app Android, clique em **Continuar** e, em seguida, **Concluir**. 
3. Construa e execute o seu aplicativo. Em uma construção bem-sucedida, a mensagem `Construção de Gradle concluída` aparecerá.
4. Inclua o cliente Push SDK com Gradle.
	1. Configure seu [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) . 
	2. Configure o [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) arquivo.
	3. Inclua o arquivo `google-services.json` em seu diretório-raiz do módulo aplicativo Android.
5. Inicialize os SDKs. Veja [Inicializando o Core SDK e o Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
6. Construa o aplicativo.
7. É possível optar por registrar o serviço Push Notifications clicando no botão Registrar dispositivo no aplicativo ou passando por [Registrando no serviço usando o Push Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

Sua próxima etapa é [Enviar uma notificação](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Em aplicativos Cordova
{: #push_step_3_Cordova}

Cordova é uma plataforma para criar aplicativos híbridos
com JavaScript, CSS e HTML. O serviço Push Notifications suporta o desenvolvimento de aplicativos iOS e Android baseados em Cordova.

Para permitir que os aplicativos Cordova recebam notificações push para seus dispositivos, será necessário configurar o [Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

Depois de configurar o Cordova Plugin Push SDK, a próxima etapa será [Enviar uma notificação](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Em aplicativos iOS
{: #push_step_3_iOS}

Para permitir que os aplicativos iOS recebam {{site.data.keyword.mobilepushshort}} para seus dispositivos, será necessário configurar o [serviço iOS SDK for Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

Depois de configurar o iOS SDK, a próxima etapa será [Enviar uma notificação](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## Em navegadores da Web
{: #push_step_3_web}

Para permitir que os aplicativos de navegador recebam notificações push, será necessário configurar o [serviço Web SDK for Push Notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

Depois de configurar o Web SDK, a próxima etapa será [Enviar uma notificação](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

