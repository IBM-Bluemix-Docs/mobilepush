---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, sending a notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 步驟 5：傳送通知
{: #push_step_4}

開發應用程式之後，您可以傳送基本推送通知。

若要傳送基本推送通知，請完成下列步驟：

1. 選取**訊息**，並透過選取**傳送至**選項來編寫訊息。支援的選項有**依標籤的裝置**、**裝置 ID**、**使用者 ID**、**Android 裝置**、**iOS 裝置**、**Web 通知**、**Chrome Apps and Extensions**、**Chrome 瀏覽器**、**Firefox**、**Safari** 和**所有裝置**。
**附註**：當您選取**所有裝置**選項時，所有已訂閱 {{site.data.keyword.mobilepushshort}} 的裝置都會接收到通知。
	
    ![通知畫面](images/tag_notification.jpg "顯示「傳送至」、「訊息」以及「其他有效負載」欄位的「傳送通知」畫面")

2. 在**訊息**欄位中，編寫訊息。視需要選擇配置選用設定。
3. 按一下**傳送**。
3. 驗證您的裝置或瀏覽器已接收到通知。

下列擷取畫面顯示在 Android 裝置的前景中處理推送通知的警示框。



![Android 上的前景推送通知](images/Android_Screenshot.jpg "含測試通知的警示方框")

下列擷取畫面顯示 Android 背景中的推送通知。
	

![Android 上的背景推送通知](images/background.jpg "Android 裝置上的推送通知")

## 選用性的 Android 設定 
{: #push_step_4_Android}

您可以進一步自訂 {{site.data.keyword.mobilepushshort}} 設定，以將通知傳送給 Android 裝置。 

![Android 自訂設定](images/android_custom_settings.jpg "「推送通知自訂設定」頁面")

支援下列選用自訂選項：

- 收合金鑰：收合金鑰會附加至通知。如果多個具有相同收合金鑰的通知在裝置離線時循序到達，則會予以收合。當裝置上線時，會接收到來自 FCM 伺服器的通知，並且只會顯示含有相同收合金鑰的最新通知。如果未設定收合金鑰，則會儲存新舊訊息，以供未來遞送。
- 音效：指出要在收到通知時播放的音效短片。支援預設值或應用程式中所組合的音效資源名稱。
- 圖示：指定要針對通知顯示的圖示名稱。請確定您已將圖示與用戶端應用程式包裝至 `res/drawable` 資料夾。
- 優先順序：指定用於指派訊息遞送優先順序的選項。 
	- 優先順序 `high` 或 `max` 會導致提前通知。
	- 優先順序 `low` 或 `default` 不會在休眠中的裝置上開啟網路連線。 
	- 優先順序 `min` 將是無聲自動通知。
- 可見性：您可以選擇將通知可見性選項設為 `public` 或 `private`。 
	- `private` 選項會限制公用檢視，因此，如果您的裝置使用 PIN 碼或型樣保護，且通知設定設為**隱藏機密通知內容**，則可以選擇啟用它。可見性設為 `private` 時，必須提及 `redact` 欄位。只有 `redact` 欄位中所指定的內容才會顯示在裝置的安全鎖定畫面上。 
	- `public` 選項會讓通知成為可自由讀取。
- 存活時間：此值是以秒為單位來設定。如果未指定此參數，則 FCM 伺服器會儲存訊息四週，並嘗試遞送。有效性會在四週後到期。可能值範圍是從 0 到 2,419,200 秒。
- 閒置時延遲：您可以將此參數設為下列其中一個值：
	- `True` 指示 FCM 伺服器如果裝置在閒置中就不要遞送通知。 
	- `False` 確定即使裝置閒置也會遞送通知。
- 同步：透過將此選項設定為 `true`，將同步所有已登錄裝置的通知。如果具有使用者名稱的使用者有多個已安裝相同應用程式的裝置，則讀取某個裝置上的通知可確保刪除其他裝置中的通知。您需要確定已使用 userId 向 {{site.data.keyword.mobilepushshort}} 服務進行登錄，此選項才能運作。
- 其他有效負載：指定通知的自訂有效負載值。
- 可展開的通知：這讓客戶能選擇展開通知的相關資訊，而基本通知顯示時會將通知收合。支援下列選項：
	- 大圖片通知：您可以選擇當通知展開時包含圖片。請務必提供圖片的標題文字和 URL。
	- 大文字通知：您可以選擇包含其他文字和標題。請務必提供大文字訊息和標題文字資訊。
	- 收件匣樣式通知：您可以使用收件匣通知的樣式來傳送通知。請提供標題文字，並逐行提供訊息。	 

## 選用性的 iOS 設定 
{: #push_step_4_ios}

您可以自訂 {{site.data.keyword.mobilepushshort}} 設定，以將通知傳送給 iOS 裝置。支援下列選用自訂選項。


- **徽章**：指出應用程式徽章上所顯示的號碼。預設值是零 (0)，而且這不會顯示徽章。 
- **音效**：指出要在收到通知時播放的音效短片。支援預設值或應用程式中所組合的音效資源名稱。
- **其他有效負載**：指定通知的自訂有效負載值。

您也可以選擇啟用[互動式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications)及[複合式多媒體通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications)。

## 監視已遞送的通知 
{: #push_step_4_monitor}

{{site.data.keyword.mobilepushshort}} 服務提供監視公用程式，以協助您檢查已傳送訊息的狀態。若要配置監視公用程式，請完成下列任一選項：

- [啟用 Android 應用程式的監視](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring)。
- [啟用 iOS 應用程式的監視](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring)。
