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

# 合規性
{: #compliance}

IBM Cloud {{site.data.keyword.mobilepushshort}} 服務提供安全、可靠的方式，以將通知傳送到已登錄的行動裝置。
{: shortdesc}

## HIPAA
{: #hipaa}

IBM {{site.data.keyword.mobilepushshort}} 服務符合所需的 IBM 控制措施，這些控制措施與《1996 年健康保險可移植性和責任法案》(HIPAA) 中的「安全和隱私權規則」要求一致。{{site.data.keyword.mobilepushshort}} 服務以靜態加密格式儲存資料，並以加密形式傳輸資料。

如果您想要使用 IBM Cloud {{site.data.keyword.mobilepushshort}} 服務傳送 HIPAA 監管資訊，您不應使用 Post/訊息 API，因為透過協力廠商推送提供者傳送的有效負載可能不符合監管準則。可以改為使用下列步驟，其中僅 messageId 透過協力廠商推送提供者傳送，但是實際的機密資料由用戶端應用程式透過安全 (https) 傳輸進行下載。

1. 佈建新實例「進階方案」，或者將現有實例升級到「進階方案」。
2. 使用 {{site.data.keyword.mobilepushshort}} 服務傳送[無聲自動通知](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios)。
3. {{site.data.keyword.mobilepushshort}} 服務使用 FCM、APNS 之類的推送雲端提供者傳送通知。根據無聲自動通知的性質，警示不作為通知的一部分進行傳送。
4. 一旦裝置接收到傳輸了 ``message id`` / ``nid`` 的通知後，應用程式將呼叫 {{site.data.keyword.mobilepushshort}} 服務以使用 ``GET /message/{messageId}`` 接收通知警示。

這有助於使用 IBM Cloud {{site.data.keyword.mobilepushshort}} 服務透過安全頻道達到機密文字內容的傳輸。

IBM 與 APNS/FCM 之間沒有業務夥伴協議 (BAA)。
{: note}
## 國際標準化組織 (ISO)
{: #iso}

{{site.data.keyword.mobilepushshort}} 服務由協力廠商安全公司進行審核，並符合下列 ISO 要求：

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [搜尋所有 IBM ISO 憑證 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}。
 
## SOC 2 類型 1 憑證
{: #soccert}

{{site.data.keyword.IBM_notm}} 為 {{site.data.keyword.mobilepushshort}} 服務提供服務組織控制 (SOC) 2 類型 1 報告。這些報告會根據「美國註冊會計師協會 (AICPA) 信任服務原則」所設定的準則來評估 IBM 的作業控制措施。「信任服務原則」定義適當的控制系統，並建立服務提供者（如 IBM Cloud）的業界標準，以保護其客戶資料及資訊。

您可以從客戶入口網站要求 SOC 2 類型 1 報告，或者聯絡業務代表。或者，您可以向 [IBM Cloud 支援中心 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/support){: new_window} 開立支援問題單。

## 一般資料保護規範 (GDPR) 
{: #gdpr}

GDPR 尋求在歐盟建立協同的資料保護法律架構，旨在將市民的個人資料控制權歸還市民，同時對世界各地管理和「處理」此類資料的個人和機構進行嚴格的管制。該規範還引入了與歐盟境內和境外個人資料自由流動相關的規則。 

有了[一般資料保護規範 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.eugdpr.org/){: new_window}，{{site.data.keyword.mobilepushshort}} 服務客戶可以依賴 {{site.data.keyword.mobilepushshort}} 服務團隊對新興的資料隱私權標準和法規的理解及遵守，以及 {{site.data.keyword.IBM}} 能夠更妥善提供全套解決方案來協助各種規模的企業滿足其自己的內部資料控管要求。
