---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Paso 5: Enviar una notificación
{: #push_step_4}
Última actualización: 27 de junio de 2017
{: .last-updated}


Una vez que haya desarrollado sus aplicaciones, puede enviar notificaciones push básicas.

Para enviar notificaciones push básicas, siga estos pasos:

1. Seleccione **Enviar notificaciones** y para redactar un mensaje seleccione la opción **Enviar a**. Las opciones admitidas son **Dispositivo por etiqueta**, **ID de dispositivo**, **ID de usuario**, **Dispositivos Android**, **Dispositivos iOS**, **Notificaciones web** y **Todos los dispositivos**.
**Nota**: Cuando seleccione la opción **Todos los dispositivos**, todos los dispositivos suscritos a {{site.data.keyword.mobilepushshort}} recibirán notificaciones.
	
	![pantalla Notificaciones](images/tag_notification.jpg)

2. En el campo **Mensaje**, redacte el mensaje. Elija configurar los valores opcionales según sea necesario.
3. Pulse **Enviar**.
3. Verifique que los dispositivos o el navegador hayan recibido la notificación.

La captura de pantalla siguiente muestra un recuadro de alerta que maneja una notificación push
en el primer plano en un dispositivo Android.
	![Notificación push en primer plano en Android](images/Android_Screenshot.jpg)

La captura de pantalla siguiente muestra una notificación push en segundo plano para Android.
	![Notificación push en segundo plano en Android](images/background.jpg)

## Valores opcionales de Android 
{: #push_step_4_Android}

Puede personalizar aún más los valores de {{site.data.keyword.mobilepushshort}} para el envío de notificaciones a dispositivos Android. 

![Valores personalizados de Android](images/android_custom_settings.jpg)

Se admiten las siguientes opciones de personalización opcionales:

- Contraer clave: las claves contraídas se adjuntan a las notificaciones. Si llegan varias notificaciones de forma secuencial con la misma clave contraída cuando el dispositivo está desconectado, estas se contraerán. Cuando el dispositivo vuelva a conectarse, recibirá las notificaciones del servidor FCM/GCM y mostrará solo la última notificación transportada con la misma clave contraída. Si no se establece esta clave contraída, se almacenarán los mensajes nuevos y antiguos para entregarlos más adelante.
- Sonido: indica un fragmento de sonido que se reproducirá al recibir una notificación. Da soporte a la opción predeterminada o al nombre de un recurso de sonido incorporado en la app.
- Icono: Especifique el nombre del icono que se mostrará para la notificación. Asegúrese de que haya empaquetado el icono en la carpeta `res/drawable` con la aplicación cliente.
- Prioridad: especifica las opciones para asignar la prioridad de entrega a los mensajes. 
	- Para las prioridades `high` o `max` se emitirá una notificación de aviso.
	- Para las prioridades `low` o `default` no se abrirán las conexiones de red en un dispositivo en suspensión. 
- Visibilidad: puede optar por definir la opción de visibilidad de notificación en `public` o `private`. 
	- La opción `private` limita la visualización pública y puede habilitarla si el dispositivo está protegido mediante pin o un patrón y si el valor de notificación está establecido en **Ocultar contenido confidencial de notificación**. Cuando la visibilidad está establecida en `private`, debe mencionarse algún campo de `redacción`. Solo se mostrará el contenido especificado en el campo de `redacción` en la pantalla segura bloqueada del dispositivo. 
	- La opción `public` entregará notificaciones que se puedan leer libremente.
- Tiempo de duración: este valor se establece en segundos. Si no se especifica este parámetro, el servidor FCM/GCM almacenará el mensaje cuatro semanas e intentará entregarlo. La validez caduca transcurridas cuatro semanas. El intervalo de valores posible es de 0 a 2.419.200 segundos.
- Retrasar cuando esté desocupado: puede establecerlo en uno de los valores siguientes:
	- `True`, el servidor FCM/GCM no entregará la notificación cuando el dispositivo esté desocupado. 
	- `False`, garantiza que se entregan notificaciones aunque el dispositivo esté desocupado.
- Sinc: si esta opción se establece en `true`, se sincronizan las notificaciones de todos los dispositivos registrados. Si un usuario dispone de varios dispositivos con la misma aplicación instalada, al leer la notificación en un dispositivo se suprimirán las notificaciones del resto de los dispositivos. Debe asegurarse que está registrado al servicio {{site.data.keyword.mobilepushshort}} con userId para que esta opción funcione.
- Carga útil adicional: permite especificar valores personalizados de carga útil para las notificaciones.
- Notificación expandible: proporciona a los clientes una opción para expandir una notificación con más información; con la notificación contraída es visible una notificación básica. Se admiten las siguientes opciones:
	- Notificaciones de imagen grandes: Puede optar por incluir una imagen cuando la notificación se expanda. Proporcione un texto y un URL de título para la imagen.
	- Notificaciones de texto grandes: Puede optar por incluir texto adicional con un título. Proporcione el mensaje de texto grande y la información del texto de título.
	- Notificaciones de estilo de bandeja de entrada: Puede enviar la notificación con estilo de notificación de bandeja de entrada. Proporcione un texto de título y proporcione el mensaje en líneas.	 

## Valores de iOS opcionales 
{: #push_step_4_ios}

Puede personalizar los valores de {{site.data.keyword.mobilepushshort}} para el envío de notificaciones a dispositivos iOS. Se admiten las siguientes opciones de personalización.

- **Identificador**: Indica el número que se muestra en el identificador de la aplicación. El valor predeterminado es cero (0), que no mostraría un identificador. 
- **Sonido**: indica un fragmento de sonido que se reproducirá al recibir una notificación. Da soporte a la opción predeterminada o al nombre de un recurso de sonido incorporado en la app.
- **Carga útil adicional**: permite especificar valores personalizados de carga útil para las notificaciones.

También puede decidir habilitar las [notificaciones interactivas](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications) y las [notificaciones de Rich Media](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications).

## Supervisión de las notificaciones entregadas 
{: #push_step_4_monitor}

El servicio de {{site.data.keyword.mobilepushshort}} proporciona un programa de utilidad de supervisión para ayudarle a comprobar el estado de los mensajes enviados. Para configurar el programa de utilidad de supervisión, vaya a una de las opciones siguientes:

- [Habilitar supervisión para aplicaciones de Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
- [Habilitar supervisión para aplicaciones de iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
