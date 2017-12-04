---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Paso 3: Configurar una instancia de servicio 
{: #push_step_2}
Última actualización: 27 de junio de 2017
{: .last-updated}

Asegúrese de haber leído el apartado [Obtener las credenciales de la notificación](push_step_1.html).


## Para Android y apps y extensiones de Chrome
{: #push_step_2_Android}


Asegúrese de haber leído el apartado [Obtener las credenciales del proveedor de notificaciones](push_step_1.html) para configurar el proyecto FCM y obtener las credenciales.

Para configurar las credenciales de FCM para aplicaciones Android y apps y extensiones de Google Chrome, lleve a cabo los pasos siguientes:

1. Abra el catálogo de IBM Cloud y pulse la instancia del servicio {{site.data.keyword.mobilepushfull}} que ha creado. 
2. Pulse **Gestionar** &gt; **Configurar**. 
3. Seleccione una de las opciones siguientes: 
	- Para Android: Seleccione **Móvil** y, a continuación, actualice el separador Credenciales de push de GCM/FCM con el ID de remitente/número de proyecto y la clave de API. 
	- Para apps y extensiones de Google Chrome: Seleccione **Web** y, a continuación, actualice el separador Apps y extensiones de Chrome con el ID de remitente/número de proyecto y la clave de API. 
4. Pulse **Guardar**. Se configura el servicio de notificaciones push.

El siguiente paso consiste en [configurar el SDK de cliente de servicio push](push_step_3.html).


## Para aplicaciones de Cordova 
{: #push_step_2_b}


Cordova es una plataforma para crear aplicaciones híbridas con JavaScript, CSS y HTML. El servicio de {{site.data.keyword.mobilepushshort}} da soporte al desarrollo de aplicaciones para iOS y Android basadas en Cordova.

Para habilitar aplicaciones de Cordova para recibir notificaciones push en sus dispositivos, vaya a [SDK de push de plugins de Cordova de notificaciones push](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).



## Para aplicaciones de iOS y navegador Safari 
{: #enable-push-ios-notifications}


Para utilizar el servicio {{site.data.keyword.mobilepushshort}} para enviar notificaciones, cargue los certificados `.p12` que haya creado en el Paso 1: [Obtener las credenciales del proveedor de notificaciones](push_step_1.html). Este certificado contiene la clave privada y los certificados SSL necesarios para crear y publicar la aplicación. También se puede utilizar la API REST para subir un certificado de APNs.

**Nota**: Después de que el archivo `.cer` se encuentre en el acceso de cadena de claves, expórtelo al sistema para crear un certificado `.p12`.

Para obtener más información sobre cómo utilizar APNs, consulte en la [Biblioteca de desarrolladores de iOS la guía de programación de notificaciones push y locales ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ProvisioningDevelopment.html#//apple_ref/doc/uid/TP40008194-CH104-SW4){: new_window}.

Para configurar APNs en la consola de servicios de notificación push, siga estos pasos:

1. Seleccione **Configurar** en la consola de servicios de notificación push.
2. Elija la opción **Móvil** para actualizar la información del formulario **Credenciales de push de APNs**.
3. Seleccione una de las opciones siguientes:
	- Para la opción **Móvil**
		1. Seleccione **Sandbox** (desarrollo) o **Producción** (distribución) según convenga y, a continuación, cargue el certificado `p.12` que ha creado.
		  ![Establecer la consola de notificaciones push](images/wizard.jpg)

		1. En el campo **Contraseña**, especifique la contraseña asociada con el archivo de certificado `.p12` y, a continuación, pulse **Guardar**.
	- Para la opción **Web**
		- En la sección Push de Safari, actualice el formulario con la información necesaria. 
		- **Nombre del sitio web**: Este es el nombre que ha facilitado en el Centro de notificaciones.
		- **ID Push del sitio web**: Actualice con la serie de dominio invertido para el ID Push del sitio web. Por ejemplo, web.com.acmebanks.www.
		- **URL del sitio web**: Proporcione el URL del sitio web que debería estar suscrito a notificaciones push. Por ejemplo, https://www.acmebanks.com.
		- **Dominios permitidos**: Este es un parámetro opcional. Es la lista de sitios web que solicita permiso del usuario. Asegúrese de que las URL sean valores separados por coma. Tenga en cuenta que el valor del URL del sitio web se utilizará si no se proporciona. 
		- **Serie de formato de URL**: El URL a resolver cuando se pulse la notificación. Por ejemplo, ["https://www.acmebanks.com"]. Asegúrese de que el URL utilice el esquema http o https.
		-**Certificado push web de Safari**: cargue el certificado .p12 y proporcione la contraseña.
4. Pulse **Save**.	
![consola de notificaciones push](images/push_configure_safari.jpg)	

Una vez que haya configurado el servicio para las aplicaciones de iOS, debe [Configurar el SDK de cliente del servicio push](push_step_3.html).


## Para navegadores Chrome y Firefox 
{: #push_step2_chromefirefox}

1. En la consola de notificaciones push, seleccione **Configurar**.
2. Seleccione el separador web
	![Configuraciones WebPush](images/webpush_configure.jpg)
3. Configure la clave de la API de FCM/GCM y el URL del sitio web que se registrará para la recepción de notificaciones por push.
4. Pulse **Guardar**.
5. Una vez que haya configurado el servicio, debe [Configurar el SDK de cliente del servicio push](push_step_3.html).
