---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, faq, frequently asked questions

subcollection: mobile-pushnotification

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 常見問題集 
{: #faq}

### 為何我的記號失效？
{: #faq-tokens}	

對於裝置、瀏覽器及 Chrome Apps & Extensions 登錄，Push Notifications 服務會對從通知提供者（APNs for Apple 或 FCM for Google）發出的記號保持唯一參照。服務通知提供者可基於數個原因，而讓這些記號失效。 

例如，在裝置上解除安裝應用程式的期間。在這種情境中，當嘗試根據裝置失效的提供者回應遞送通知時，{{site.data.keyword.mobilepushshort}} 服務將移除裝置或 Web 瀏覽器登錄。接著，這將限制隨後不得將通知傳送至失效裝置。 

您也可能在取消登錄裝置之後遇到問題。

請確定您取得有效的伺服器 API 金鑰和寄件者 ID，以便繼續作業。請參閱[取得通知提供者認證](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)。

### 我在試圖起始設定 Web Push SDK 時，為什麼會看到 *Notification is not working for WEB_Chrome.*？
{: #faq-web-chrome}	

您可能已變更 Web Push SDK 的 FCM 認證，Chrome 瀏覽器的訊息遞送可能會失敗。請確定您呼叫 *bmsPush.unRegisterDevice*，以避免發生失敗。

### 我在試圖起始設定 Web Push 的 SDK 時收到訊息 *Service workers aren't supported in this browser*。問題可能是什麼？ 
{: #faq-service-workers}	

請遵循[步驟 3：設定推送服務用戶端 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3) 所提及的步驟。另外，也請確定：

1. 使用正確的啟動方法。 
2. 在根資料夾中包含 `manifest.json` 檔案。
3. 管理您的網站。最好是在 IBM Cloud 中建立 `node.js` 入門範本進行試用。例如：`https://<mysamplewebsite>.cloud.ibm.com/`。	

### 我如何解決 Web Push 的 Web 配置錯誤？
{: #faq-web-config-errors}	

`BMSPushSDK.js` 的 Web 推送錯誤包含失敗的資訊。請參閱[疑難排解](/docs/services/mobilepush?topic=mobile-pushnotification-errors)。	

### 如果裝置離線，通知會持續保存嗎？
{: #faq-notification-persist}	

此特性視通知提供者而定。	

### messageID 是否對於應用程式而言唯一，其大小為何？
{: #faq-messageid}	

messageID 對於應用程式而言是唯一的，大小限制為八個字元。它可以是英數字元。

### Push Notifications 在有效負載大小方面的限制為何？
{: #faq-limits-push-payload-size}	

{{site.data.keyword.mobilepushshort}} 訊息有效負載大小取決於「閘道」（FCM、APNs）及用戶端平台所配置的限制。 

若為 iOS 8 以及更新版本，接受的大小上限為 4 KB。請注意，APNs 不會傳送超過此限制的通知。若為 Android、Firefox 瀏覽器、Chrome 瀏覽器及 Chrome Apps & Extensions，容許的訊息有效負載大小上限為 4 KB。	

### 傳送的通知會儲存在 BMS 伺服器嗎？
{: #faq-bms-servers}	

是的，通知會儲存九十天。建議您不要以通知的方式傳送任何機密訊息。

### 我可以將通知傳送至處於打盹模式的裝置嗎？
{: #faq-doze-mode}	

不支援此特性。	

### Push Notifications 服務可用的不同定價方案有哪些？
{: #faq-pricing-plans}	

* <b>進階方案</b>：使用此方案的價格是 100.00 美元/實例、0.50 美元/百萬條數位訊息、0.50 美元/百萬台可定址裝置。運用進階方案，您可以傳送推送通知給 1 百萬台可定址裝置，以及傳送 1 億條數位訊息。進階方案包括參數化訊息和端對端訊息生命週期追蹤之類的功能。

* <b>基本方案</b>：使用此方案的價格是 1.00 美元/百萬條數位訊息。使用基本方案，您可以傳送推送通知至唯一的裝置、瀏覽器、端點或 Webhook 型事件。 

* <b>精簡方案</b>：這是免費方案，每個月可以免費使用 10 萬條數位訊息。不過，精簡方案服務會在無活動狀態長達 30 天之後刪除。	

### 哪裡可以找到其他資訊，例如指導教學或新增功能？
{: #faq-what-is-new}	

請瀏覽 Push Notifications 服務[視訊](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA)。	

### 通知和訊息有不同嗎？
{: #faq-diff-notification-message}	

是的。_訊息_ 是使用者提交給 {{site.data.keyword.mobilepushshort}} 服務的內容。服務會將這分派為_通知_，送到通知閘道 (APNs/FCM)，然後這會遞送到裝置或 Web 瀏覽器。

對於您提交給服務的每一則訊息，預期的對象都會收到通知。	

### Push Notifications 監視儀表板會顯示已傳送訊息的任何狀態嗎？
{: #faq-push-monitor-dashboard}	

監視公用程式會顯示每一則已傳送訊息的狀態。訊息可能處於下列狀態：
	
* 已傳送：通知所要送往的裝置數。
* 可見：通知已到達的裝置數。
* 開啟：已開啟通知的裝置數。
* 無效：記號無效的裝置數。

如需相關資訊，請參閱 [IBM Push Notifications ReST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/) 中的 GET 訊息報告。	

### 推送通知會監視一直到使用者裝置的推送通知遞送嗎？同時針對 Android 和 iOS？
{: #faq-end-user-device}	

推送通知是根據從使用者裝置看到或開啟的通知數來監視。這適用於 Android 和 iOS。不支援以裝置 ID 為基礎的監視。 

### 我收到訊息，伺服器目前無法處理要求？要如何解決呢？
{: #faq-server-unable-to-handle-requests}	

您可能會看到錯誤，錯誤碼為 FPWSE0025E。這可能是因為有太多要求，伺服器無法處理。您可以嘗試稍後再重新提交要求。	

### 我要依標籤傳送通知，但標籤的清單很長，可能難以手動新增。 
{: #faq-tag-based-notification}	

您可以使用 REST API 來自動新增標籤。請參閱 [POST 大量訊息](https://eu-gb.imfpush.cloud.ibm.com/imfpush/)。

### 如何依使用者行動裝置中儲存的資訊來過濾推送通知遞送？
{: #faq-filter-device}	

這應該是在應用程式開發的環境定義中處理。

### 我可以進一步自訂推送通知監視，以新增自訂報告，例如每個區隔的遞送報告嗎？
{: #faq-customize-delivery-report}	

不支援此特性。

### 我可以為新應用程式使用者或有段時間未存取行動應用程式的使用者建立區段嗎？
{: #faq-create-segment}	

這應該是在應用程式開發的環境定義中處理。
	
### 我可以使用 REST API 大量登錄/更新行動式裝置嗎？
{: #faq-register-mobile-devices}	

根據設計，將使用 SDK 從行動應用程式呼叫登錄/更新裝置的操作。不支援透過 REST API 大量登錄/更新。如果使用 REST API 同時呼叫許多裝置登錄/更新，則可能需要很長時間或者可能失敗。	

### 我沒有 appSecret 時，如何傳送 Push Notifications 或使用 Rest API？
{: #faq-rest-api-appsecret}	

由於 {{site.data.keyword.mobilepushshort}} 服務採用了 IAM，在使用者建立服務認證時會顯示 `apiKey` 而不是 `appSecret`。

若要使用任何 REST API，您必須使用下列 curl 指令產生存取記號：

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```

```
{
 "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```
{: codeblock}

使用上述 curl 指令產生存取記號時，您現在可以透過在 Authorization 標頭中傳遞 `Bearer <value of access_token>` 來操作 REST API。

例如：

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
