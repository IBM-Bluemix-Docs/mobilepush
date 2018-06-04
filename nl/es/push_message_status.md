---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Estado de entrega del mensaje
{: #tag_based_notifications}
Última actualización: 21 de agosto de 2017
{: .last-updated}


Con el servicio de {{site.data.keyword.mobilepushshort}}, puede visualizar el estado de entrega de todas las notificaciones que se han enviado al servicio. 

Una vez enviado el mensaje, puede realizar un seguimiento de la información de entrega del mensaje mirando al estado de entrega. En un momento dado, el servicio muestra el estado de los 10 últimos mensajes que se encuentran disponibles dentro de un periodo de 90 días.

El separador **Mensajes** del servicio {{site.data.keyword.mobilepushshort}} muestra el estado de la notificación.

![estado de las notificaciones](images/notification_status_new.png)

1. **ID del mensaje**: Un único identificador para identificar un mensaje.

2. **Texto de mensaje**: Una plantilla de mensaje enviada a los usuarios de la app.

3. **Fecha**: Fecha y hora en que se envió el mensaje al servicio.

4. **Estado**: Ofrece un breve estado de resumen del mensaje. En función del estado de entrega del mensaje, es posible que vea el siguiente estado:

 - Aceptado: El mensaje ha sido aceptado para que sea entregado por el servicio de notificaciones push.
   
 - Asignando: El proveedor de notificaciones ha recibido la notificación, APNs, FCM o Web, y está a punto de ser asignada. Cualquier notificación que se encuentre en el proceso de ser asignada también puede devolver un error con el estado **La asignación ha fallado**.
 
 - Asignado: La notificación ha sido asignada por el proveedor de notificaciones.
 
 - Proceso: El mensaje ha sido procesado y se asignará a la pasarela del proveedor de notificaciones. Cualquier notificación que sea procesada puede devolver un fallo con el estado **El proceso ha fallado**.
 
 - Desconocido: No se puede determinar el estado de la notificación.
 
5. **Ver**: Muestra el estado de entrega de las notificaciones asignadas. Puede ver la información basada en los siguientes aspectos:

 - Categoría: Todo, Móvil, Web<!---and HTTP--->.
 
 - Estado del mensaje: Enviado, Visto, Abierto y No válido. 

![estado de las notificaciones](images/message_delivery_status_new.png)

6. **Opciones** - Ofrece estado detallado de una notificación. Se puede realizar el seguimiento del estado seleccionando el `ID de dispositivo` o el `ID de usuario` desde el menú desplegable. Puede resultar útil obtener el mensaje de estado detallado cuando realiza el seguimiento de un mensaje de error.

![estado detallado](images/detailed_message_delivery.png)

**Nota**: Solo se habilita la característica para los usuarios que han elegido el `plan Avanzado`. Seleccione **Plan** en la consola de servicio de {{site.data.keyword.mobilepushshort}} para [actualizar](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)


