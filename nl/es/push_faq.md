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


# Preguntas más frecuentes 
{: #faq}

### ¿Por qué se invalidan mis señales?
{: #faq-tokens}	

Para los registros de dispositivos, navegadores y apps y extensiones de Chrome, el servicio de notificaciones push mantiene una referencia única para las señales emitidas a partir de proveedores de notificaciones -
APNs para Apple o FCM para Google. El proveedor de notificación del servicio puede invalidar las señales por diversos motivos. 

Por ejemplo, se puede producir durante la desinstalación de una app en el dispositivo. En tal caso, cuando se intenta entregar una notificación en función de la respuesta de los proveedores que ha invalidado el dispositivo, el servicio {{site.data.keyword.mobilepushshort}} eliminará los registros de dispositivos o navegadores web. Esto a su vez podría restringir los intentos consecuentes al enviar notificación a los dispositivos invalidados. 

También puede obtener el problema si tiene un dispositivo sin registrar.

Asegúrese de obtener una clave de API de servidor válida y un ID de remitente para continuar. Consulte [Obtener las credenciales del proveedor de notificaciones](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1).

### ¿Por qué obtengo *La notificación no funciona para WEB_Chrome.* al intentar inicializar el SDK de push web?
{: #faq-web-chrome}	

Es posible que haya cambiado las credenciales de FCM del SDK de push web y no pueda realizar la entrega del mensaje en el navegador Chrome. Asegúrese de que invoca *bmsPush.unRegisterDevice* para evitar anomalías.

### Obtengo el mensaje *No se admiten trabajadores de servicio en este navegador* al intentar inicializar el SDK de push web. ¿Cuál puede ser el problema? 
{: #faq-service-workers}	

Siga los pasos mencionados en [Paso 3: Configurar el SDK del cliente de servicio Push](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3). Asegúrese también de:

1. Utilizar el método de inicio adecuado. 
2. Incluir el archivo `manifest.json` en la carpeta raíz.
3. Alojar su sitio web. Preferiblemente, cree un iniciador `node.js` en IBM Cloud para probarlo. Por ejemplo: https://<mysamplewebsite>.cloud.ibm.com/.	

### ¿Cómo se resuelven los errores de configuración web de un envío Web?
{: #faq-web-config-errors}	

Los errores de push web procedentes de `BMSPushSDK.js` contienen información sobre el error. Consulte [Resolución de problemas](/docs/services/mobilepush?topic=mobile-pushnotification-errors).	

### ¿Persisten las notificaciones si los dispositivos están fuera de línea?
{: #faq-notification-persist}	

Esta función depende del proveedor de notificaciones.	

### ¿El ID messageID es único para una aplicación? ¿Cuál es su tamaño?
{: #faq-messageid}	

El ID messageID es único para la aplicación y está limitado a ocho caracteres. Puede ser alfanumérico.

### ¿Cuáles son los límites para las notificaciones Push en términos de tamaño de carga útil?
{: #faq-limits-push-payload-size}	

El tamaño de carga útil de los mensajes de {{site.data.keyword.mobilepushshort}} depende de las restricciones diseñadas por las pasarelas (FCM, APNs) y las plataformas cliente. 

Para iOS 8 y versiones posteriores, el tamaño máximo permitido es de 4 kilobytes. Tenga en cuenta que los APNs no envían notificaciones que superen este límite. Para Android, el navegador Firefox, el navegador Chrome y apps y extensiones de Chrome existe una limitación de 4 kilobytes como tamaño máximo de carga útil del mensaje permitido.	

### ¿Se almacenan en servidores BMS las notificaciones que se envían?
{: #faq-bms-servers}	

Sí, las notificaciones se almacenan durante un período de noventa días. Se recomienda no enviar ningún mensaje confidencial como notificación.

### ¿Se puede enviar una notificación a dispositivos en modalidad Doze?
{: #faq-doze-mode}	

No se admite esta función.	

### ¿Cuáles son los diferentes planes de precios disponibles para el servicio de notificaciones Push?
{: #faq-pricing-plans}	

* <b>Plan avanzado</b>: está disponible por $100,00 USD/Instancia, $0,50 USD/Millón de mensajes digitales y $0,50 USD/Millón de dispositivos direccionables. Con el plan avanzado, puede enviar notificaciones push a 1 millón de dispositivos direccionables y 100 millones de mensajes digitales. El plan avanzado incluye funciones como parametrizar mensajes y realizar el seguimiento del ciclo de vida de mensaje de extremo a extremo.

* <b>Plan básico</b>: está disponible por $1,00 USD/Millón de mensajes digitales. Con el plan básico, puede enviar notificaciones a un dispositivo único, un navegador, puntos finales o suceso basado en webhook. 

* <b>Plan Lite</b>: plan gratuito que incluye cien mil mensajes digitales gratuitos por mes. Los servicios del plan Lite se suprimen tras 30 días de inactividad.	

### ¿Dónde se puede encontrar más información como guías de aprendizaje o novedades?
{: #faq-what-is-new}	

Visite los [vídeos](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA) del servicio de notificaciones push.	

### ¿Hay diferencia entre una notificación y un mensaje?
{: #faq-diff-notification-message}	

Sí. Un _mensaje_ es lo que el usuario envía al servicio {{site.data.keyword.mobilepushshort}}. El servicio envía el mensaje como una _notificación_ a la pasarela de notificaciones (APNs/FCM) y este se entrega al dispositivo o al navegador web.

Para cada mensaje que se envía al servicio, los usuarios de destino reciben una notificación.	

### ¿El panel de control de supervisión de notificaciones Push muestra algún estado para los mensajes que se envían?
{: #faq-push-monitor-dashboard}	

La utilidad de supervisión muestra el estado de cada mensaje enviado. Los mensajes pueden tener los estados siguientes:
	
* Enviado: El número de dispositivos a los que se envían notificaciones.
* Visto: El número de dispositivos a los que han llegado las notificaciones.
* Abierto: El número de dispositivos en el que se ha abierto la notificación.
* No válido: El número de dispositivos en los que la señal no es válida.

Para obtener más información, consulte el informe de mensajes GET en la [API REST de IBM Push Notifications](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).	

### ¿Las notificaciones push supervisan la entrega de notificaciones hasta el dispositivo del usuario final? ¿Están disponibles tanta para Android como para iOS?
{: #faq-end-user-device}	

Las notificaciones Push se supervisan en función del número de notificaciones que se ven o abren desde el dispositivo de usuario final. Están disponibles tanto para Android como para iOS. No se admite la supervisión basada en el ID de dispositivo. 

### ¿Por qué recibo un mensaje que indica que actualmente el servidor no puede gestionar solicitudes? ¿Cómo se puede resolver?
{: #faq-server-unable-to-handle-requests}	

Es posible que vea el error con el código de error FPWSE0025E. Puede que haya demasiadas solicitudes en el servidor y este no pueda gestionarlas. Intente enviar la solicitud de nuevo más tarde.	

### Envío notificaciones por etiquetas, pero tengo una lista larga de etiquetas que pueden ser difíciles de añadir manualmente. 
{: #faq-tag-based-notification}	

Puede utilizar las API REST para automatizar las adiciones de etiquetas. Consulte [mensajes POST masivos](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).

### ¿Cómo se pueden filtrar la entrega de notificaciones Push por información almacenada en el dispositivo móvil del usuario?
{: #faq-filter-device}	

Esto debe gestionarse en el contexto del desarrollo de aplicaciones.

### ¿Puedo personalizar aún más la supervisión de notificaciones Push para añadir informes personalizados como informes de entrega por segmentación?
{: #faq-customize-delivery-report}	

No se admite esta función.

### ¿Puedo crear un segmento para un usuario o usuarios nuevos de la app que no hayan accedido a la app para móviles desde hace tiempo?
{: #faq-create-segment}	

Esto debe gestionarse en el contexto del desarrollo de aplicaciones.
	
### ¿Puedo registrar/actualizar dispositivos móviles de manera masiva utilizando las API REST?
{: #faq-register-mobile-devices}	

Por diseño, el registro/actualización de un dispositivo se invoca desde las aplicaciones móviles utilizando el SDK. No se admiten registros/actualizaciones de forma masiva a través de las API REST. Si se van a invocar muchos registros/actualizaciones de dispositivos simultáneamente utilizando las API REST, esto puede tardar mucho tiempo o puede fallar.	

### ¿Cómo envío notificaciones push o utilizo las API REST cuando no tengo el secreto de app (appSecret)?
{: #faq-rest-api-appsecret}	

Debido a que el servicio {{site.data.keyword.mobilepushshort}} ha adoptado IAM, se muestra una `apiKey` en lugar del
`appSecret` cuando el usuario crea las credenciales del servicio.

Para utilizar las API REST, debe generar la señal de acceso utilizando el mandato curl siguiente:

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

Tras generar la señal de acceso utilizando el mandato curl anterior, ahora puede operar con las API REST pasando `Bearer <value of access_token>` en la cabecera Authorization.

Por ejemplo:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \
   "message": { \
     "alert": "Notification alert message" \
   } \
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
