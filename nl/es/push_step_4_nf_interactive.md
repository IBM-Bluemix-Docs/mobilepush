---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, interactive notification, silent notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificaciones interactivas y silenciosas  
{: #interactive-notifications}

Las notificaciones interactivas permiten a los usuarios responder a notificaciones sin tener que abrir la aplicación. Cuando llega una notificación interactiva, el dispositivo mostrará los botones de acción junto con el mensaje de notificación. 

**Nota:** no se soportan las notificaciones interactivas en dispositivos iOS con versiones anteriores a la 8. 

## Envío de notificaciones interactivas
{: #send_interactive_notifications}

La notificación interactiva puede enviarse mediante la consola de notificaciones push o mediante la [Documentación de la API REST](https://cloud.ibm.com/apidocs/push-notifications).


Desde la consola de {{site.data.keyword.mobilepushshort}}: 

1. En el separador de notificaciones, pulse **Enviar notificación**. 
2. Elija los destinatarios de la notificación y pulse **Siguiente**. 
3. En la página para crear notificaciones se puede enviar un push interactivo estableciendo Tipo en Predeterminado o Mixto y especificando Valor de categoría en el separador Opciones avanzadas. 

## Gestión de notificaciones interactivas 
{: #handle_interactive_notifications}

- Para iOS, vaya a [Habilitar y gestionar notificaciones interactivas en aplicaciones Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications).
- Para Cordova, vaya a [Habilitar y gestionar notificaciones interactivas en aplicaciones de Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications).
- Para Android, vaya [Habilitar y gestionar notificaciones interactivas en aplicaciones de Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications).


## Manejo de notificaciones silenciosas para iOS
{: #send_silent_notifications_for_ios}

Las notificaciones silenciosas no aparecen en la pantalla del dispositivo y la aplicación las recibe en segundo plano. Para obtener más información, consulte [Notificaciones silenciosas en dispositivos iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification).
