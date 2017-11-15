---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Notificaciones de difusión 
{: #broadcast_notifications}

Las notificaciones de difusión son mensajes destinados a todas las instancias de una aplicación instalada en dispositivos móviles, navegadores o implementadas como instancias de apps o extensiones de Chrome y configuradas para el servicio {{site.data.keyword.mobilepushshort}}. Las notificaciones de difusión están habilitadas de forma predeterminada para cualquier aplicación habilitada para {{site.data.keyword.mobilepushshort}}.

Cuando una aplicación cliente se registra en el servicio {{site.data.keyword.mobilepushshort}}, puede comenzar a recibir difusiones. Las aplicaciones habilitadas para el servicio {{site.data.keyword.mobilepushshort}} tienen una suscripción predefinida en la etiqueta Push.ALL, que utiliza el servidor para transmitir mensajes de notificación a todos los dispositivos. Para enviar una notificación de difusión que utiliza la API Push REST, asegúrese de que el "destino" sea un archivo JSON vacío al publicar en recursos de mensajes.
