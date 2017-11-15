---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Paso 4: Configurar el SDK del cliente de servicio
{: #push_step_3}
Última actualización: 27 de junio de 2017
{: .last-updated}

Asegúrese de haber [obtenido las credenciales de la notificación](push_step_1.html) y haber [configurado una instancia del servicio push](push_step_2.html). A continuación, debe configurar la aplicación para que utilice el servicio de notificaciones push para registrar, suscribirse y recibir notificaciones push. 

Para configurar un SDK del cliente de servicio, siga los pasos siguientes en función del tipo de aplicación.

## En aplicaciones Android
{: #push_step_3_Android}

Puede habilitar las aplicaciones de Android para recibir notificaciones push en sus dispositivos. Android Studio es un requisito previo y es el método recomendado para crear proyectos de Android. Es esencial tener conocimientos básicos de Android Studio.

Asegúrese de haber leído el apartado [Obtener las credenciales del proveedor de notificaciones](push_step_1.html) para configurar el proyecto FCM y obtener las credenciales.

Lleve a cabo los pasos del [SDK de Android de notificaciones push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) para habilitar apps de Android para recibir notificaciones push enviadas desde el servicio. 

1. Abra la app en Android Studio. Copie el archivo `google-services.json` que ha creado mediante [Paso 2: Obtener las credenciales](push_step_1.html) al directorio raíz del módulo de aplicación de Android. Tenga en cuenta que el archivo `google-service.json` incluye los nombres de paquete añadidos.

    ![Añadir el archivo json al directorio raíz de la aplicación](images/FCM_7.jpg)

2. En la ventana Añadir Firebase a la app de Android, pulse **Continuar** y, a continuación, **Finalizar**. 
3. Cree y ejecute la aplicación. Una vez que se cree correctamente, aparecerá el mensaje `Creación Gradle finalizada`.
4. Incluya el SDK de push del cliente con Gradle.
	1. Configure el archivo [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle). 
	2. Configure el archivo [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest).
	3. Añada el archivo `google-services.json` al directorio raíz del módulo de aplicación de Android.
5. Inicialice los SDK. Consulte [Inicialización del SDK de Core y el SDK de push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
6. Crear la aplicación.
7. Puede registrar el servicio de notificaciones push pulsando el botón Registrar dispositivo de la aplicación o mediante [Registro al servicio mediante el SDK de Android push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice).

El paso siguiente es [Enviar una notificación](push_step_4.html).


## En aplicaciones de Cordova
{: #push_step_3_Cordova}

Cordova es una plataforma para crear aplicaciones híbridas con JavaScript, CSS y HTML. El servicio de notificaciones push soporta el desarrollo de aplicaciones para iOS y Android basadas en Cordova.

Para habilitar aplicaciones de Cordova para que reciban notificaciones push en sus dispositivos, debe configurar el [SDK de push del plugin de Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

Una vez que haya configurado el SDK de push del plugin de Cordova, el paso siguiente es [Enviar una notificación](push_step_4.html).


## En aplicaciones iOS
{: #push_step_3_iOS}

Para habilitar aplicaciones de iOS para que reciban {{site.data.keyword.mobilepushshort}} en sus dispositivos, debe configurar el [servicio de notificaciones push para el plugin SDK de iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application). 

Después de configurar el SDK de iOS, el siguiente paso es [Enviar una notificación](push_step_4.html).


## En navegadores web
{: #push_step_3_web}

Para habilitar aplicaciones del navegador para recibir notificaciones push, debe configurar el [SDK Web para el servicio de notificaciones push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md).

Después de configurar el SDK Web, el siguiente paso es [Enviar una notificación](push_step_4.html).
