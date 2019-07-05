---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-24"

keywords: push notifications, notifications, compliance, hipaa, iso, soc 2 type 1 certification, gdpr

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Conformidad
{: #compliance}

El servicio {{site.data.keyword.mobilepushshort}} de IBM Cloud proporciona una forma fiable y segura de enviar notificaciones a los dispositivos móviles registrados.
{: shortdesc}

## HIPAA
{: #hipaa}

El servicio {{site.data.keyword.mobilepushshort}} de IBM cumple los controles de IBM necesarios en consonancia con los requisitos de la normativa de privacidad y seguridad de Health Insurance Portability and Accountability Act of 1996 (HIPAA). El servicio {{site.data.keyword.mobilepushshort}} almacena los datos en un formato cifrado en reposo, y transmite los datos cifrados.

Si desea enviar información regulada por la HIPAA utilizando el servicio
{{site.data.keyword.mobilepushshort}} de IBM Cloud, no debe utilizar la API Post/message, ya que es posible que la carga útil enviada a través de proveedores de Push de terceros no cumpla las directrices de la normativa. En su lugar, puede utilizar los pasos siguientes, en los que solo se envía el ID de mensaje a través de proveedores de Push de terceros, pero los datos confidenciales reales los descarga la aplicación cliente a través de un transporte seguro (https).

1. Suministre una nueva instancia de plan avanzado o actualice su instancia existente a un plan avanzado.
2. Envíe una [notificación silenciosa](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios) utilizando el servicio {{site.data.keyword.mobilepushshort}}.
3. El servicio {{site.data.keyword.mobilepushshort}} envía la notificación utilizando proveedores de nube de envío por push como FCM o APNS. Debido a las características de la notificación silenciosa, no se envía una alerta como parte de la notificación.
4. Una vez que el dispositivo reciba la notificación con el ``message id`` / ``nid`` transmitido, la aplicación realizará una llamada al servicio
{{site.data.keyword.mobilepushshort}} para recibir la alerta de notificación utilizando ``GET /message/{messageId}``.

Esto ayuda a lograr la transmisión de contenido de texto confidencial a través de un canal seguro utilizando el servicio
{{site.data.keyword.mobilepushshort}} de IBM Cloud.

IBM no tiene una relación de acuerdo de socio empresarial (BAA) con APNS/FCM.
{: note}
## International Organization for Standardization (ISO)
{: #iso}

El servicio {{site.data.keyword.mobilepushshort}} es auditado por una compañía de seguridad de terceros y cumple los requisitos de ISO siguientes:

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [Buscar todos los certificados ISO de IBM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}.
 
## Certificación SOC 2 Tipo 1
{: #soccert}

{{site.data.keyword.IBM_notm}} proporciona un informe de Controles de organización de servicios (SOC) 2 Tipo 1 para el servicio {{site.data.keyword.mobilepushshort}}. Los informes evalúan los controles operativos de IBM de acuerdo con los criterios establecidos por los llamados Trust Services Principles del American Institute of Certified Public Accountants (AICPA). 
Los Trust Services Principles definen unos sistemas de control adecuados y establecen estándares del sector para que los proveedores de servicios como IBM custodien los datos y la información de sus clientes.

Puede solicitar un informe SOC 2 Tipo 1 desde el portal de clientes o ponerse en contacto con el representante de ventas. Como alternativa, puede abrir una incidencia de soporte con el
[soporte de IBM Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/support){: new_window}.

## Reglamento General de Protección de Datos (GDPR) 
{: #gdpr}

El GDPR busca crear una infraestructura legislativa de protección de datos armonizada en la UE, y tiene como objetivo otorgar de nuevo a los ciudadanos el control de sus datos personales, al tiempo que impone reglas estrictas sobre aquellos que alojan y 'procesan' estos datos, en cualquier parte del mundo. La normativa también presenta reglas referentes a la libre circulación de datos personales dentro y fuera de la Unión Europea. 

Con el [Reglamento general de protección de datos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.eugdpr.org/){: new_window}, los clientes del servicio {{site.data.keyword.mobilepushshort}} pueden confiar en que el equipo del servicio
{{site.data.keyword.mobilepushshort}} conoce y cumple la normativa y los estándares emergentes de privacidad de datos, así como en la capacidad de {{site.data.keyword.IBM}} para proporcionar un conjunto exhaustivo de soluciones para ayudar a los negocios de todos los tamaños con sus propios requisitos de control de datos internos.
