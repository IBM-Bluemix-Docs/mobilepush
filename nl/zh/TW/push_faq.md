---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 常見問題集 
{: #faq}


1. 為何我的記號失效？
	
	對於裝置、瀏覽器及 Chrome Apps & Extensions 登錄，Push Notifications 服務會對從通知提供者（APNs for Apple 或 FCM for Google）發出的記號保持唯一參照。服務通知提供者可基於數個原因，而讓這些記號失效。 

	例如，在裝置上解除安裝應用程式的期間。在這種情境中，當嘗試根據裝置失效的提供者回應遞送通知時，{{site.data.keyword.mobilepushshort}} 服務將移除裝置或 Web 瀏覽器登錄。接著，這將限制隨後不得將通知傳送至失效裝置。 

	您也可能在取消登錄裝置之後遇到問題。

	請確定您取得有效的伺服器 API 金鑰和寄件者 ID，以便繼續作業。請參閱[取得通知提供者認證](push_step_1.html)。


2. 我在試圖起始設定 Web Push SDK 時，為什麼會看到 "Notification is not working for WEB_Chrome."？

	您可能已變更 Web Push SDK 的 FCM/GCM 認證，Chrome 瀏覽器的訊息遞送可能會失敗。請確定您呼叫 "bmsPush.unRegisterDevice" 以避免發生失敗

3. 我在試圖起始設定 Web Push 的 SDK 時收到訊息 "Service workers aren't supported in this browser"。問題可能是什麼？ 

	請遵循[步驟 3：設定推送服務用戶端 SDK](push_step_3.html) 所提及的步驟。另外，也請確定：
 
	1. 您使用正確的啟動方法。 
	1. 在根資料夾中包含 `manifest.json` 檔案。
	1. 管理您的網站。最好是在 Bluemix 中建立 `node.js` 入門範本進行試用。例如：`https://<mysamplewebsite>.mybluemix.net/`。	

4. 我如何解決 Web Push 的 Web 配置錯誤？

	`BMSPushSDK.js` 的 Web 推送錯誤包含失敗的資訊。請參閱[疑難排解](push_troubleshooting.html)。	

5. 如果裝置離線，通知會持續保存嗎？

	此特性視通知提供者而定。	

6. messageID 是否對於應用程式而言唯一，其大小為何？

	messageID 對於應用程式而言是唯一的，大小限制為八個字元。它可以是英數字元。

7. Push Notifications 在有效負載大小方面的限制為何？

	{{site.data.keyword.mobilepushshort}} 訊息有效負載大小取決於「閘道」（FCM/GCM、APNs）及用戶端平台所配置的限制。 

	若為 iOS 8 以及更新版本，接受的大小上限為 4 KB。請注意，APNs 不會傳送超過此限制的通知。若為 Android、Firefox 瀏覽器、Chrome 瀏覽器及 Chrome Apps & Extensions，容許的訊息有效負載大小上限為 4 KB。	

8. 傳送的通知會儲存在 BMS 伺服器嗎？

	是的，通知會儲存長達七天。建議您不要以通知的方式傳送任何機密訊息。

9. 我可以將通知傳送至處於打盹模式的裝置嗎？

	不支援此特性。	

10. Push Notifications 服務可用的不同定價方案有哪些？

	基本方案：這方案的價格為 $1.00 美金/百萬數位訊息。使用基本方案，您可以傳送推送通知至唯一的裝置、瀏覽器、端點或 Webhook 型事件。 

	精簡方案：這是免費方案，特色為每個月有十萬則免費數位訊息可用。不過，精簡方案服務會在無活動狀態長達 30 天之後刪除。	

11. 哪裡可以找到其他資訊，例如指導教學或新增功能？

	請參閱 Push Notifications 服務[部落格](http://push-notification-service.mybluemix.net/)。	

12. 通知和訊息有不同嗎？

	是的。_訊息_ 是使用者提交給 {{site.data.keyword.mobilepushshort}} 服務的內容。服務會將這分派為_通知_，送到通知閘道 (APNs/FCM)，然後這會遞送到裝置或 Web 瀏覽器。

	對於您提交給服務的每一則訊息，預期的對象都會收到通知。	

13. Push Notifications 監視儀表板會顯示已傳送訊息的任何狀態嗎？

	監視公用程式會顯示每一則已傳送訊息的狀態。訊息可能處於下列狀態：
	
	- 已傳送：通知所要送往的裝置數。
	- 可見：通知已到達的裝置數。
	- 開啟：已開啟通知的裝置數。
	- 無效：記號無效的裝置數。

	如需相關資訊，請參閱 [IBM Push Notifications ReST API](https://mobile.ng.bluemix.net/imfpush/) 中的 GET 訊息報告。	

14. 推送通知會監視一直到使用者裝置的推送通知遞送嗎？同時針對 Android 和 iOS？

	推送通知是根據從使用者裝置看到或開啟的通知數來監視。這適用於 Android 和 iOS。不支援以裝置 ID 為基礎的監視。 

15. 我收到訊息，伺服器目前無法處理要求？要如何解決呢？

	您可能會看到錯誤，錯誤碼為 FPWSE0025E。這可能是因為有太多要求，伺服器無法處理。您可以嘗試稍後再重新提交要求。	

16. 我要依標籤傳送通知，但標籤的清單很長，可能難以手動新增。 
	
	您可以使用 REST API 來自動新增標籤。請參閱 [POST 大量訊息](https://mobile.ng.bluemix.net/imfpush/)。

17. 如何依使用者行動裝置中儲存的資訊來過濾推送通知遞送？

	這應該是在應用程式開發的環境定義中處理。

18. 我可以進一步自訂推送通知監視，以新增自訂報告，例如每個區隔的遞送報告嗎？

	不支援此特性。

19.  我可以為新應用程式使用者或有段時間未存取行動應用程式的使用者建立區段嗎？

	這應該是在應用程式開發的環境定義中處理。


	


	
	




	


