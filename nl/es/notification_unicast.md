---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificaciones de difusión única
{: #notification_unicast}


Las notificaciones de difusión única son mensajes destinados a un dispositivo o usuario específico. Dichas notificaciones destinadas a dispositivos no necesitan ninguna configuración adicional y están habilitadas de forma predeterminada cuando se habilita la aplicación para {{site.data.keyword.mobilepushshort}}.

Sin embargo, las notificaciones de difusión única destinadas a usuarios necesitan que se asocie un ID de usuario a un dispositivo en el momento de registrar el dispositivo móvil cliente o el navegador web o las apps y extensiones de Chrome a {{site.data.keyword.mobilepushshort}}.   

Normalmente, las aplicaciones cliente primero ejecutan un ciclo de autenticación en el que el usuario de la app móvil se autentica en un servicio de autenticación, como por ejemplo [Mobile Client Access](docs/services/mobileaccess/index.html). Si la autenticación es correcta, el ID de usuario autenticado se pasa a la API de registro del dispositivo push. 

Para enviar una notificación de difusión única mediante la API REST, asegúrese de que se proporcionan los deviceId o los userId al publicarse en un recurso de mensajes.
