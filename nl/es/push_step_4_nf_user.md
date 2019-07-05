---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, user-based, register device with user ID, synchronize user login and logout

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificaciones basadas en el usuario
{: #user_based_notifications}

Las {{site.data.keyword.mobilepushshort}} basadas en ID de usuario están pensadas para los usuarios de apps móviles con mensajes personalizados. Con las notificaciones basadas en usuarios, puede elegir notificar a individuos específicos según sus preferencias.

## Dispositivo de registro con ID de usuario
{: #register_device_wh_userid}

Para habilitar las notificaciones push destinadas por ID de usuario, asegúrese de registrar el dispositivo con un campo de ID de usuario definido.     

El ID de usuario puede ser cualquier serie que proporcione la aplicación a la API de registro del dispositivo. Normalmente, las aplicaciones móviles primero ejecutan un ciclo de autenticación en el que el usuario de la app móvil se autentica en un servicio de autenticación, como por ejemplo {{site.data.keyword.amafull}}. Si la autenticación es correcta, el ID de usuario autenticado se pasa a la API de registro del dispositivo push. 

Para registrarse para la notificación basada en userID, realice los pasos siguientes:

- [Registro de una aplicación de Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [Registro de una aplicación de iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Registro de una aplicación de Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Registro de una aplicación web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## Uso de notificaciones basadas en userId
{: #using_userid}

Las notificaciones basadas en userID son mensajes de notificación que están pensados para un usuario específico. Muchos dispositivos pueden registrarse con un usuario. Los pasos siguientes describen cómo enviar notificaciones basadas en el ID de usuario.

1. En la consola **Notificación push**, seleccione la opción **Enviar notificaciones**.
2. Seleccione **UserId** en la lista de opciones **Enviar a**.
3. En el campo **ID de usuario**, busque el ID de usuario que desee utilizar y, a continuación, pulse
**+Añadir**.![Pantalla Notificaciones](images/user_notification.jpg "Consola de notificaciones push que muestra el botón Añadir para el campo ID de usuario")
4. En el campo **Mensaje**, escriba el texto que desea enviar en la notificación.
5. Pulse **Enviar**.


## Sincronización del inicio y cierre de sesión de un usuario 
{: #sync_login_logout}

Puede elegir el envío de notificaciones únicamente si el usuario ha iniciado la sesión. 

Por ejemplo, piense en un dispositivo compartido por los miembros de un equipo de trabajo o por un equipo de trabajo, y habrá necesidad de dirigirse a determinados usuarios. En tal caso práctico, habría una secuencia de inicio y cierre de sesión de usuario. Este mecanismo de autenticación permite que la aplicación efectúe un seguimiento de la identidad del usuario de la aplicación en cuestión. De esta manera, se garantiza que las notificaciones destinadas a un usuario específico lleguen siempre únicamente a dicho usuario. Después de iniciar sesión, invoque la API de registro de dispositivos pasando el ID de usuario del usuario conectado. De la misma manera, antes de cerrar la sesión, invoque la API de `eliminación` de registro de dispositivos. La secuenciación de estas API push con el inicio y el cierre de sesión garantizará que las notificaciones destinadas a un determinado usuario se envíen únicamente a dicho usuario.
