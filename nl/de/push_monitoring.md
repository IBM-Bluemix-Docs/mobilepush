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

# Benachrichtigungen überwachen 
{: #push_monitoring}

Der IBM {{site.data.keyword.mobilepushshort}}-Service verfügt nun über erweiterte Funktionen zum Überwachen des Durchsatzes von Push-Operationen, indem aus Ihren Benutzerdaten Diagramme generiert werden. Sie können das Dienstprogramm zum Auflisten aller gesendeten Push-Benachrichtigungen oder aller registrierten Geräte sowie für die tägliche, wöchentliche oder monatliche Analyse der Informationen verwenden.

Verwenden Sie zum Generieren von Berichten für alle Ihre gesendeten Benachrichtigungen die in [REST-APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window} beschriebene Berichtsmethode 'GET report' für Push-Nachrichten. 
	![Bericht zu gesendeten Benachrichtigungen - Balkendiagramm](images/monitoring_messages1.png "Balkendiagramm zu gesendeten Benachrichtigungen auf der Basis von monatlichen Daten")
<br>&nbsp;</br>
	![Bericht zu gesendeten Benachrichtigungen - Kreisdiagramm](images/monitoring_messages2.png "Kreisdiagramm zu gesendeten Benachrichtigungen auf der Basis der Plattform")
Verwenden Sie zum Generieren von Berichten für alle Ihre registrierten Geräte die in [REST-APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window} beschriebene Berichtsmethode 'GET report' für Push-Geräteregistrierungen.
	![Bericht zu registrierten Geräten - Liniendiagramm](images/monitoring_devices1.png "Liniendiagramm zu registrierten Geräten")
<br>&nbsp;</br>
	![Bericht zu registrierten Geräten - Kreisdiagramm](images/monitoring_devices2.png "Kreisdiagramm zu registrierten Geräten auf der Basis der Plattform")


Weiter Informationen zum Aktivieren des Überwachungsdienstprogramms für die jeweilige Plattform finden Sie hier:

 - [Push-Benachrichtigungen auf Android-Geräten überwachen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Push-Benachrichtigungen in iOS-Anwendungen überwachen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

Hinweis:

1. Auf der Registerkarte zur {{site.data.keyword.mobilepushshort}}-Überwachung werden keine Analysedaten angezeigt.
2. Der mithilfe der REST-APIs generierte Bericht wird im Cache zwischengespeichert, der Cache wird für einen Zeitraum von 30 Minuten beibehalten.
Darüber hinaus werden die in der Grafik dargestellten Daten auf der Basis der im Cache gespeicherten Daten generiert.
 
