---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, tag-based, creating tags, managing tags, get tag, subscribe tag

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 標籤型通知
{: #tag_based_notifications}

標籤型通知是指以所有訂閱特定標籤之裝置為目標的訊息。標籤型通知容許根據主旨區域或主題分段通知。只有在通知是所感興趣的主旨或主題時，通知收件者才能選擇接收通知。因此，標籤型通知提供一種方法來分段收件者。此特性會啟用定義標籤後根據標籤來傳送及接收訊息的能力。訊息只會以訂閱標籤的用戶端應用程式實例（在行動裝置或瀏覽器上，或者作為應用程式或延伸規格）為目標。您必須先建立應用程式的標籤，並設定標籤訂閱，然後起始標籤型通知。若要傳送使用 REST API 的標籤型通知，請確定在公佈至訊息資源時提供 "tagNames"。

您可以定義標籤，然後使用標籤來傳送及接收訊息。您必須先建立應用程式的標籤、建立訂閱，然後起始標籤型通知。若要使用 [REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: new_window} 傳送標籤型通知，請確定在公佈至訊息資源時已提供 "tagName"。


## 管理標籤
{: #manage_tags}

使用 {{site.data.keyword.mobilepushshort}} 主控台來建立及刪除您應用程式的標籤，然後起始標籤型通知。標籤型通知是在訂閱標籤的裝置上接收。


### 建立標籤
{: #create_tags}

標籤型通知是指以所有訂閱特定標籤之裝置為目標的訊息。每一個裝置都可以訂閱任意數目的標籤。 

1. 在 {{site.data.keyword.mobilepushshort}} 主控台上，選取**管理標籤**標籤。
1. 按一下 + **建立標籤**按鈕。   
   1. 在**名稱**欄位中，輸入標籤的名稱。例如，"coupons"。
   1. 在**說明**欄位中，輸入標籤說明。
   1. 按一下**儲存**。

1. 在**程式碼 Snippet** 區域中，選取您行動應用程式的平台。
1. 修改程式碼 Snippet 來處理錯誤，然後將每一個標籤的程式碼 Snippet 複製到行動應用程式。

### 刪除標籤
{: #delete_tags}

1. 從**標籤**標籤中，選取您要刪除的標籤，然後按一下**刪除**圖示。
1. 按一下**確定**。

刪除標籤時，會刪除與該標籤相關聯的資訊（包括其訂閱者及裝置）。不需要自動取消訂閱，因為標籤不再存在。用戶端不需要採取任何進一步動作。

### 編輯標籤說明
{: #edit_tags}

1. 從**標籤**標籤中，選取您要編輯的標籤。
1. 按一下**編輯**圖示。
1. 編輯標籤說明，然後按一下**儲存**按鈕。

## 取得標籤
{: #get_tags}

標籤提供的方法是根據使用者的興趣將目標通知傳送給使用者，與傳送給所有應用程式的一般播送不同。您可以使用 {{site.data.keyword.mobilepushshort}} 主控台上的「標籤」標籤或使用 REST API 來建立及管理標籤。您可以使用程式碼 Snippet 來管理及查詢行動應用程式的標籤訂閱。您可以使用程式碼 Snippet 來取得訂閱、訂閱標籤、取消訂閱標籤，或取得可用標籤清單。請將這些程式碼 Snippet 複製到行動應用程式中。


- 若為 Android，請參閱 [Push Notification get tags on Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app) 中的 `getTags` API 和 `getSubscriptions` API。

- 若為 Cordova，請參閱 [Push Notifications get tags on Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags) 中的 `retrieveAvailableTags()` API 和 `retrieveSubscriptions()` API。

- 若為 iOS，請參閱 [Push Notifications get tags on Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags) 中的 `retrieveAvailableTagsWithCompletionHandler` API。

- 若為 Web 瀏覽器，請參閱 [Push Notifications get tag on web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags) 中的 `retrieveAvailableTags()` API。


## 訂閱標籤
{: #Subscribe_tags}

使用下列 API，可容許裝置擷取標籤、訂閱標籤，擷取子訂閱以及取消訂閱標籤。

- 若為 Android，請使用 `getTags`、`subscribe`、`getSubscriptions` 及 `unsubscribeFromTags` API。請參閱 [Push Notifications subscribe tags for Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags)。

- 若為 Cordova，請使用 `retrieveAvailableTags()`、`subscribe()`、`retrieveSubscriptions()` 及 `unsubscribe()` API。請參閱 [Push Notifications subscribe tags for Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags)。

- 若為 iOS，請使用 `retrieveAvailableTagsWithCompletionHandler`、`subscribeToTags`、`retrieveSubscriptionsWithCompletionHandler` 及 `unsubscribeFromTags` API。請參閱 [Push Notifications subscribe tags for Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags)。

- 若為 Web 瀏覽器，請使用 `retrieveAvailableTags()`、`subscribe()`、`retrieveSubscriptions()` 及 `unSubscribe()` API。請參閱 [Push Notifications subscribe tags for web browsers](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags)。

## 使用標籤型通知
{: #using_tags}

標籤型通知是指以所有訂閱特定標籤之裝置為目標的訊息。每一個裝置都可以訂閱任意數目的標籤。本主題說明如何傳送標籤型通知。訂閱透過 {{site.data.keyword.mobilepushshort}} Service IBM Cloud 實例進行維護。刪除標籤時，會刪除與該標籤相關聯的所有資訊（包括其訂閱者及裝置）。無需對此標籤進行自動取消訂閱，因為此標籤已不存在，因此也不需要從用戶端採取進一步的動作。

在**標籤**畫面上建立標籤。如需如何建立標籤的相關資訊，請參閱[建立標籤](/docs/services/mobilepush?topic=mobile-pushnotification-tag_based_notifications#create_tags)。

1. 從 **Push Notification** 主控台中，按一下**訊息**。
2. 選取**傳送至**下拉清單中的**依標籤的裝置**選項。
3. 搜尋想要使用的標籤，並將其選取。
![通知畫面](images/tag_notification_new2.jpg "選取了「訊息」導覽選項的 Push Notifications 主控台，其中顯示「傳送通知」頁面。「傳送至」欄位設定為「依標籤的裝置」。")
4. 在**訊息文字**欄位中，輸入將當作通知傳送給已訂閱讀者的文字。
5. 按一下**傳送**。

