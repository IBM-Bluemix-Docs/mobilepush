---

copyright:
  years: 2016, 2021
lastupdated: "2021-02-03"

keywords: push notifications, push notification, activity tracker for Push Notifications service, LogDNA for Push Notifications service, Push Notifications service events, Push Notifications service security, audit logs for Push Notifications service, viewing Push Notifications service events, Push Notifications service events

subcollection: mobilepush

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:java: .ph data-hd-programlang='java'}
{:ruby: .ph data-hd-programlang='ruby'}
{:c#: .ph data-hd-programlang='c#'}
{:objectc: .ph data-hd-programlang='Objective C'}
{:python: .ph data-hd-programlang='python'}
{:javascript: .ph data-hd-programlang='javascript'}
{:php: .ph data-hd-programlang='PHP'}
{:swift: .ph data-hd-programlang='swift'}
{:reactnative: .ph data-hd-programlang='React Native'}
{:csharp: .ph data-hd-programlang='csharp'}
{:ios: .ph data-hd-programlang='iOS'}
{:android: .ph data-hd-programlang='Android'}
{:cordova: .ph data-hd-programlang='Cordova'}
{:xml: .ph data-hd-programlang='xml'}

# Auditing events for {{site.data.keyword.mobilepushshort}} service
{: #at_events}

As a security officer, auditor, or manager, use the Activity Tracker service to track how users and applications interact with the {{site.data.keyword.mobilepushshort}} service in {{site.data.keyword.cloud}}. You can manage, view, and audit actions or events such as device registration, device subscription, and application configuration can be tracked for {{site.data.keyword.mobilepushshort}} service. 
{: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.at_full_notm}}](https://cloud.ibm.com/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started).

## Prerequisite
{: at-prerequisite}

You need to have an instance of {{site.data.keyword.at_full_notm}} in the region where you would like to track events.

To view and search for the event logs, use any one of the {{site.data.keyword.at_full_notm}} plans (7 or 14 or 30 days) based on your log search need. Using {{site.data.keyword.at_full_notm}} lite plan is not recommended for event logging.
{: important}

## List of events by {{site.data.keyword.mobilepushshort}} service
{: #at_actions}

The following table lists the {{site.data.keyword.cloudaccesstrailfull}} events for {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service:

|Action                                |Description                                                                       |
|--------------------------------------|----------------------------------------------------------------------------------|
|imfpush.app.credentials.decrypt.error |Event sent if error occurs on decryption of credentials via Key Protect           |
|imfpush.app.credentials.encrypt.error |Event sent if error occurs while encryption of credentials via key protect        |
|imfpush.app.credentials.ready-to-use	 |Event sent before sending credentials for encryption or decryption to Key Protect |
|imfpush.app.forbidden		             |Event sent for non privileged access of API's                                     |
|imfpush.app.provisioned               |App provisioned                                                                   |
|imfpush.app.resource-not-found	       |Event sent if resource to be updated or deleted, not there in the service         |
|imfpush.app.unauthorized		           |Event sent for not authorised access                                              |
|imfpush.app.unprovisioned             |App unprovisioned                                                                 |
|imfpush.app.update                    |Updates to the Application                                                        |
|imfpush.app-channel.read              |App channel information read                                                      |
|imfpush.app-channels.read             |App channels information read                                                     |
|imfpush.app-channel-group.read        |App channel group read                                                            |
|imfpush.app-conf.delete               |Application configuration deletion                                                |
|imfpush.app-conf.read                 |Application configuration read                                                    |	
|imfpush.app-conf.update               |Application configuration update                                                  |
|imfpush.app-device.create             |Device registration                                                               |
|imfpush.app-device.delete             |Device unregistration                                                             |
|imfpush.app-device.read               |Device information read                                                           |
|imfpush.app-device.report.read        |Devices report                                                                    |
|imfpush.app-devices.read              |Devices information read                                                          |
|imfpush.app-message.create            |Send message                                                                      |
|imfpush.app-message.latest.read       |Latest Messages information by timestamp                                          |
|imfpush.app-message.read              |Message information read                                                          |
|imfpush.app-messages.read             |Messages information read                                                         |
|imfpush.app-subscription.create       |Device subscription for a tag                                                     |
|imfpush.app-subscription.delete       |Device unsubscription for a tag                                                   |
|imfpush.app-subscription.read         |Subscription information read                                                     |
|imfpush.app-tag.create                |Tag creation                                                                      |
|imfpush.app-tag.delete                |Tag deletion                                                                      |
|imfpush.app-tag.read                  |Tag information read                                                              |
|imfpush.app-tag.update                |Tag update                                                                        |
|imfpush.app-tags.read                 |Tags information read                                                             |
|imfpush.app-webhook.create            |Webhook creation                                                                  |
|imfpush.app-webhook.delete            |Webhook deletion                                                                  |
|imfpush.app-webhook.update            |Webhook update                                                                    |
|imfpush.app-webhook.read              |Webhook information read                                                          |
|imfpush.app-webhooks.read             |Webhook informations read                                                         |
{: caption="Table 1. List of actions that genererate an event" caption-side="top"}

Currently, the {{site.data.keyword.cloudaccesstrailshort}} Events for {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service are available only on `Dallas, Washington DC, London, Sydney, and Tokyo`.
{: note}

## Viewing events
{: #at_ui}

Events that are generated by an instance of the {{site.data.keyword.mobilepushshort}} service are automatically forwarded to the {{site.data.keyword.at_full_notm}} service instance that is available in the same location.

{{site.data.keyword.mobilepushshort}} service manages Activity Tracker by using the same common Dallas instance for Washington DC and Dallas and use tags that let events filter based on region.
{: note}

{{site.data.keyword.at_full_notm}} can have only one instance per location. To view events, you must access the web UI of the {{site.data.keyword.at_full_notm}} service in the same location where your service instance is available. For more information, see [Launching the web UI through the IBM Cloud UI](https://cloud.ibm.com/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_cloud_ui).

## Analyzing events
{: #at_events_iam_analyze}

{{site.data.keyword.at_full_notm}} compiles all of your logs at an account level, which means that all of your services are shown in the same instance, per region. If you have an app that runs in Dallas and another app that runs in London, the events are found in the respective instances of Activity Tracker.

1. Log in to your IBM Cloud account.
1. In the IBM Cloud console navigation, click **Observability**.
1. Select **Activity Tracker** from the **Observability** navigation.
1. Select the instance of Activity Tracker that correlates to the region for which you want to see events.
1. Click **View LogDNA**. When the dashboard loads, you see an overview of all of the activity that is covered by that instance of Activity Tracker with LogDNA. You can use the search operators to filter the events by tags, sources, apps, or levels. You can also search for specific events or jump to a specific timeframe.
1. To see events for a specific application, select the app that you want to track from the **All Apps** drop-down. To help meet compliance regulations, you can choose to retain your events or archive them into [IBM Cloud Object Storage](https://www.ibm.com/cloud/object-storage).

   ![Push Log DNA](images/mp-logDNA.png "View of your Activity Tracker instance with a sample audit event")

   Figure 1: View of your Activity Tracker instance with a sample audit event.
