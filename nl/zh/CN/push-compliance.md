---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-24"

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

# 合规性
{: #compliance}

IBM Cloud {{site.data.keyword.mobilepushshort}} 服务提供安全、可靠的方式，以将通知发送到已注册的移动设备。
{: shortdesc}

## HIPAA
{: #hipaa}

IBM {{site.data.keyword.mobilepushshort}} 服务满足所需的 IBM 控制措施，这些控制措施与《1996 年健康保险可移植性和责任法案》(HIPAA) 中的“安全性和隐私规则”要求一致。{{site.data.keyword.mobilepushshort}} 服务以静态加密格式存储数据，并以加密形式传输数据。

如果您想要使用 IBM Cloud {{site.data.keyword.mobilepushshort}} 服务发送 HIPAA 监管信息，您不应使用 Post/message API，因为通过第三方推送提供者发送的有效内容可能不满足监管准则。可以改为使用以下步骤，其中仅 messageId 通过第三方推送提供者发送，但是实际的敏感数据由客户机应用程序通过安全 (https) 传输进行下载。

1. 供应新实例“高级套餐”，或者将现有实例升级到“高级套餐”。
2. 使用 {{site.data.keyword.mobilepushshort}} 服务发送[静默通知](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios)。
3. {{site.data.keyword.mobilepushshort}} 服务使用 FCM、APNS 之类的推送云提供者发送通知。根据静默通知的特征，警报不作为通知的一部分进行发送。
4. 一旦设备接收到传输了 ``message id`` / ``nid`` 的通知后，应用程序将调用 {{site.data.keyword.mobilepushshort}} 服务以使用 ``GET /message/{messageId}`` 接收通知警报。

这有助于使用 IBM Cloud {{site.data.keyword.mobilepushshort}} 服务通过安全的通道实现敏感文本内容的传输。

IBM 与 APNS/FCM 之间没有业务伙伴协议 (BAA)。
{: note}
## 国际标准化组织 (ISO)
{: #iso}

{{site.data.keyword.mobilepushshort}} 服务由第三方安全公司进行审计，并满足以下 ISO 要求：

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [搜索所有 IBM ISO 证书 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}。
 
## SOC 2 类型 1 证书
{: #soccert}

{{site.data.keyword.IBM_notm}} 为 {{site.data.keyword.mobilepushshort}} 服务提供服务组织控制 (SOC) 2 类型 1 报告。这些报告依据美国注册会计师协会 (AICPA) 信托服务原则所设置的标准来评估 IBM 的运营控制措施。信托服务原则为 IBM Cloud 之类的服务供应者定义了充分的控制体系并建立了行业标准，以保护其客户的数据和信息。


您可以从客户门户网站请求 SOC 2 类型 1 报告，或者联系销售代表。或者，您可以向 [IBM Cloud 支持 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/support){: new_window} 开具支持凭单。

## 通用数据保护条例 (GDPR) 
{: #gdpr}

GDPR 寻求在欧盟建立协同的数据保护法律框架，旨在将市民的个人数据控制权归还市民，同时对世界各地托管和“处理”此类数据的个人和机构进行严格的管制。该条例还引入了与欧盟境内和境外个人数据自由流动相关的规则。 

有了[通用数据保护条例 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.eugdpr.org/){: new_window}，{{site.data.keyword.mobilepushshort}} 服务客户可以信赖 {{site.data.keyword.mobilepushshort}} 服务团队能够理解和遵守对新兴的数据隐私标准和法规，以及 {{site.data.keyword.IBM}} 能够更好地提供全套解决方案来协助各种规模的企业满足其自己的内部数据治理要求。
