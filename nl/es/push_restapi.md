---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# API REST de notificaciones push
{: #push-api-rest}
Última actualización: 22 de mayo de 2017
{: .last-updated}

Puede utilizar una API (application program interface, interfaz de programa de aplicaciones) REST (Representational State Transfer) para {{site.data.keyword.mobilepushshort}}. También puede utilizar el SDK y la [API Push ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](https://imfpush.{DomainName}/imfpush/){: new_window} para seguir desarrollando aplicaciones cliente.

Con la API REST Push, los clientes y las aplicaciones de servidor de fondo pueden acceder a las funciones {{site.data.keyword.mobilepushshort}}.

- Registros de dispositivos
- Registros
- Mensajes
- Suscripciones
- Etiquetas
- Webhooks

Para obtener el URL base de la API REST, siga estos pasos:

1. Cree una aplicación back-end en el catálogo IBM Cloud® de la sección de contenedores modelo eligiendo MobileFirst Services Starter. De esta manera se enlaza el servicio {{site.data.keyword.mobilepushshort}} con la aplicación. También puede crear una instancia de servicio de push y dejarla desenlazada. 
1. En la página principal del catálogo de IBM Cloud, vaya al área **Aplicaciones** y seleccione la app.
3. Pulse **OPCIONES MÓVILES**. Se mostrarán la ruta y los valores GUID de la app al principio de la página de detalles de su app. La pantalla Mostrar credenciales muestra información sobre el AppSecret. Puede obtener el secreto de la aplicación en Opciones móviles, así como el secreto de cliente de algunas de las API.

También puede utilizar la línea de mandatos para obtener las credenciales del servicio:

```
    cf create-service-key {nombre_instancia_push} {nombre_clave}

 cf service-key {nombre_instancia_push} {nombre_clave}
```
	{: codeblock}

## Cabecera Accept Language
{: #push-api-rest-accept}

La cabecera "Accept-Language" especifica el idioma que se utilizará para los mensajes de error que emite la [API REST de Push ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](https://imfpush.{DomainName}/imfpush/){: new_window}. Se da soporte a los siguientes idiomas para ver si contienen mensajes de error: chino (simplificado), chino (tradicional), inglés (EE.UU.), alemán, francés, italiano, japonés, coreano, portugués y español.


## Filtros API REST de Push
{: #push-api-rest-filters}

Los filtros definen los criterios de búsqueda que restringen los datos devueltos de una API GET de {{site.data.keyword.mobilepushshort}}. Aplique los filtros con el resultado de la operación Get que desee filtrar. El filtro restringe el número de entradas incluidas en el resultado. Por ejemplo, puede utilizar un filtro para buscar etiquetas que empiecen por "test". 

Los filtros se pueden generar mediante la siguiente sintaxis:

**name**: el nombre de campo en el que se está aplicando el filtro.

**operator**: == (Coincidencia exacta) o =@ (Contiene subserie) que describe la coincidencia de filtro que se debe utilizar.

**expression**: los valores que se deben incluir en el resultado.

Cuando se visualizan en una expresión una coma y una barra inclinada invertida, se deben poder escapar con la barra inclinada invertida.

Al utilizar varios filtros, se pueden combinar mediante la lógica AND y OR.

- Para la lógica AND, utilice varios filtros en la consulta.
- Para la lógica OR, utilice una coma (,) dentro de la expresión de filtro.
- Para la lógica AND y OR: una única consulta puede tener la lógica AND y OR. Cada filtro se evalúa de forma individual antes de que los filtros se combinen en una expresión AND.

Para la API GET del dispositivo, se da soporte a las siguientes combinaciones:
-El nombre es el campo plataforma.
- Excepto para la plataforma, el operador puede ser == o =@
- Para la plataforma, el operador debe ser ==. Si se utiliza el operador =@, el valor puede ser una subcadena.
- Si se utiliza ==, el valor debe ser una cadena de caracteres de coincidencia exacta.

Para la API GET de suscripción, se da soporte a las siguientes combinaciones:

- El nombre puede ser uno de estos campos: tagName o deviceId
- Excepto para la plataforma, el operador puede ser == o =@
- Para la plataforma, el operador debe ser ==
- Si se utiliza el operador =@, el valor puede ser una subcadena. Si se utiliza el operador ==, el valor debe ser una cadena de caracteres de coincidencia exacta.
- Para la API GET de la etiqueta, se da soporte a las siguientes combinaciones:
- El nombre puede ser uno de estos campos: “name” o “description”
- Si se utiliza el operador =@, el valor puede ser una subcadena.
- Si se utiliza ==, el valor debe ser una cadena de caracteres de coincidencia exacta.


## Códigos de respuesta del servicio de notificaciones push
{: #push-api-response-codes}

Estado: Método 405 no permitido - Se esperaba el método apropiado.
