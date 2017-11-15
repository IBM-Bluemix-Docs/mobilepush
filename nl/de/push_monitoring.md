---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Benachrichtigungen überwachen 
{: #push_monitoring}
Letzte Aktualisierung: 22. Juni 2017
{: .last-updated}


Der IBM {{site.data.keyword.mobilepushshort}}-Service verfügt nun über erweiterte Funktionen zum Überwachen des Durchsatzes von Push-Operationen, indem aus Ihren Benutzerdaten Diagramme generiert werden. Sie können das Dienstprogramm zum Auflisten aller gesendeten Push-Benachrichtigungen oder aller registrierten Geräte sowie für die tägliche, wöchentliche oder monatliche Analyse der Informationen verwenden.

Verwenden Sie zum Generieren von Berichten für alle Ihre gesendeten Benachrichtigungen die in [REST-APIs](https://mobile.{DomainName}/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window} beschriebene Berichtsmethode 'GET report' für Push-Nachrichten. 
	![Bericht zu gesendeten Benachrichtigungen](images/monitoring_messages.jpg)


Verwenden Sie zum Generieren von Berichten für alle Ihre registrierten Geräte die in [REST-APIs](https://mobile.{DomainName}/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window} beschriebene Berichtsmethode 'GET report' für Push-Geräteregistrierungen.
	![Bericht zu registrierten Geräten](images/monitoring_devices.jpg)

Beachten Sie, dass auf der Registerkarte zur {{site.data.keyword.mobilepushshort}}-Überwachung keine Analysedaten angezeigt werden.

Weiter Informationen zum Aktivieren des Überwachungsdienstprogramms für die jeweilige Plattform finden Sie hier:

 - [Push-Benachrichtigungen auf Android-Geräten überwachen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Push-Benachrichtigungen in iOS-Anwendungen überwachen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
 



 
