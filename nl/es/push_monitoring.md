---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificaciones de supervisión 
{: #push_monitoring}
Última actualización: 30 de octubre de 2017
{: .last-updated}


El servicio {{site.data.keyword.mobilepushshort}} de IBM ahora amplía sus funciones para supervisar el rendimiento push generando gráficos desde los datos de usuario. Puede utilizar el programa de utilidad para enumerar todas las notificaciones push enviadas, o para enumerar todos los dispositivos registrados y para analizar información de forma diaria, semanal o mensual.

Para generar informes para todas las notificaciones enviadas, utilice el método de informes Push Messages GET en [API REST](https://imfpush.{DomainName}/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Informe de notificaciones enviadas](images/monitoring_messages.jpg)


Para generar informes para todos los dispositivos registrados, utilice el método de informes Push Device Registrations GET en [API REST](https://imfpush.{DomainName}/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Informe de dispositivos registrados](images/monitoring_devices.jpg)


Para obtener información sobre cómo habilitar la supervisión de programas de utilidad para la plataforma:

 - [Supervisión de notificaciones push en dispositivos Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Supervisión de notificaciones push en aplicaciones de iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

Nota:

1. El separador de supervisión de {{site.data.keyword.mobilepushshort}} no muestra los datos analíticos.
2. El informe que se ha generado utilizando las API REST se almacenarán en la memoria caché y esta se mantendrá durante treinta minutos.
Asimismo, los datos que se representan en el gráfico se generarán a partir de los datos de la memoria caché.
 



 
