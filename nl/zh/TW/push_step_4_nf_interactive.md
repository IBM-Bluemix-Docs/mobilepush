---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 互動式及無聲自動通知  
{: #interactive-notifications}
前次更新：2017 年 5 月 22 日
{: .last-updated}

互動式通知可讓使用者在不開啟應用程式的情況下，就可以回應通知。當互動式通知到達時，裝置會顯示動作按鈕以及通知訊息。 

**附註：**版本在 8 之前的 iOS 裝置上不支援互動式通知。 

## 傳送互動式通知
{: #send_interactive_notifications}

您可以使用 Push 主控台或使用 [REST API 文件](push_restapi.html)來傳送互動式通知。

從 {{site.data.keyword.mobilepushshort}} 主控台，請執行下列動作： 

1. 在通知標籤上，按一下**傳送通知**。 
2. 選擇您的通知收件者，然後按**下一步**。 
3. 在「編寫通知」頁面中，將「類型」設為「預設值」或「混合」，並在「進階選項」標籤下指定「種類」值，即可傳送互動式推送。 

## 處理互動式通知 
{: #handle_interactive_notifications}

- 若為 iOS，請完成[在 Swift 應用程式上啟用及處理互動式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications)。
- 若為 Cordova，請完成[在 Cordova 應用程式上啟用及處理互動式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications)。
- 若為 Android，請完成[在 Android 應用程式上啟用及處理互動式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications)。


## 處理 iOS 的無聲自動通知
{: #send_silent_notifications_for_ios}

無聲自動通知不會出現在裝置畫面上，而是由應用程式在背景中接收。如需相關資訊，請參閱 [Silent Notifications on iOS devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification)。
