---

copyright:
  years: 2015, 2020
lastupdated: "2020-03-19"

keywords: push notifications, notifications, upgrading plan, lite, basic, advanced

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

# Upgrading your plan
{: #upgrade-push}

The {{site.data.keyword.mobilepushshort}} service offers three plans that provide different levels of resources and capabilities to suit your needs.
{: shortdesc}

## Pricing plan
{: #pricing-plan}

- A push notification that is sent to a unique device/end point or a webhook event constitutes a digital message. 
- An Addressable Device is a device upon which an application is installed that is addressable by the Cloud Service.
- Lite plan services are deleted after 30 days of inactivity.
{: note}

|                |Lite                           |Basic                        |Advanced                      |
|----------------|-------------------------------|-----------------------------|------------------------------|
|**Features**    |100,000 digital messages per month; 50 addressable devices |First 1 million digital messages and 10000 addressable devices free            | Charged per Instance </br> Includes 100 million digital messages and 1 million addressable devices<br/> Advanced Capabilities<br/> - [Parameterize messages](/docs/services/mobilepush?topic=mobilepush-template_based_notifications)<br/> - [End to End message lifecycle tracking](/docs/services/mobilepush?topic=mobilepush-message-delivery-status)<br/>|
|**Pricing**     |Free|- $1.00 / Ten Thousand Addressable Devices <br/> - $1.00 / Million Digital Messages <br /> |- $100.00 / Instance <br/> - $0.50 / Million Digital Messages <br/> - $0.50 / Million Addressable Devices <br/> |
{:caption="Table 1. Service plans" caption-side="top"}

## Upgrading a service
{: #upgrading-a-service}

To upgrade your plan, complete these steps:

1. From the {{site.data.keyword.Bluemix_notm}} menu, select **Services** > **Dashboard**.
1. Select the service instance that you want to upgrade to open it.
1. Click **Plan** from the navigation pane.
   From here, you can see your current plan and other available plan options, and make changes.

For information about calculating costs, see the [{{site.data.keyword.Bluemix_notm}} Pricing Calculator](https://cloud.ibm.com/estimator){: external}.
