---

copyright:
  years: 2018, 2019
lastupdated: "18 February 2019"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Compliance
{: #compliance}

IBM Cloud {{site.data.keyword.mobilepushshort}} Service provides a trustworthy and secure way to send notifications to the registered mobile devices.
{: shortdesc}

## HIPAA
{: #hipaa}

IBM {{site.data.keyword.mobilepushshort}} Service meets the required IBM Controls that are commensurate with the Health Insurance Portability and Accountability Act of 1996 (HIPAA) Security and Privacy Rule requirements. The {{site.data.keyword.mobilepushshort}} Service stores the data in encrypted format at rest, and transmits the data encrypted.

If you are part of regulatory industry like HIPAA and want to send sensitive information using the IBM Cloud {{site.data.keyword.mobilepushshort}}  Service you should not be using Post/message API, since the payload sent over third-party Push providers may not meet regulatory guidelines. Instead, you could follow the below steps where only messageId is sent over third-party Push providers, but the actual sensitive data is downloaded by the client application over a secure (https) transport.

1. Provision a new instance Advanced Plan or upgrade your existing instance to an Advanced Plan.
2. Send a [silent notification](https://cloud.ibm.com/docs/services/mobilepush/push_step_4_nf_interactive.html#send_silent_notifications_for_ios) using the {{site.data.keyword.mobilepushshort}} Service.
3. The {{site.data.keyword.mobilepushshort}} Service sends the notification using the push cloud providers like FCM, APNS. By the characteristics of the silent notification alert is not sent as part of the notification.
4. Once the device receives notification with the ``message id`` / ``nid`` transmitted, application makes a call to the {{site.data.keyword.mobilepushshort}} Service to receive the notification alert using the ``GET /message/{messageId}``.

This helps in achieving transmission of sensitive text content over a secured channel using the IBM Cloud {{site.data.keyword.mobilepushshort}} Service.

**Note**: IBM doesn't have Business Associate Agreements (BAA) relation with APNS/FCM.
