---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Sucesos de Activity Tracker
{: #push_activity_tracker}

El servicio {{site.data.keyword.cloudaccesstrailfull}} supervisa la interacción de un usuario con los servicios de IBM Cloud. Puede buscar y analizar cómo interactúan los usuarios y aplicaciones con los servicios de IBM Cloud.

Los administradores, la seguridad y los desarrolladores de la nube pueden:

<dl>
	<dt>Obtener información de su entorno para supervisar e investigar brechas de seguridad</dt>
	<dd>Capture las interacciones de los usuarios y de las aplicaciones con los recursos suministrados de IBM Cloud. Investigue los posibles accesos no autorizados y brechas de seguridad.</dd>
	<dt>Cumplir sus necesidades de retención de registros, conformidad y normativa</dt>
	<dd>Almacene los sucesos capturados el tiempo que desee, protegidos en soluciones de almacenamiento económicas de clase de nube. Consultar los datos de sucesos recopilados a través de la API o exporte los datos de actividad de la nube.</dd>
	<dt>Disponer de transparencia de la nube para que los equipos de DevOps puedan depurar y realizar planificaciones de la capacidad</dt>
	<dd>Los sucesos de actividad en la nube proporcionan transparencia de las operaciones de IT en IBM Cloud. Identifique cuándo y cómo se utilizan los servicios de la nube para aislar y depurar las aplicaciones. Consulte los datos recopilados en el tiempo para prever el crecimiento de la nube y las necesidades de cada temporada.</dd>
	<dt>Simplificar la recopilación y mejore la seguridad de la nube</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}} captura automáticamente los sucesos de IBM Cloud.</dd>
</dl>


Los registros de actividad de {{site.data.keyword.cloudaccesstrailshort}} se pueden utilizar para identificar la información siguiente:

- Los usuarios que han realizado llamadas de API a servicios en la nube.
- La dirección IP de origen desde la que se han realizado las llamadas de API.
- La indicación de fecha y hora de realización de las llamadas de API.
- El estado de la llamada de API.

## Lista de sucesos
{: #actions}

En la siguiente tabla se muestran los sucesos de {{site.data.keyword.cloudaccesstrailshort}} para {{site.data.keyword.mobilepushshort}}
<table>
  <caption>Tabla 1. Lista de acciones que generan un suceso</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>Actualizaciones de la aplicación</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>Supresión de la configuración de la aplicación</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>Actualización de la configuración de la aplicación</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>Creación de etiquetas</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>Supresión de etiquetas</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>Actualización de etiquetas</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Creación de webhook</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Supresión de webhook</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Actualización de webhook</td>
  </tr>   
</table>


Para obtener más información sobre cómo trabajar con {{site.data.keyword.cloudaccesstrailshort}}, consulte la
[documentación aquí](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}.


Actualmente, los sucesos de Activity Tracker solo están disponibles en `IBM Cloud - Región EE.UU. sur`.
{: note}
