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

# Monitora le notifiche 
{: #push_monitoring}

Il servizio IBM {{site.data.keyword.mobilepushshort}} ora estende le funzionalità di monitoraggio delle prestazioni di push generando dei grafici dai tuoi dati utente. Puoi utilizzare il programma di utilità per elencare tutte le notifiche di push inviate o tutti i dispositivi registrati e per analizzare le informazioni su base giornaliera, settimanale o mensile.

Per generare dei report per tutte le tue notifiche inviate, utilizza il metodo GET report Push Messages nelle [API REST](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Report notifiche inviate - Grafico a barre](images/monitoring_messages1.png "Grafico a barre delle notifiche inviate basato sui dati mensili")
<br>&nbsp;</br>
	![Report notifiche inviate - Diagramma a settori](images/monitoring_messages2.png "Diagramma a settori delle notifiche inviate basato sulla piattaforma")

Per generare dei report per tutti i tuoi dispositivi registrati, utilizza il metodo GET report Push Device Registrations nelle [API REST](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Report dispositivi registrati - Grafico a linee](images/monitoring_devices1.png "Grafico a linee dei dispositivi registrati")
<br>&nbsp;</br>
	![Report dispositivi registrati - Grafico a torta](images/monitoring_devices2.png "Grafici a torta dei dispositivi registrati basati sulla piattaforma")


Per informazioni su come abilitare il programma di utilità di monitoraggio per la tua piattaforma:

 - [Monitoraggio di notifiche di push su dispositivi Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Monitoraggio di notifiche di push sulle applicazioni iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

Nota:

1. La scheda del monitoraggio {{site.data.keyword.mobilepushshort}} non visualizza i dati di analisi.
2. Il report generato utilizzando le API REST sarà memorizzato nella cache e la cache viene conservata per trenta minuti.
Inoltre, i dati rappresentati nel grafico saranno generati dai dati memorizzati nella cache.
 
