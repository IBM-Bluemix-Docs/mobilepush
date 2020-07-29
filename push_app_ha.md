---

copyright:
  years: 2020
lastupdated: "2020-07-24"

keywords: push notifications, push notification, notifications, high availability, ha, high-availability, regional high availability, application high availability

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

# High Availability
{: #push_app-ha}

Your global strategy is important, and {{site.data.keyword.cloud}} uses global load balancing to ensure a redundant, highly-available platform is available for you to host your workloads and applications.
{: shortdesc}

## Regional high-availability
{: #regional-ha}

{{site.data.keyword.mobilepushshort}} service is a highly available, regional service that runs in multiple zones. For more information on Regional high-availability, see [here](/docs/mobilepush?topic=mobilepush-gettingstartedtemplate#regional-high-availability).

## Application high-availability
{: #push_app-ha}

Applications that communicate over networks and cloud services are subject to transient connection failures. There can be a short blip in connectivity or trigger a fail-over. You want to design your applications to retry connections when errors are caused by a temporary loss in connectivity to your deployment or to {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.mobilepushshort}} service is a managed service, regular updates occurs as part of normal operations. This can occasionally cause short intervals where your service is unavailable. It can also cause a trigger to graceful fail-over, retry, and reconnect. So you might also see a short connection interruption.

Your applications must be designed to handle temporary interruptions to the service, implement error handling for failed commands, and implement retry logic to recover from a temporary interruption.

Open a support ticket with details if you have longer time periods of failures so we can investigate.

