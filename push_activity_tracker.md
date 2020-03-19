---

copyright:
  years: 2015, 2020
lastupdated: "2020-03-19"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

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

# Activity Tracker Events
{: #push_activity_tracker}

The {{site.data.keyword.cloudaccesstrailfull}} service monitors a user's interaction with the {{site.data.keyword.cloud_notm}} services. You can search and analyze how your users and applications interact with {{site.data.keyword.cloud_notm}} services.

Refer to the [Activity Tracker Page](https://cloud.ibm.com/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started){: external} for details.

## List of events by {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service
{: #actions}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service is now able to send events to {{site.data.keyword.cloudaccesstrailfull}}
 service. You can choose to track activity on the {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service by creating an instance of [{{site.data.keyword.cloudaccesstrailfull}} service](https://cloud.ibm.com/observe/activitytracker/create).

The following table lists the {{site.data.keyword.cloudaccesstrailfull}} events for {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service:

|Action                             |Description                        |
|-----------------------------------|-----------------------------------|
|imfpush.app.update                 |Updates to the Application         |
|imfpush.app-conf.delete            |Application configuration deletion |
|imfpush.app-conf.update            |Application configuration update   |
|imfpush.app-device.create          |Device registration                |
|imfpush.app-device.delete          |Device unregistration             |
|imfpush.app-tag.create             |Tag creation                       |
|imfpush.app-tag.delete             |Tag deletion                       |
|imfpush.app-tag.update             |Tag update                         |
|imfpush.app-subscription.create    |Device subscription for a tag      |
|imfpush.app-subscription.delete    |Device unsubscription for a tag   |
|imfpush.app-message.create         |Send message                       |
|imfpush.app-webhook.create         |Webhook creation                   |
|imfpush.app-webhook.delete         |Webhook deletion                   |
|imfpush.app-webhook.update         |Webhook update                     |
{:caption="Table 1. List of actions that genererate an event" caption-side="top"}

Currently, the {{site.data.keyword.cloudaccesstrailshort}} Events for {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} service are available only on `IBM Cloud - US South and US East Regions`.
{: note}
