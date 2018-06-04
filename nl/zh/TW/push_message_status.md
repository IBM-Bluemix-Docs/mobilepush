---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 訊息遞送狀態
{: #tag_based_notifications}
前次更新：2017 年 8 月 21 日
{: .last-updated}


使用 {{site.data.keyword.mobilepushshort}} 服務，您可以檢視每個提交給服務之通知的遞送狀態。 

傳送訊息之後，您可以查看訊息遞送狀態來追蹤訊息的遞送資訊。在任何時間點，服務只會顯示 90 天的期間內最新 10 則可用訊息的狀態。

{{site.data.keyword.mobilepushshort}} 服務的**訊息**標籤會顯示通知狀態。

![通知狀態](images/notification_status_new.png)

1. **訊息 ID** - 識別訊息用的唯一 ID。

2. **訊息文字** - 傳送給應用程式使用者的訊息範本。

3. **日期** - 訊息提交給服務的日期和時間。

4. **狀態** - 提供訊息的簡短摘要狀態。視訊息的遞送狀態而定，您可能會看到下列其中一個狀態：

 - 已接受：已接受訊息以便 Push Notifications 服務遞送之用。
   
 - 分派中：通知提供者 - APNs、FCM 或 Web - 已收到通知且即將分派。正在進行分派的通知也可能傳回失敗，並具有狀態**分派失敗**。
 
 - 已分派：通知提供者已分派通知。
 
 - 處理中：正在處理訊息，以便分派到通知提供者閘道。正在進行處理的通知也可能傳回失敗，並具有狀態**處理失敗**。
 
 - 不明：無法判斷通知的狀態。
 
5. **檢視** - 顯示已分派通知的遞送狀態。您可以根據下列方面檢視資訊：

 - 種類：全部、行動、Web<!---and HTTP--->。
 
 - 訊息狀態：已傳送、已看到、開啟、無效。 

![通知狀態](images/message_delivery_status_new.png)

6. **選項** - 提供通知的詳細狀態。狀態可以藉由從下拉功能表選取 `Device Id` 或 `User Id` 來加以追蹤。取得使用者/裝置特定的詳細狀態訊息可能有助於您追蹤失敗的訊息。

![詳細狀態](images/detailed_message_delivery.png)

**附註**：特性只會針對已選擇 `Advanced Plan` 的使用者啟用。在 {{site.data.keyword.mobilepushshort}} 服務主控台中選取**方案**，以便[升級](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)。


