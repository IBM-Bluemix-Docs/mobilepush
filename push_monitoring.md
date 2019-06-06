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

# Monitor notifications 
{: #push_monitoring}

The IBM {{site.data.keyword.mobilepushshort}} service now extends capabilities to monitor the push performance by generating graphs from your user data. You can use the utility to list all the sent push notifications, or to list all the registered devices and to analyze information on a daily, weekly, or monthly basis.

To generate reports for all your the sent notifications, use the Push Messages GET report method in [REST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window}. 
	![Sent notifications report - bar graph](images/monitoring_messages1.png "Sent notifications bar graph based on monthly data")
<br>&nbsp;</br>
	![Sent notifications report - sector diagram](images/monitoring_messages2.png "Sent notifications sector diagram based on platform")

To generate reports for all your registered devices, use the Push Device Registrations GET report method in [REST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window}.
	![Registered devices report - line graph](images/monitoring_devices1.png "Registered devices line graph")
<br>&nbsp;</br>
	![Registered devices report - pie graph](images/monitoring_devices2.png "Registered devices pie charts based on platform")


For information on how to enable monitoring utility for your platform:

 - [Monitoring push notifications on Android devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [Monitoring push notifications on iOS applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

Note:

1. The {{site.data.keyword.mobilepushshort}} monitoring tab does not show analytics data.
2. The report that is generated using the REST APIs will be cached and the cache is maintained for thirty minutes.
Also, the data represented in the graph will be generated from the cached data.
 
