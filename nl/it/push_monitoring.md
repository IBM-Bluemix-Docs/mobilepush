---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Monitora le notifiche 
{: #push_monitoring}
Ultimo aggiornamento: 22 giugno 2017
{: .last-updated}


Il servizio IBM {{site.data.keyword.mobilepushshort}} ora estende le funzionalità di monitoraggio delle prestazioni di push generando dei grafici dai tuoi dati utente. Puoi utilizzare il programma di utilità per elencare tutte le notifiche di push inviate o tutti i dispositivi registrati e per analizzare le informazioni su base giornaliera, settimanale o mensile.

Per generare dei report per tutte le tue notifiche inviate, utilizza il metodo GET report Push Messages nelle [API REST](https://mobile.{DomainName}/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Report notifiche inviate](images/monitoring_messages.jpg)


Per generare dei report per tutti i tuoi dispositivi registrati, utilizza il metodo GET report Push Device Registrations nelle [API REST](https://mobile.{DomainName}/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Report dispositivi registrati](images/monitoring_devices.jpg)

Tieni presente che la scheda di monitoraggio di {{site.data.keyword.mobilepushshort}} non visualizza dati di analisi.

Per informazioni su come abilitare il programma di utilità di monitoraggio per la tua piattaforma:

 - [Monitoraggio di notifiche di push su dispositivi Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Monitoraggio di notifiche di push sulle applicazioni iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
 



 
