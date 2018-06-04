----

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Seguridad en notificaciones push 
{: #overview-push}
Última actualización: 13 de julio de 2017
{: .last-updated}


Las API de {{site.data.keyword.mobilepushshort}} se protegen mediante dos tipos de secretos:

- **appSecret**: `appSecret` protege las API que suelen invocar las aplicaciones de fondo, como por ejemplo la API para enviar {{site.data.keyword.mobilepushshort}} y la API para configurar las opciones.
- **clientSecret**:  `clientSecret` protege las API que suelen invocar las aplicaciones de clientes móviles. Sólo hay una API relacionada con el registro de un dispositivo con un ID de usuario asociado que requiere este `clientSecret`. Ninguna del resto de las API invocadas desde los clientes móviles requiere el `clientSecret`. 

`appSecret` y `clientSecret` se asignan a todas las instancias de servicio en el momento de enlazar una aplicación con el servicio {{site.data.keyword.mobilepushshort}}. Consulte la documentación de las [API REST ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](https://imfpush.{DomainName}/imfpush/) para obtener información sobre cómo se pasan los secretos y a qué API.

## appSecret 
{: #push-api-rest-secret}

Cuando una aplicación se enlaza a las {{site.data.keyword.mobilepushshort}}, el servicio generará un appSecret (una clave exclusiva) y la pasa en la cabecera de respuesta. Si está utilizando IBM {{site.data.keyword.mobilepushshort}} para la API REST de IBM Cloud, utilice la referencia de la API REST para obtener información sobre qué API se deben proteger. Para obtener información, consulte la [API REST de Push ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](https://imfpush.{DomainName}/imfpush/){: new_window}.

La cabecera de la solicitud debe contener el appSecret. Si no, el servidor devuelve un código 401 Unauthorized Error. Cuando se añade la {{site.data.keyword.mobilepushshort}} a una aplicación, se creará una AppID específica. Como parte de la respuesta, obtiene una cabecera denominada appSecret que se utiliza para crear etiquetas o para enviar mensajes. La operación sucede a través de servicios del catálogo o del contenedor modelo.

Para obtener el valor de appSecret:

1. Pulse el *app-name* que está enlazado al servicio push.
2. Pulse el enlace **Mostrar credenciales** para visualizar el appSecret (AppID).

La pantalla **Mostrar credenciales** muestra información sobre el AppSecret:
```
	{
    "imfpush_Dev": [
   {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://imfpush.ng.bluemix.net/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.ng.bluemix.net/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**Nota**: Las aplicaciones anteriores requerían que se pasara clientSecret solo al registrar o actualizar dispositivos con el campo userID. Todas las otras API invocadas con clientes móviles y de navegador no necesitaban clientSecret. Estas aplicaciones antiguas pueden seguir utilizando el clientSecret de forma opcional para los registros de dispositivos o las llamadas de actualización. Sin embargo, se recomienda encarecidamente realizar la comprobación de clientSecret en todas las llamadas de API de cliente. Para imponer esto en las aplicaciones existentes, se ha publicado una nueva API `verifyClientSecret`.  En las aplicaciones nuevas, la comprobación de clientSecret se efectuará en todas las llamadas de API de cliente. Este comportamiento no puede modificarse con la API `verifyClientSecret`.

De forma predeterminada, la verificación del secreto de cliente se impone sólo en las nuevas apps. Está permitido que tanto las apps existentes como las nuevas habiliten o inhabiliten la verificación del secreto de cliente mediante la API REST verifyClientSecret. Se recomienda que imponga la verificación del secreto de cliente para evitar exponer los dispositivos a los usuarios que puedan conocer el applicationId y el deviceId.

Asegúrese de que el `clientSecret` no se muestre nunca ni lo codifique en la app móvil. Hay varios patrones de inicialización de aplicaciones que se pueden utilizar para obtener dinámicamente el `clientSecret` durante el tiempo de ejecución de la aplicación. El diagrama de secuencia sigue el posible patrón.
![Enable_Push](images/init_client_secret.jpg) 



