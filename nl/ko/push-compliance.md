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

# 규제 준수 
{: #compliance}

IBM Cloud {{site.data.keyword.mobilepushshort}} 서비스는 등록된 모바일 디바이스에 알림을 보낼 수 있는 신뢰할 수 있는 안전한 방법을 제공합니다.
{: shortdesc}

## HIPAA
{: #hipaa}

IBM {{site.data.keyword.mobilepushshort}} 서비스는 1996년의 HIPAA(Health Insurance Portability and Accountability Act) 보안 및 개인정보 보호 규칙 요구사항에 맞는 필수 IBM 규제를 충족합니다. {{site.data.keyword.mobilepushshort}} 서비스는 데이터를 암호화된 형식으로 저장하며 암호화된 데이터를 전송합니다.

IBM Cloud {{site.data.keyword.mobilepushshort}} 서비스를 사용하여 HIPAA 규제가 적용된 정보를 전송하려면 Post/message API를 사용할 수 없습니다. 서드파티 푸시 제공자를 통해 전송된 페이로드가 규제 가이드라인을 충족하지 못하기 때문입니다. 대신 다음 단계에 따라 서드파티 푸시 제공자를 통해 메시지 ID만 전송할 수 있으나 실제 민감한 데이터는 안전한 (https) 전송을 통해 클라이언트 애플리케이션에 의해 다운로드됩니다.

1. 새 인스턴스 고급 플랜을 프로비저닝하거나 기존 인스턴스를 고급 플랜으로 업그레이드하십시오.
2. {{site.data.keyword.mobilepushshort}} 서비스를 사용하여 [자동 알림](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios)을 전송하십시오.
3. {{site.data.keyword.mobilepushshort}} 서비스가 FCM, APNS 등의 푸시 클라우드 제공자를 사용하여 알림을 전송합니다. 자동 알림의 특성에 의해 경보가 알림의 일부로 전송되지 않습니다.
4. 일단 디바이스가 ``message id`` / ``nid`` 전송과 함께 알림을 수신하면 애플리케이션이 {{site.data.keyword.mobilepushshort}} 서비스에 대한 호출을 작성하여 ``GET /message/{messageId}``를 사용하여 알림 경보를 수신합니다.

그러면 IBM Cloud {{site.data.keyword.mobilepushshort}} 서비스를 사용하여 보안 채널을 통해 민감한 텍스트 컨텐츠를 전송하는 데 도움이 됩니다.

IBM은 APNS/FCM과 비즈니스 동업 계약(BAA)이 체결되어 있지 않습니다.
{: note}
## ISO(International Organization for Standardization)
{: #iso}

{{site.data.keyword.mobilepushshort}} 서비스는 서드파티 보안 회사의 감사를 받으며
다음 ISO 요구사항을 충족합니다.

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [모든 IBM ISO 인증서 검색 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}.
 
## SOC 2 유형 1 인증
{: #soccert}

{{site.data.keyword.IBM_notm}}에서는 {{site.data.keyword.mobilepushshort}} 서비스에 대한 SOC(Service Organization Controls) 2 유형 1 보고서를
제공합니다. 보고서는 AICPA(American Institute of Certified Public Accountants) Trust Services Principles 미국 기구에 의해
설정된 기준에 따라 IBM의 운영 제어를 평가합니다.
Trust Services Principles는 적합한 제어 시스템을 평가하고 고객의 데이터 및 정보를 안전하게 보호하기 위해
서비스 제공자(IBM Cloud 등)에 대한 업계 표준을 확립합니다.

고객 포털에서 SOC 2 유형 1 보고서를 요청하거나 영업 담당자에게 문의할 수 있습니다. 또는
[IBM Cloud 지원 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/support){: new_window}을 사용하여 지원 티켓을 열 수 있습니다.

## 일반 개인정보 보호법률(General Data Protection Regulation, "GDPR") 
{: #gdpr}

GDPR의 목적은 EU 전체에 적용되는 일관된 개인정보 보호 법 체계를 만들어, 시민들에게 자신의 개인 정보에 대한 통제권을 돌려주는 동시에 전 세계에서 이러한 정보를 호스팅하고 '처리'하는 대상에게 엄격한 규칙을 적용하는 것입니다. 이 법률은 또한 EU 내부 및 외부에서의 자유로운 개인 데이터 이동과 관련된 규칙을 도입합니다. 

[General Data Protection Regulation ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.eugdpr.org/){: new_window}을 통해 {{site.data.keyword.mobilepushshort}} 서비스 고객이
{{site.data.keyword.mobilepushshort}} 서비스 팀이 부상하는 데이터 개인정보 보호 표준 및 규제를 이해하고 준수함을 확신할 수 있으며 {{site.data.keyword.IBM}}이 내부적인 데이터 통제 요구사항을 적용하여 모든 규모의 비즈니스를 지원하기 위한 포괄적인 솔루션 스위트를 제공할 수 있음을 알 수 있습니다.
