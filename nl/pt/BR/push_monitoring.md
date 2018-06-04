---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificações do Monitor 
{: #push_monitoring}
Última atualização: 30 de outubro de 2017
{: .last-updated}


Agora, o serviço IBM {{site.data.keyword.mobilepushshort}} estende os recursos para monitorar o
desempenho de push gerando gráficos de seus dados do usuário. É possível usar o utilitário para listar todas as notificações push enviadas ou para listar todos os
dispositivos registrados e analisar informações em uma base diária, semanal ou mensal.

Para gerar relatórios para todas as notificações enviadas, utilize o método de relatório GET de Mensagem push nas [APIs de REST](https://imfpush.{DomainName}/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Relatório Enviar notificações](images/monitoring_messages.jpg)


Para gerar relatórios para todos os dispositivos registrados, utilize o método de relatório GET de Registros de dispositivo push nas [APIs de REST](https://imfpush.{DomainName}/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Relatório Dispositivos registrados](images/monitoring_devices.jpg)


Para obter informações sobre como ativar o utilitário de monitoramento de sua plataforma:

 - [Monitorando notificações push em dispositivos Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Monitorando notificações push em aplicativos iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

Nota:

1. A guia de monitoramento do {{site.data.keyword.mobilepushshort}} não mostra dados de analítica.
2. O relatório gerado usando as APIs de REST será armazenado em cache e o cache será mantido por trinta minutos.
Além disso, os dados representados no gráfico serão gerados usando os dados em cache.
 



 
