---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-11"

keywords: push notifications, notifications, compliance, hipaa, iso, soc 2 type 1 certification, gdpr

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Compliance
{: #compliance}

IBM Cloud {{site.data.keyword.mobilepushshort}} Service provides a trustworthy and secure way to send notifications to the registered mobile devices.
{: shortdesc}

## HIPAA
{: #hipaa}

IBM {{site.data.keyword.mobilepushshort}} Service meets the required IBM Controls that are commensurate with the Health Insurance Portability and Accountability Act of 1996 (HIPAA) Security and Privacy Rule requirements. The {{site.data.keyword.mobilepushshort}} Service stores the data in encrypted format at rest, and transmits the data encrypted.

If you want to send HIPAA regulated information using the IBM Cloud {{site.data.keyword.mobilepushshort}}  Service you should not be using Post/message API, since the payload sent over third-party Push providers may not meet regulatory guidelines. Instead, you could follow the below steps where only messageId is sent over third-party Push providers, but the actual sensitive data is downloaded by the client application over a secure (https) transport.

1. Provision a new instance Advanced Plan or upgrade your existing instance to an Advanced Plan.
2. Send a [silent notification](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios) using the {{site.data.keyword.mobilepushshort}} Service.
3. The {{site.data.keyword.mobilepushshort}} Service sends the notification using the push cloud providers like FCM, APNS. By the characteristics of the silent notification alert is not sent as part of the notification.
4. Once the device receives notification with the ``message id`` / ``nid`` transmitted, application makes a call to the {{site.data.keyword.mobilepushshort}} Service to receive the notification alert using the ``GET /message/{messageId}``.

This helps in achieving transmission of sensitive text content over a secured channel using the IBM Cloud {{site.data.keyword.mobilepushshort}} Service.

IBM doesn't have Business Associate Agreements (BAA) relation with APNS/FCM.
{: note}
## International Organization for Standardization (ISO)
{: #iso}

{{site.data.keyword.mobilepushshort}} Service is audited by a third-party security firm
and meets the following ISO requirements:

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![External link icon](../../icons/launch-glyph.svg "External link icon")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![External link icon](../../icons/launch-glyph.svg "External link icon")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![External link icon](../../icons/launch-glyph.svg "External link icon")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [Search all IBM ISO certificates ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}.
 
## SOC 2 Type 1 Certification
{: #soccert}

{{site.data.keyword.IBM_notm}} provides a Service Organization Controls (SOC) 2 Type 1 report 
for {{site.data.keyword.mobilepushshort}} Service. The reports evaluate IBM's operational controls according to the criteria set 
by the American Institute of Certified Public Accountants (AICPA) Trust Services Principles. 
The Trust Services Principles define adequate control systems and establish industry standards 
for service providers such as IBM Cloud to safeguard their customers' data and information.

You can request an SOC 2 Type 1 report from the customer portal or contact your sales representative. Alternatively, you can open a support ticket with 
[IBM Cloud support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/support){: new_window}.

## General Data Protection Regulation (GDPR) 
{: #gdpr}

The GDPR seeks to create a harmonized data protection law framework across the EU and aims to give citizens back the control of their personal data, whilst imposing strict rules on those hosting and ‘processing’ this data, anywhere in the world. The Regulation also introduces rules relating to the free movement of personal data within and outside the EU. 

With the [General Data Protection Regulation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.eugdpr.org/){: new_window}, {{site.data.keyword.mobilepushshort}} Service customers can rely on 
the {{site.data.keyword.mobilepushshort}} Service team's understanding and compliance with emerging data privacy standards and legislation and also in {{site.data.keyword.IBM}}'s wider ability to provide a comprehensive suite of solutions to assist businesses of all sizes with their own internal data governance requirements.
