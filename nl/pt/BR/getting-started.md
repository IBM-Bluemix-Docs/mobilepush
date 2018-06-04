---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Tutorial Introdução
{: #getting-started-with-push}

Neste tutorial de introdução do {{site.data.keyword.mobilepushfull}}, passamos pelo processo de ativação de um app Android para receber notificações push e enviar uma notificação push básica para um dispositivo.
{:shortdesc}

<div id="prerequisites"></div>

## Antes de começar
{: #prereqs}

Você precisará de uma [Conta do IBM Cloud](https://console.bluemix.net/registration/), de uma instância do
serviço {{site.data.keyword.mobilepushshort}} e das ferramentas e dos requisitos a seguir:

  * API do Android 15 +
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android helloPush app de amostra](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * Os SDKs [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} e
[BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} instalados usando
o Android Studio ou o Gradle

## Etapa 1: Configurar sua instância de {{site.data.keyword.mobilepushshort}} para dispositivos Android

1. Copie o nome do pacote do arquivo `AndroidManifest.xml` de amostra.

2. Crie um app FCM e inclua o nome do pacote de seu app Android:
  1. No [console do Firebase](https://console.firebase.google.com){: new_window}, clique em **Incluir projeto**, forneça um
nome de projeto e clique em **Criar projeto**.
  2. Clique em **Incluir o Firebase em seu app Android**, insira o nome do pacote do app e clique em **Registrar app**. É possível ignorar os
dois próximos prompts clicando em **Continuar > Concluir**. 

3. Inclua as credenciais do FCM em sua instância do {{site.data.keyword.mobilepushshort}}:
  1. No console do Firebase, acesse **Configurações > Configurações do projeto > Cloud Messaging** e copie a chave Servidor e o ID do emissor.
  2. No console do {{site.data.keyword.Bluemix_notm}}, abra o painel para sua instância de serviço.
  3. Clique em **Gerenciar > Configurar**.
  4. Insira o ID do emissor e a chave do servidor no campo **Credenciais de Push do GCM/FCM**.

## Etapa 2: Ativar o app Android para enviar notificações push

1. Configure os arquivos de nível de projeto `build.gradle` e nível de módulo `build.gradle`:

  * Inclua a dependência SDK no arquivo de nível de projeto `build.gradle`:
  
  ```
  dependencies {
  ........
  compile group: 'com.ibm.mobilefirstplatform.clientsdk.android',
      name: 'push',
      version: '3.+',
      ext: 'aar',
      transitive: true
  .......
	      }
  ```
  {: codeblock}

  * Inclua as dependências a seguir no arquivo de nível de módulo `build.gradle`:
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    Classpath 'com.google.gms:google-services: 3.0.0' }
  ```
  {: codeblock}
  
  * Inclua a dependência de serviços do Google Play no término do arquivo de nível de módulo `build.gradle` depois das dependências:
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * Inclua as permissões a seguir no arquivo `AndroidManifest.xml` de seu app:
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.USE_CREDENTIALS" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  ```
  {: codeblock}
  
  * Inclua as configurações de intento de notificação da atividade. 
  
  Essa configuração inicia o app quando o usuário clica na notificação recebida da área de notificação. Substitua
  `<yourAndroidPackageName>` pelo nome do pacote do app usado em seu app.
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * Atualize o serviço de intento FCM e os filtros de intento das notificações de evento `RECEIVE` e `REGISTRATION`:
  
  ```
  <service android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushIntentService"
    android:exported="true" >
  <intent-filter>
     <action android:name="com.google.firebase.MESSAGING_EVENT" />
  </intent-filter>
  </service>
  <service
  android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPush"android:exported="true" >
  <intent-filter>
   <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
  </intent-filter>
  </service>
  ```
  {: codeblock}
  
2. Abra o app no Android Studio e inclua o arquivo `google-services.json` no diretório-raiz do módulo de app.

3. Inicialize o Core SDK e o Push SDK. 

Um local comum para colocar o código de inicialização é o método onCreate() da atividade principal no app Android:

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... em que `<bluemixRegionSuffix>` é o local no qual o app está hospedado. É possível usar qualquer um dos valores a seguir:

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID é o valor GUID do app push e clientSecret é o valor secreto do cliente push. 

## Etapa 3: Registrar seu dispositivo Android com sua instância do {{site.data.keyword.mobilepushshort}}

1. Execute seu app.

2. Use a API MFPPush.register() para registrar seu dispositivo para ativar notificações baseadas no usuário.

```
//Register the device to Push Notifications service instance
 push.registerDeviceWithUserId("userId",new MFPPushResponseListener<String>() {
 @Override
    	public void onSuccess(String response) {
 //Handle successful device registration here
 }
 @Override
    public void onFailure(MFPPushException ex) {
 //Handle failure in device registration here
 }
 });
 ```
 {: codeblock}
 
 
 userId é usado para passar o valor de ID de usuário exclusivo para registrar notificações push. Certifique-se de também fornecer o valor clientSecret.
 {: tip}
 
 ## Etapa 4: Enviar uma notificação push básica
 
 1. No console do {{site.data.keyword.Bluemix_notm}}, acesse o painel de sua instância de serviço.
 2. Clique em **Gerenciar > Enviar Notificações**.
 3. Selecione Dispositivos Android no menu **Enviar para**.
 4. Insira sua mensagem e clique em **Enviar**. 
 
