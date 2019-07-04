---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, service instance, cordova application

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 步驟 3：配置服務實例 
{: #push_step_2}

請確定您已完成[取得通知認證](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)。

## Android 及 Chrome Apps & Extensions
{: #push_step_2_Android}

請確定您已完成[取得通知提供者認證](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)，可以設定 FCM 專案並取得認證。

若要配置 Android 應用程式及 Google Chrome Apps & Extensions 的 FCM 認證，請完成下列步驟：

1. 開啟 IBM Cloud 型錄，然後按一下您已建立的 {{site.data.keyword.mobilepushfull}} 服務實例。 
2. 按一下**管理** > **配置**。 
3. 選擇下列一個選項： 
	- 若為 Android：選取**行動**，然後使用「寄件者 ID」/「專案號碼」和「API 金鑰」更新「FCM 推送認證」標籤。 
	- 若為 Google Chrome Apps & Extensions：選取 **Web**，然後使用「寄件者 ID」/「專案號碼」和「API 金鑰」更新 Chrome Apps and Extensions 標籤。 
4. 按一下**儲存**。Push Notifications 服務現在已完成配置。

您的下一步是要[設定推送服務用戶端 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)。


## Cordova 應用程式 
{: #push_step_2_b}


Cordova 是一個平台，可使用 JavaScript、CSS 及 HTML 來建置混合式應用程式。{{site.data.keyword.mobilepushshort}} Service 支援開發 Cordova 型 iOS 及 Android 應用程式。

若要啟用 Cordova 應用程式來接收傳送至您裝置的推送通知，請完成 [Push Notifications Cordova 外掛程式 Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)。



## iOS 應用程式及 Safari 瀏覽器 
{: #enable-push-ios-notifications}


若要使用 {{site.data.keyword.mobilepushshort}} 服務傳送通知，請上傳您在步驟 1：[取得通知提供者認證](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)中建立的 `.p12` 憑證。此憑證包含私密金鑰以及建置和發佈應用程式所需的 SSL 憑證。您也可以使用 REST API 來上傳 APNs 憑證。

**附註**：`.cer` 檔案位於您的金鑰鏈存取之後，請將它匯出至您的電腦，以建立 `.p12` 憑證。

如需使用 APNs 的相關資訊，請參閱 [iOS Developer Library: Local and Push Notification Programming Guide ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1){: new_window}。

若要在 Push Notification 服務主控台上設定 APNs，請完成以下步驟：

1. 在 Push Notification 服務主控台上，選取**配置**。
2. 選擇 **Mobile** 選項，以更新 **APNs Push 認證**表單中的資訊。
3. 選擇下列一個選項：
	- 對於**行動**選項
		1. 相應地選取**沙盤推演**（開發）或**正式作業**（配送），然後上傳已建立的 `p.12` 憑證。
		  ![設定 Push Notifications 主控台](images/wizard.jpg "選取了「配置」導覽選項的 Push Notifications 主控台，其中顯示「行動」標籤和 APN 推送認證")

		1. 在**密碼**欄位中，輸入與 `.p12` 憑證檔案相關聯的密碼，然後按一下**儲存**。
	- 對於 **Web** 選項
		- 在 Safari Push 區段中，使用必要的資訊更新表單。 
		- **網站名稱**：這是您在通知中心提供的名稱。
		- **Website Push ID**：使用 Website Push ID 的反向網域字串來更新。例如，`web.com.acmebanks.www`。
		- **網站 URL**：提供應該訂閱推送通知的網站 URL。例如，`https://www.acmebanks.com`。
		- **接受的網域**這是選用性的參數。這是向使用者要求許可權的網站清單。請確定 URL 是以逗點區隔的值。請注意，如果未提供此值，將會使用網站 URL 的值。 
		- **URL 格式字串**：按一下通知時要解析的 URL。例如，["`https://www.acmebanks.com`"]。請確定 URL 使用 http 或 https 方法。
		- **Safari Web 推送憑證**上傳 .p12 憑證並提供密碼。
4. 按一下**儲存**。	
![Push Notifications 主控台](images/push_configure_safari.jpg "Web 選項頁面欄位")	

針對 iOS 應用程式設定服務之後，您需要[設定推送服務用戶端 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)。


## Chrome 及 Firefox 瀏覽器 
{: #push_step2_chromefirefox}

1. 在 Push Notifications 主控台上，選取**配置**。
2. 選取 Web 選項標籤。
![WebPush 配置](images/webpush_configure.jpg "用於定義網站的 FCM API 金鑰和 URL 的 Web Push 配置視窗")
3. 配置 FCM API 金鑰，以及將登錄以接收推送通知的網站 URL。
4. 按一下**儲存**。
5. 設定服務之後，您需要[設定推送服務用戶端 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)。


