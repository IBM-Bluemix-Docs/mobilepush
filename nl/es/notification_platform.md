---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificaciones basadas en plataforma
{: #notification_platform}


Las notificaciones se pueden definir para alcanzar una plataforma de dispositivo determinada. Por ejemplo, se puede enviar una notificación únicamente a todos los usuarios de Android o Google Chrome. Para enviar una notificación basada en plataforma que utilice la API REST, asegúrese de que se proporcionan plataformas de destino al publicar en un recurso de mensajes. Especifique las plataformas como una matriz. Las plataformas soportadas son las siguientes:

* A (Apple)
* G (Google)
* WEB_CHROME (push web del navegador Google Chrome)
* WEB_FIREFOX (push web del navegador Mozilla Firefox)
* WEB_SAFARI (push web del navegador Safari)
* APPEXT_CHROME (apps y extensiones de Google Chrome)
