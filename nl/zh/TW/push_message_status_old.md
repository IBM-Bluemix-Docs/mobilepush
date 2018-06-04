---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 訊息通知遞送狀態
{: #tag_based_notifications}
前次更新：2017 年 8 月 21 日
{: .last-updated}


使用 {{site.data.keyword.mobilepushshort}} 服務，您可以檢視每個提交給服務之通知的狀態。 

已提交的訊息可能有下列狀態：

- **已接受**：已接受訊息以便 Push Notifications 服務遞送之用。
- **處理中**：正在處理訊息，以便分派到通知提供者閘道。正在進行處理的通知也可能傳回失敗，並具有狀態**處理失敗**。
- **分派中**：通知提供者 - APNs、FCM 或 Web - 已收到通知且即將分派。正在進行分派的通知也可能傳回失敗，並具有狀態**分派失敗**。
- **已分派**：通知提供者已分派通知。
- **不明**：無法判斷通知的狀態。

{{site.data.keyword.mobilepushshort}} 服務的「訊息」標籤會顯示通知狀態。

![通知狀態](images/notification_status_new.png)

1. **檢視**選項會顯示已分派通知的遞送狀態。您可以根據下列方面檢視資訊：

 - 種類：全部、行動、Web<!---and HTTP--->。
 - 訊息狀態：已傳送、已看到、開啟、無效。 

![通知狀態](images/message_delivery_status_new.png)

2. 按一下**選項**可以取得**詳細訊息遞送狀態**。詳細遞送狀態可以藉由從下拉功能表選取 `Device Id` 或 `User Id` 來加以追蹤。可以提取特定使用者或裝置的詳細狀態。

![詳細狀態](images/detailed_message_delivery.png)


在任何時間點，服務只會顯示 90 天的期間內最新 10 則可用訊息的狀態。

**附註**：特性只會針對已選擇 `Advanced Pricing Plan` 的使用者啟用。在 {{site.data.keyword.mobilepushshort}} 服務主控台中選取**方案**，以便[升級](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)。
