---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Surveillance des notifications 
{: #push_monitoring}
Dernière mise à jour : 22 juin 2017
{: .last-updated}


Le service IBM {{site.data.keyword.mobilepushshort}} étend désormais les capacités de surveillance des performances push en générant des graphiques depuis vos données utilisateur. Vous
pouvez utiliser l'utilitaire pour répertorier toutes les notifications push envoyées ou pour répertorier tous les appareils enregistrés et analyser les informations sur une base quotidienne, hebdomadaire ou mensuelle.

Pour générer des rapports pour toutes les notifications envoyés, utilisez la méthode du rapport Push Messages GET report dans les [API REST](https://mobile.{DomainName}/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Rapport Notifications envoyées](images/monitoring_messages.jpg)


Pour générer des rapports pour tous les appareils enregistrés, utilisez la méthode du rapport Push Device Registrations GET dans les
[API REST](https://mobile.{DomainName}/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Rapport Appareils enregistrés](images/monitoring_devices.jpg)

Notez que l'onglet de surveillance {{site.data.keyword.mobilepushshort}} n'affiche pas de données d'analyse.

Pour plus d'informations sur l'activation de l'utilitaire de surveillance pour votre plateforme, voir :

 - [Monitoring push notifications on Android devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Monitoring push notifications on iOS applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
 



 
