---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-09-25"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Activity Tracker Events
{: #push_activity_tracker}

The {{site.data.keyword.cloudaccesstrailfull}} service monitors a user's interaction with the {{site.data.keyword.cloud_notm}} services. You can search and analyze how your users and applications interact with {{site.data.keyword.cloud_notm}} services.

Refer to the [Activity Tracker Page](https://cloud.ibm.com/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started){: new_window} for details.

## List of events by {{site.data.keyword.IBM}} Cloud {{site.data.keyword.mobilepushshort}} service
{: #actions}

{{site.data.keyword.IBM}} Cloud {{site.data.keyword.mobilepushshort}} service is now able to send events to {{site.data.keyword.cloudaccesstrailfull}}
 service. You can choose to track activity on the {{site.data.keyword.IBM}} Cloud {{site.data.keyword.mobilepushshort}} service by creating an instance of [{{site.data.keyword.cloudaccesstrailfull}}
 service](https://cloud.ibm.com/observe/activitytracker/create).

The following table lists the {{site.data.keyword.cloudaccesstrailfull}} events for {{site.data.keyword.IBM}} Cloud {{site.data.keyword.mobilepushshort}} service:

|Action                             |Description                        |
|-----------------------------------|-----------------------------------|
|imfpush.app.update                 |Updates to the Application         |
|imfpush.app-conf.delete            |Application configuration deletion |
|imfpush.app-conf.update            |Application configuration update   |
|imfpush.app-device.create          |Device registration                |
|imfpush.app-device.delete          |Device un-registration             |
|imfpush.app-tag.create             |Tag creation                       |
|imfpush.app-tag.delete             |Tag deletion                       |
|imfpush.app-tag.update             |Tag update                         |
|imfpush.app-subscription.create    |Device subscription for a tag      |
|imfpush.app-subscription.delete    |Device un-subscription for a tag   |
|imfpush.app-message.create         |Send message                       |
|imfpush.app-webhook.create         |Webhook creation                   |
|imfpush.app-webhook.delete         |Webhook deletion                   |
|imfpush.app-webhook.update         |Webhook update                     |
{:caption="Table 1. List of actions that genererate an event" caption-side="top"}

Currently, the Activity Tracker Events for {{site.data.keyword.IBM}} Cloud {{site.data.keyword.mobilepushshort}} service are available only on `IBM Cloud - US South and US East Regions`.
{: note}
