---

copyright:
  years:  2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, service access, manage, user roles

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Gestión de acceso de servicio
{: #service-access-management}

Con Identity and Access Management (IAM) de {{site.data.keyword.mobilepushshort}} e {{site.data.keyword.Bluemix_notm}}, los propietarios de cuenta pueden gestionar el acceso de usuario en la cuenta.
{: shortdesc}

Como propietario de una cuenta, puede establecer políticas dentro de la cuenta para crear distintos niveles de acceso para distintos usuarios. Por ejemplo, algunos usuarios pueden tener acceso de **Solo lectura** a una instancia, pero acceso de **Escritura** a otra. Puede decidir quién tiene permiso para crear, actualizar y suprimir instancias de {{site.data.keyword.mobilepushshort}}.

**Nota:** debido a que el servicio {{site.data.keyword.mobilepushshort}} ha adoptado IAM, no se generará el secreto de app para las nuevas instancias. Debe utilizar las [claves de API en su lugar](https://cloud.ibm.com/docs/iam?topic=iam-manapikey).

## Roles de usuario
{: #roles}

El ámbito de una política de acceso se basa en el rol asignado a un usuario.
{: shortdesc}

Las políticas permiten que se otorgue acceso en distintos niveles. Algunas de las opciones incluyen:
<ul><ul>
  <li>Acceso en todas las instancias del servicio en su cuenta</li>
  <li>Acceso a instancias de un servicio individual de su cuenta</li>
  <li>Acceso a un recurso específico dentro de una instancia</li>
  <li>Acceso a todos los servicios habilitados para IAM de su cuenta</li>
</ul></ul>

Los roles de gestión de plataformas permiten a los usuarios realizar tareas en los recursos de servicio a nivel de plataforma. Por ejemplo, los roles pueden asignarse para determinar quién puede crear o suprimir ID, crear instancias y enlazar instancias a apps. La tabla siguiente detalla las acciones a medida que se correlacionan con los roles de gestión de plataformas.

<table>
  <tr>
    <th>Rol de plataforma</th>
    <th>Permisos</th>
    <th>Acciones de ejemplo</th>
  </tr>
  <tr>
    <td><i>Visor</i></td>
    <td>Ver instancias de {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puede ver los datos de usuario de un Directorio de nube o la configuración de proveedor de identidad.</td>
  </tr>
  <tr>
    <td><i>Editor</i></td>
    <td>Ver y enlazar instancias de {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puede enlazar aplicaciones a una instancia de {{site.data.keyword.mobilepushshort}}.</td>
  </tr>
  <tr>
    <td><i>Operador</i></td>
    <td>Crear, suprimir, editar, suspender, reanudar, ver o enlazar instancias de {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puede crear o suprimir una instancia de {{site.data.keyword.mobilepushshort}} desde el catálogo.</td>
  </tr>
  <tr>
    <td><i>Administrador</i></td>
    <td>Todas las acciones de gestión para todos los servicios de la cuenta.</td>
    <td>Puede realizar todas las acciones del operador y la capacidad de asignar políticas a otros usuarios.</td>
  </tr>
</table>

</br>
</br>
En la tabla siguiente se detallan las acciones correlacionadas con los roles de acceso al servicio. Los roles de acceso al servicio permiten a los usuarios acceder a {{site.data.keyword.mobilepushshort}}, así como la posibilidad de llamar a la API de {{site.data.keyword.mobilepushshort}}.


<table>
  <tr>
    <th>Rol de servicio</th>
    <th>Permisos</th>
    <th>Acciones de ejemplo</th>
  </tr>
  <tr>
    <td><i>Lector</i></td>
    <td>Ver datos de instancia de {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puede ver los detalles de la instancia de servicio como los datos de usuario o la información del proveedor de identidad.</td>
  </tr>
  <tr>
    <td> <i>Escritor o Gestor</i></td>
    <td>Ver y cambiar una instancia de {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puede realizar todas las acciones del Lector y editar la instancia de servicio, como por ejemplo editar la configuración del proveedor de identidad. </li></ul></td>
  </tr>
</table>

Para obtener más información sobre la asignación de roles de usuario en la IU, consulte [Gestión del acceso de IAM](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser).


## Políticas de acceso de {{site.data.keyword.mobilepushshort}}
{: #access}

Todos los usuarios que accedan al servicio {{site.data.keyword.mobilepushshort}} en su cuenta deben tener asignada una política de acceso con un rol de usuario de IAM definido. Esta política determina qué acciones puede realizar el usuario dentro del contexto del servicio o instancia que seleccione.
{: shortdesc}

Las acciones son personalizadas y están definidas por el servicio de {{site.data.keyword.Bluemix_notm}} como operaciones permitidas para realizarse en el servicio. Las acciones se correlacionarán entonces con los roles de usuario de IAM. Con el servicio {{site.data.keyword.cloudaccesstrailshort}}, se puede realizar un seguimiento de algunas de las acciones que se realizan. En la tabla siguiente, se correlacionan las acciones y los permisos necesarios para {{site.data.keyword.mobilepushshort}}.

|Acción |Descripción |Rol necesario |
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |Obtener valores de la app |Gestor, escritor, lector|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |Suprimir los valores de la app |Gestor|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |Actualizar los valores de la app |Gestor|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |Obtener dispositivos |Gestor, escritor, lector|
|`POST /imfpush/v1/apps/{applicationId}/devices` |Registrar el dispositivo |Gestor, escritor|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Actualizar el dispositivo |Gestor, escritor|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Suprimir el dispositivo |Gestor|
|`POST /imfpush/v1/apps/{applicationId}/messages` |Enviar mensajes |Gestor, escritor|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |Enviar mensajes masivos |Gestor, escritor|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |Suprimir un mensaje |Gestor|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |Obtener mensajes |Gestor, lector, escritor|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |Actualizar el estado de entrega del mensaje|Gestor, escritor|
|`POST /imfpush/v1/apps/{applicationId}/tags` |Crear etiquetas |Gestor, escritor|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Actualizar etiqueta   |Gestor, escritor|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Suprimir etiqueta   |Gestor|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |Obtener etiquetas |Gestor, lector, escritor|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |Crear suscripciones |Gestor, escritor|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |Suprimir suscripciones |Gestor|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |Obtener suscripciones |Gestor, lector, escritor|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |Crear webhook |Gestor, escritor|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Actualizar webhook |Gestor, escritor|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Suprimir webhook |Gestor|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |Obtener webhook |Gestor, lector, escritor|-|

## Cómo trabajar con claves de API
{: #apikeys}

Tras crear las credenciales de servicio, es posible que note que aparece una clave de API en lugar del secreto de app.

Para utilizar las API REST, debe generar la señal de acceso utilizando el mandato curl siguiente:

### Parámetros

```
  curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### Respuesta

```
{
    "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```

Tras generar la señal de acceso utilizando el mandato curl anterior, ahora puede operar con las API REST pasando ‘Bearer <valor de la señal de acceso>’ en la cabecera Authorization

Por ejemplo:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \
   "message": { \
     "alert": "Notification alert message" \
   } \
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

Para obtener más información sobre IAM, consulte [Acceso de IAM](https://cloud.ibm.com/docs/iam?topic=iam-userroles).
