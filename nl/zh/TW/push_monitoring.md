---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, monitoring notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 監視通知 
{: #push_monitoring}

IBM {{site.data.keyword.mobilepushshort}} 服務現在已擴充功能，可藉由從您的使用者資料產生圖形，來監視推送效能。您可以使用此公用程式來列出所有已傳送的推送通知，或是列出所有已登錄裝置，並以每日、每週或每月為基礎分析資訊。

若要產生所有已傳送通知的報告，請使用 [REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window} 中的 Push Messages GET report 方法。 
	![已傳送通知報告 - 條狀圖](images/monitoring_messages1.png "根據每月資料的已傳送通知條狀圖")
<br>&nbsp;</br>
	![已傳送通知報告 - 扇形圖](images/monitoring_messages2.png "根據平台的已傳送通知扇形圖")

若要產生所有已登錄裝置的報告，請使用 [REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window} 中的 Push Device Registrations GET report 方法。
	![已登錄的裝置報告 - 線條圖](images/monitoring_devices1.png "已登錄的裝置線條圖")
<br>&nbsp;</br>
	![已登錄裝置報告 - 圓餅圖](images/monitoring_devices2.png "根據平台的已登錄裝置圓餅圖")


如需如何啟用平台之監視公用程式的相關資訊：

 - [在 Android 裝置上監視推送通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring)。
 - [在 iOS 應用程式上監視推送通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring)。

附註：

1. {{site.data.keyword.mobilepushshort}} 監視標籤不會顯示分析資料。
2. 將會快取使用 REST API 產生的報告，且快取會維護三十分鐘。此外，圖形中所呈現的資料會從快取資料產生。
 
