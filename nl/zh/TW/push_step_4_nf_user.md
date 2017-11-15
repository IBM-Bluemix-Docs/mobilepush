---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 以使用者為基礎的通知
{: #user_based_notifications}
前次更新：2017 年 5 月 22 日
{: .last-updated}

使用者 ID 型 {{site.data.keyword.mobilepushshort}} 是以具有自訂訊息的行動應用程式使用者為目標。運用使用者型通知，您可以選擇根據其喜好設定來通知特定個體。

## 向使用者 ID 登錄裝置
{: #register_device_wh_userid}

若要啟用「使用者 ID」設為目標的推送通知，請確定您已設定「使用者 ID」欄位來登錄裝置。     

「使用者 ID」可以是應用程式提供給裝置登錄 API 的任何字串。一般而言，行動應用程式會先執行鑑別週期，在此鑑別週期，會對鑑別服務（例如 [{{site.data.keyword.amafull}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/docs/services/mobileaccess/index.html){: new_window}）鑑別行動應用程式使用者。鑑別成功時，接著會將已鑑別使用者 ID 傳遞至「推送裝置登錄 API」。 

若要登錄以 userId 為基礎的通知，請完成：

- [登錄 Android 應用程式](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [登錄 iOS 應用程式](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [登錄 Cordova 應用程式](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [登錄 Web 應用程式](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## 使用 userId 型通知
{: #using_userid}

userId 型通知是以特定使用者為目標的通知訊息。可向一個使用者登錄多個裝置。下列步驟說明如何傳送使用者 ID 型通知。

1. 從 **Push Notification** 主控台中，選取**傳送通知**選項。
1. 在**傳送至**選項清單中，選取**使用者 ID**。
1. 在**使用者 ID** 欄位中，搜尋您要使用的使用者 ID，然後按一下 **+ 新增**。![通知畫面](images/user_notification.jpg)
1. 在**訊息**欄位中，輸入要在通知中傳送的文字。
1. 按一下**傳送**。


## 同步化使用者登入及登出 
{: #sync_login_logout}

只有在使用者已登入時，您才能選擇傳送通知。 

例如，請考慮使用工作團隊成員共用的裝置，而且需要定址特定使用者。在這類使用案例中，將會有使用者登入及登出序列。此鑑別機制容許應用程式追蹤現行應用程式使用者的身分。這確保一律只有該使用者才會接收到以特定使用者為目標的通知。在成功登入之後，請呼叫傳遞已登入使用者之「使用者 ID」的裝置登錄 API。同樣地，登出之前，請呼叫裝置 `unregistration` API。排序這些具有登入及登出的 Push API，可確保只將要送往特定使用者的通知傳送給該使用者。
