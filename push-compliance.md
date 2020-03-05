---

copyright:
  years: 2018, 2020
lastupdated: "2020-02-04"

keywords: push notifications, notifications, compliance, hipaa, iso, soc 2 type 2 certification, gdpr

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

# Compliance
{: #compliance}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} Service provides a trustworthy and secure way to send notifications to the registered mobile devices.
{: shortdesc}

## HIPAA
{: #hipaa}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.mobilepushshort}} Service meets the required {{site.data.keyword.IBM_notm}} Controls that are commensurate with the Health Insurance Portability and Accountability Act of 1996 (HIPAA) Security and Privacy Rule requirements. The {{site.data.keyword.mobilepushshort}} Service stores the data in encrypted format at rest, and transmits the data encrypted.

If you want to send HIPAA regulated information by using the {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} Service that you should not be using Post/message API, since the payload sent over third-party Push providers might not meet regulatory guidelines. Instead, you can use the following steps where only messageId is sent over third-party Push providers, but the actual sensitive data is downloaded by the client application over a secure (https) transport.

1. Provision a new instance.
1. Send a [silent notification](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios) by using the {{site.data.keyword.mobilepushshort}} Service.
1. The {{site.data.keyword.mobilepushshort}} Service sends the notification by using the push cloud providers like FCM, APNS. By the characteristics of the silent notification alert are not sent as part of the notification.
1. Once the device receives notification with the ``message id`` / ``nid`` transmitted, application makes a call to the {{site.data.keyword.mobilepushshort}} Service to receive the notification alert by using the ``GET /message/{messageId}``.

This helps in achieving transmission of sensitive text content over a secured channel by using the {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} Service.

IBM doesn't have Business Associate Agreements (BAA) relation with APNS/FCM.
{: note}

## International Organization for Standardization (ISO)
{: #iso}

{{site.data.keyword.mobilepushshort}} Service is audited by a third-party security firm and meets the following ISO requirements:

* [{{site.data.keyword.cloud_notm}} ISO 27001](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: external}
* [{{site.data.keyword.cloud_notm}} ISO 27017](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: external}
* [{{site.data.keyword.cloud_notm}} ISO 27018](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: external}
* [Search all IBM ISO certificates](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: external}.
 
## SOC Certification
{: #soccert}

{{site.data.keyword.mobilepushshort}} Service is SOC1 Type 2, SOC2 Type 2, SOC3 audit certified for the Security and Availability principles. The reports evaluate IBM's operational controls according to the criteria set by the American Institute of Certified Public Accountants (AICPA) Trust Services Principles. 
The Trust Services Principles define adequate control systems and establish industry standards for service providers such as {{site.data.keyword.cloud_notm}} to safeguard their customers' data and information. For more information on compliance, visit this [blog](https://admin.blogs.prd.ibm.event.ibm.com/w3-techblog/compliance/).

You can request an SOC Certification report from the customer portal or contact your sales representative. Alternatively, you can open a support ticket with 
[IBM Cloud support](https://www.ibm.com/cloud/support){: external}.

## General Data Protection Regulation (GDPR) readiness
{: #gdpr}

Please visit [IBM's commitment to GDPR readiness](https://www.ibm.com/data-responsibility/gdpr/) page to learn about IBM’s GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey. 

- [IBM Data Processing Addendum (DPA)](https://www.ibm.com/support/customer/csol/terms/?cat=dpa) 
