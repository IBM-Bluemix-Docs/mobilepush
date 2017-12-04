---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Preguntas más frecuentes 
{: #faq}


1. ¿Por qué se invalidan mis señales?
	
	Para los registros de dispositivos, navegadores y apps y extensiones de Chrome, el servicio de notificaciones push mantiene una referencia única para las señales emitidas a partir de proveedores de notificaciones -
APNs para Apple o FCM para Google. El proveedor de notificación del servicio puede invalidar las señales por diversos motivos. 

	Por ejemplo, se puede producir durante la desinstalación de una app en el dispositivo. En tal caso, cuando se intenta entregar una notificación en función de la respuesta de los proveedores que ha invalidado el dispositivo, el servicio {{site.data.keyword.mobilepushshort}} eliminará los registros de dispositivos o navegadores web. Esto a su vez podría restringir los intentos consecuentes al enviar notificación a los dispositivos invalidados. 

	También puede obtener el problema si tiene un dispositivo sin registrar.

	Asegúrese de obtener una clave de API de servidor válida y un ID de remitente para continuar. Consulte [Obtener las credenciales del proveedor de notificaciones](push_step_1.html).


2. ¿Por qué obtengo el mensaje "La notificación no funciona para WEB_Chrome."al intentar inicializar SDK web de push?

	Es posible que haya cambiado las credenciales de FCM/GCM del SDK web de push y no pueda realizar la entrega del mensaje en el navegador Chrome. Asegúrese de invocar "bmsPush.unRegisterDevice" para evitar anomalías.

3. Obtengo el mensaje "No se admiten trabajadores de servicio en este navegador" al intentar inicializar el SDK web de push. ¿Cuál puede ser el problema? 

	Siga los pasos mencionados en [Paso 3: Configurar el SDK del cliente de servicio Push](push_step_3.html).	Asegúrese también de:
 
	1. Utilizar el método de inicio adecuado. 
	1. Incluir el archivo `manifest.json` en la carpeta raíz.
	1. Alojar su sitio web. Preferiblemente, cree un iniciador `node.js` en IBM Cloud para probarlo. Por ejemplo: https://<mysamplewebsite>.mybluemix.net/.	

4. ¿Cómo se resuelven los errores de configuración web de un envío Web?

	Los errores de push web procedentes de `BMSPushSDK.js` contienen información sobre el error.  Consulte [Resolución de problemas](push_troubleshooting.html).	

5. ¿Persisten las notificaciones si los dispositivos están fuera de línea?

	Esta función depende del proveedor de notificaciones.	

6. ¿El ID messageID es único para una aplicación? ¿Cuál es su tamaño?

	El ID messageID es único para la aplicación y está limitado a ocho caracteres, que pueden ser alfanuméricos.

7. ¿Cuáles son los límites para las notificaciones Push en términos de tamaño de carga útil?

	El tamaño de carga útil de los mensajes de {{site.data.keyword.mobilepushshort}} depende de las restricciones diseñadas por las pasarelas (FCM/GCM, APNs) y las plataformas cliente. 

	Para iOS 8 y versiones posteriores, el tamaño máximo permitido es de 4 kilobytes. Tenga en cuenta que los APNs no envían notificaciones que superen este límite. Para Android, el navegador Firefox, el navegador Chrome y apps y extensiones de Chrome existe una limitación de 4 kilobytes como tamaño máximo de carga útil del mensaje permitido.	

8. ¿Se almacenan en servidores BMS las notificaciones que se envían?

	Sí, las notificaciones se almacenan durante un período de siete días. Se recomienda no enviar ningún mensaje confidencial como notificación.

9. ¿Se puede enviar una notificación a dispositivos en modalidad Doze?

	No se admite esta función.	

10. ¿Cuáles son los diferentes planes de precios disponibles para el servicio de notificaciones Push?

	Plan básico: Esta opción está disponible por 1,00 USD/un millón de mensajes digitales. Con el plan básico, puede enviar notificaciones a un dispositivo único, un navegador, puntos finales o suceso basado en webhook. 

	Plan Lite: Es un plan gratuito que incluye cien mil mensajes digitales gratuitos por mes. Los servicios del plan Lite se suprimen tras 30 días de inactividad.	

11. ¿Dónde se puede encontrar más información como guías de aprendizaje o novedades?

	Pase por el [blog](http://push-notification-service.mybluemix.net/) del servicio de notificaciones Push.	

12. ¿Hay diferencia entre una notificación y un mensaje?

	Sí. Un _mensaje_ es lo que el usuario envía al servicio {{site.data.keyword.mobilepushshort}}. El servicio envía el mensaje como una _notificación_ a la pasarela de notificaciones (APNs/FCM) y este se entrega al dispositivo o al navegador web.

	Para cada mensaje que se envía al servicio, los usuarios de destino reciben una notificación.	

13. ¿El panel de instrumentos de supervisión de notificaciones Push muestra algún estado para los mensajes que se envían?

	La utilidad de supervisión muestra el estado de cada mensaje enviado. Los mensajes pueden tener los estados siguientes:
	
	- Enviado: El número de dispositivos a los que se envían notificaciones.
	- Visto: El número de dispositivos a los que han llegado las notificaciones.
	- Abierto: El número de dispositivos en el que se ha abierto la notificación.
	- No válido: El número de dispositivos en los que la señal no es válida.

	Para obtener más información, consulte el informe de mensajes GET en la [API REST de IBM Push Notifications](https://mobile.ng.bluemix.net/imfpush/).	

14. ¿Las notificaciones push supervisan la entrega de notificaciones hasta el dispositivo del usuario final? ¿Están disponibles tanta para Android como para iOS?

	Las notificaciones Push se supervisan en función del número de notificaciones que se ven o abren desde el dispositivo de usuario final. Están disponibles tanto para Android como para iOS. No se admite la supervisión basada en el ID de dispositivo. 

15. ¿Por qué recibo un mensaje que indica que actualmente el servidor no puede gestionar solicitudes? ¿Cómo se puede resolver?

	Es posible que vea el error con el código de error FPWSE0025E. Puede que haya demasiadas solicitudes en el servidor y este no pueda gestionarlas. Intente enviar la solicitud de nuevo más tarde.	

16. Envío notificaciones por etiquetas, pero tengo una lista larga de etiquetas que pueden ser difíciles de añadir manualmente. 
	
	Puede utilizar las API REST para automatizar las adiciones de etiquetas. Consulte [mensajes POST masivos](https://mobile.ng.bluemix.net/imfpush/).

17. ¿Cómo se pueden filtrar la entrega de notificaciones Push por información almacenada en el dispositivo móvil del usuario?

	Esto debe gestionarse en el contexto del desarrollo de aplicaciones.

18. ¿Puedo personalizar aún más la supervisión de notificaciones Push para añadir informes personalizados como informes de entrega por segmentación?

	No se admite esta función.

19.  ¿Puedo crear un segmento para un usuario o usuarios nuevos de la app que no hayan accedido a la app para móviles desde hace tiempo?

	Esto debe gestionarse en el contexto del desarrollo de aplicaciones.


	


	
	




	


