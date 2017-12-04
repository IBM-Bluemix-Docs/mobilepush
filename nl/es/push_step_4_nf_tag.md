---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificaciones basadas en etiquetas
{: #tag_based_notifications}
Última actualización: 30 de junio de 2017
{: .last-updated}

Las notificaciones basadas en etiquetas son mensajes que están pensados para todos los dispositivos suscritos a una etiqueta determinada. Las notificaciones basadas en código permiten la segmentación de notificaciones en función de los temas o de las áreas de temas. Los destinatarios de la notificación pueden elegir recibir notificaciones sólo si es sobre un asunto o tema de su interés. Por lo tanto, la notificación basada en etiquetas proporciona un medio de segmentar destinatarios. Esta característica habilita la función de definir etiquetas y, a continuación, enviar y recibir mensajes por etiquetas. Un mensaje sólo se ha dirigido a las instancias de aplicación cliente (en móvil, navegador o como una app o extensión) que están suscritas a la etiqueta. Primero debe crear las etiquetas para la aplicación, configurar las suscripciones de etiquetas y, a continuación, iniciar las notificaciones basadas en etiquetas. Para enviar una notificación basada en etiquetas que utiliza la API REST, asegúrese de que los "tagNames" se proporcionen al publicarse en el recurso de mensajes.

Puede definir etiquetas y, a continuación, enviar y recibir mensajes mediante etiquetas. Primero debe crear las etiquetas para la aplicación, crear suscripciones y, a continuación, iniciar las notificaciones basadas en etiquetas. Para enviar una notificación basada en código utilizando la [API REST](https://mobile.{DomainName}/imfpush/){: new_window}, asegúrese de que se proporcionen los "tagNames" al publicar en el recurso de mensajes.


## Gestión de etiquetas
{: #manage_tags}

Utilice la consola de {{site.data.keyword.mobilepushshort}} para crear y suprimir etiquetas para la aplicación y, a continuación, iniciar las notificaciones basadas en etiquetas. La notificación basada en etiquetas se recibe en los dispositivos suscritos a las etiquetas.


### Creación de etiquetas
{: #create_tags}

Las notificaciones basadas en etiquetas son mensajes que están pensados para todos los dispositivos suscritos a una etiqueta determinada. Cada dispositivo se puede suscribir a cualquier número de etiquetas. 

1. En la consola {{site.data.keyword.mobilepushshort}}, seleccione el separador **Etiquetas**.
1. Pulse el botón **Crear etiqueta** +.   
   1. En el campo **Nombre**, especifique el nombre de la etiqueta. Por ejemplo, "cupones".
   1. En el campo **Descripción**, especifique una descripción de las etiquetas.
   1. Pulse **Guardar**.

1. En el área **Fragmentos de código**, seleccione la plataforma para la aplicación para móviles.
1. Modifique los fragmentos de código para manejar errores y, a continuación, copiar los fragmentos de código para cada etiqueta en la aplicación para móviles.

### Supresión de etiquetas
{: #delete_tags}

1. En el separador **Etiqueta**, seleccione la etiqueta que desea suprimir y pulse el icono **Suprimir**.
1. Pulse **Aceptar**.

Cuando se suprime una etiqueta, también se suprime toda la información asociada a dicha etiqueta, incluidos los suscriptores y los dispositivos. No es necesaria la anulación automática de la suscripción, porque la etiqueta ya no existe. No es necesario realizar más acciones en el lado del cliente.

### Edición de una descripción de etiquetas
{: #edit_tags}

1. Desde el separador **Etiqueta**, seleccione la etiqueta que desee editar.
1. Pulse el icono **Editar**.
1. Edite la descripción de etiquetas y, a continuación, pulse el botón **Guardar**.

## Obtener etiquetas
{: #get_tags}

Las etiquetas proporcionan una forma para enviar notificaciones de destino a usuarios en función de sus intereses, a diferencia de las difusiones generales que se envían a todas las aplicaciones. Puede crear y gestionar etiquetas con el separador Etiquetas en la consola de {{site.data.keyword.mobilepushshort}} o con las API REST. Puede utilizar fragmentos de código para gestionar y consultar las suscripciones de etiquetas para la aplicación móvil. Puede utilizar los fragmentos de código para obtener suscripciones, suscribirse a una etiqueta, anular la suscripción de una etiqueta u obtener una lista de las etiquetas disponibles. Copie estos fragmentos de código en su aplicación móvil.


- Para Android, consulte las API `getTags` y `getSubscriptions` en  [Etiquetas de obtención de notificaciones push de Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

- Para Cordova, consulte la API `retrieveAvailableTags()` API y `retrieveSubscriptions()` en [Etiquetas de obtención de notificaciones push en Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Para iOS, consulte la API `retrieveAvailableTagsWithCompletionHandler` en [Etiquetas de obtención de notificaciones push en Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags).

- Para navegadores web, consulte la API `retrieveAvailableTags()` en [Etiquetas de obtención de notificaciones push en navegadores web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).


## Suscribir etiquetas
{: #Subscribe_tags}

Utilice las siguientes API para permitir que los dispositivos recuperen etiquetas, se suscriban a una etiqueta, recuperen suscripciones y cancelen la suscripción de una etiqueta.

- Para Android, utilice las API `getTags`, `subscribe`, `getSubscriptions` y `unsubscribeFromTags`. Consulte [Etiquetas de suscripción a notificaciones push para Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags).

- Para Cordova, utilice las API `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` y `unsubscribe()`. Consulte [Etiquetas de suscripción a notificaciones push para Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Para iOS, utilice las API `retrieveAvailableTagsWithCompletionHandler`, `subscribeToTags`, `retrieveSubscriptionsWithCompletionHandler` y `unsubscribeFromTags`. Consulte [Etiquetas de suscripción a notificaciones push para Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags).

- Para navegadores web, utilice las API `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` y `unSubscribe()`. Consulte [Etiquetas de suscripción a notificaciones push para navegadores web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).

## Utilización de notificaciones basadas en etiquetas
{: #using_tags}

Las notificaciones basadas en etiquetas son mensajes que están pensados para todos los dispositivos suscritos a una etiqueta determinada. Cada dispositivo se puede suscribir a cualquier número de etiquetas. En este tema se describe cómo enviar notificaciones basadas en etiquetas. Las suscripciones las mantiene la instancia de IBM Cloud del servicio {{site.data.keyword.mobilepushshort}}. Cuando se suprime una etiqueta, también se suprime toda la información asociada a dicha etiqueta, incluidos los suscriptores y los dispositivos. No es necesaria ninguna anulación de la suscripción automática para esta etiqueta porque ya no existe y no es necesaria ninguna acción desde el lado del cliente.

Cree etiquetas en la pantalla **Etiquetas**. Para obtener más información sobre cómo crear etiquetas, consulte [Creación de etiquetas](t_manage_tags.html).

1. Desde la consola **Notificación Push**, pulse **Enviar notificaciones**.
1. Seleccione la opción **Dispositivo por etiqueta** en la lista desplegable **Enviar a**.
1. Busque las etiquetas que desee utilizar y selecciónelas.
![Pantalla de notificaciones](images/tag_notification.jpg)
1. En el campo **Texto del mensaje**, especifique texto que desee enviar como notificación a la audiencia suscrita.
1. Pulse **Enviar**.
