---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, monitoring notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificações do Monitor 
{: #push_monitoring}

Agora, o serviço IBM {{site.data.keyword.mobilepushshort}} estende os recursos para monitorar o
desempenho de push gerando gráficos de seus dados do usuário. É possível usar o utilitário para listar todas as notificações push enviadas ou para listar todos os
dispositivos registrados e analisar informações em uma base diária, semanal ou mensal.

Para gerar relatórios para todas as notificações enviadas, utilize o método de relatório GET de Mensagem push nas [APIs de REST](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Relatório de notificações enviado - gráfico de barras](images/monitoring_messages1.png "Gráfico de barras de notificações enviado com base em dados mensais")
<br>&nbsp;</br>
	![Relatório de notificações enviado - diagrama de setor](images/monitoring_messages2.png "Diagrama de setor de notificações enviado com base na plataforma")

Para gerar relatórios para todos os dispositivos registrados, utilize o método de relatório GET de Registros de dispositivo push nas [APIs de REST](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Relatório de dispositivos registrados - gráfico de linhas](images/monitoring_devices1.png "Gráfico de linhas de dispositivos registrados")
<br>&nbsp;</br>
	![Relatório de dispositivos registrados - gráfico de pizza](images/monitoring_devices2.png "Gráfico de pizza de dispositivos registrados com base na plataforma")


Para obter informações sobre como ativar o utilitário de monitoramento de sua plataforma:

 - [Monitorando notificações push em dispositivos Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Monitorando notificações push em aplicativos iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

Nota:

1. A guia de monitoramento do {{site.data.keyword.mobilepushshort}} não mostra dados de analítica.
2. O relatório gerado usando as APIs de REST será armazenado em cache e o cache será mantido por trinta minutos.
Além disso, os dados representados no gráfico serão gerados usando os dados em cache.
 
