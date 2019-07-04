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

# Surveillance des notifications 
{: #push_monitoring}

Le service IBM {{site.data.keyword.mobilepushshort}} étend désormais les capacités de surveillance des performances push en générant des graphiques depuis vos données utilisateur. Vous
pouvez utiliser l'utilitaire pour répertorier toutes les notifications push envoyées ou pour répertorier tous les appareils enregistrés et analyser les informations sur une base quotidienne, hebdomadaire ou mensuelle.

Pour générer des rapports pour toutes les notifications envoyés, utilisez la méthode du rapport Push Messages GET report dans les [API REST](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Rapport sur les notifications envoyées - diagramme à barres](images/monitoring_messages1.png "Diagramme à barres des notifications envoyées basé sur des données mensuelles")
<br>&nbsp;</br>
	![Rapport sur les notifications envoyées - diagramme sectoriel](images/monitoring_messages2.png "Diagramme sectoriel des notifications envoyées basé sur la plateforme")

Pour générer des rapports pour tous les appareils enregistrés, utilisez la méthode du rapport Push Device Registrations GET dans les
[API REST](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Rapport sur les appareils enregistrés - diagramme linéaire](images/monitoring_devices1.png "Diagramme linéaire des appareils enregistrés")
<br>&nbsp;</br>
	![Rapport sur les appareils enregistrés - graphique circulaire](images/monitoring_devices2.png "Graphiques circulaires des appareils enregistrés basés sur la plateforme")


Pour plus d'informations sur l'activation de l'utilitaire de surveillance pour votre plateforme, voir :

 - [Monitoring push notifications on Android devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Monitoring push notifications on iOS applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

Remarque :

1. L'onglet Surveillance de {{site.data.keyword.mobilepushshort}} n'affiche pas les données d'analyse.
2. Le rapport généré à l'aide des API REST sera mis en cache et le cache sera conservé pendant trente minutes.
De même, les données représentées dans le graphique seront générées à partir des données mises en cache.
 
