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

# Guía de aprendizaje de iniciación
{: #getting-started-with-push}

En esta guía de aprendizaje de iniciación de {{site.data.keyword.mobilepushfull}} se explica el proceso de habilitación de una app de Android para recibir notificaciones push y el envío de una notificación push básica a un dispositivo.
{:shortdesc}

<div id="prerequisites"></div>

## Antes de empezar
{: #prereqs}

Necesitará una [cuenta de IBM Cloud](https://console.bluemix.net/registration/), una instancia del servicio {{site.data.keyword.mobilepushshort}} y las siguientes herramientas y requisitos:

  * API de Android 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [app de ejemplo helloPush Android](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * Los SDK [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} y
  [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} se instalan mediante
  Android Studio o Gradle

## Paso 1: Configurar la {{site.data.keyword.mobilepushshort}} instancia para dispositivos Android

1. Copie el nombre de paquete del archivo de ejemplo `AndroidManifest.xml`.

2. Cree una app FCM y añada el nombre de paquete de su app de Android:
  1. En la [consola Firebase](https://console.firebase.google.com){: new_window}, pulse **Añadir proyecto**, proporcione un nombre  de proyecto, y pulse **Crear proyecto**.
  2. Pulse **Añadir Firebase a la app de Android**, especifique el nombre de paquete de app y pulse **Registrar app**. Pulse **Continuar &gt; Finalizar** para omitir las siguientes dos solicitudes. 

3. Añada las credenciales FCM a la instancia {{site.data.keyword.mobilepushshort}}:
  1. En la consola Firebase, vaya a **Configuración &gt; Configuración del proyecto &gt; Cloud Messaging** y copie la clave del servidor y el ID de remitente.
  2. En la consola {{site.data.keyword.Bluemix_notm}}, abra el panel de control de la instancia de servicio.
  3. Pulse **Gestionar > Configurar**.
  4. Especifique el ID de remitente y la clave de servidor en el campo **Credenciales de push de GCM/FCM**.

## Paso 2: Habilite la app de Android para enviar notificaciones push

1. Configure los archivos de nivel de proyecto `build.gradle` y de nivel del módulo `build.gradle` archivos:

  * Añada la dependencia SDK al archivo de nivel de proyecto `build.gradle`:
  
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

  * Añada las siguientes dependencias al archivo de nivel de módulo `build.gradle`:
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * Añada la dependencia de servicios Google Play al final del archivo de nivel de módulo `build.gradle` después de las dependencias:
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * Añada los permisos siguientes al archivo `AndroidManifest.xml` de la app:
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
  <uses-permission android:name="android.permission.GET_ACCOUNTS" />
  <uses-permission android:name="android.permission.USE_CREDENTIALS" />
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  ```
  {: codeblock}
  
  * Añade los valores de intención de notificación para la actividad. 
  
  Este valor inicia la app cuando el usuario pulsa la notificación recibida desde el área de notificación. Sustituya `<yourAndroidPackageName>`con el nombre del paquete de app utilizado en la app.
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * Actualice el servicio de intento de FCM y los filtros de intento de las notificaciones de sucesos `RECEIVE` y `REGISTRATION`:
  
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
  
2. Abra la app en Android Studio y añada el archivo `Google- services.json` al directorio raíz del módulo de la app.

3. Inicialice el SDK principal y el SDK de push. 

Un lugar común para colocar el código de inicialización es el método onCreate() de la actividad principal de la app de Android:

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... en el que `<bluemixRegionSuffix>` es la ubicación en la que se aloja la app. Puede utilizar uno de los siguientes valores:

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID es el valor de GUID de la app de envío y clientSecret es el valor secreto del cliente push. 

## Paso 3: Registre su dispositivo Android con la instancia {{site.data.keyword.mobilepushshort}}

1. Ejecute la app.

2. Utilice la API de MFPPush.register() para registrar el dispositivo y habilitar las notificaciones basadas en los usuarios.

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
 
 
 userId se utiliza para pasar el valor de ID único de usuario para registrar las notificaciones push. Asegúrese de proporcionar también el valor clientSecret.
 {: tip}
 
 ## Paso 4: Enviar una notificación push básica
 
 1. En la consola de {{site.data.keyword.Bluemix_notm}}, vaya al panel de control de la instancia de servicio.
 2. Pulse **Gestionar &gt; Enviar notificaciones**.
 3. Seleccione Dispositivos Android en el menú **Enviar a**.
 4. Escriba su mensaje y pulse **Enviar**. 
 
