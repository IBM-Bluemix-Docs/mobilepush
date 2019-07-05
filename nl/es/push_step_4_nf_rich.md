---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, rich media notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificaciones Rich Media
{: #rich-media-notifications}

Puede habilitar Rich Media {{site.data.keyword.mobilepushshort}} en iOS 10 y posteriores. Las notificaciones push se pueden enviar con audio, vídeo, GIF e imágenes. 

Para configurar la aplicación de modo que reciba push completo en iOS 10, siga estos pasos:  

1. En Xcode, seleccione **File** > **Nuevo** > **Destino** > **Extensión de servicio de notificación**.
2. En el método `didReceive()` de `UNNotificationServiceExtension`, añada el siguiente código.
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

Para enviar Rich Media {{site.data.keyword.mobilepushshort}} desde la consola de push, asegúrese de especificar los campos de mensaje, título, subtítulo y attachmentURL.
