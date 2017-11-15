---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 監視通知 
{: #push_monitoring}
前次更新：2017 年 6 月 22 日
{: .last-updated}


IBM {{site.data.keyword.mobilepushshort}} 服務現在已擴充功能，可藉由從您的使用者資料產生圖形，來監視推送效能。您可以使用此公用程式來列出所有已傳送的推送通知，或是列出所有已登錄裝置，並以每日、每週或每月為基礎分析資訊。

若要產生所有已傳送通知的報告，請使用 [REST API](https://mobile.{DomainName}/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window} 中的 Push Messages GET report 方法。 
	![已傳送通知的報告](images/monitoring_messages.jpg)


若要產生所有已登錄裝置的報告，請使用 [REST API](https://mobile.{DomainName}/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window} 中的 Push Device Registrations GET report 方法。
	![已登錄裝置的報告](images/monitoring_devices.jpg)

請注意，{{site.data.keyword.mobilepushshort}} 監視標籤不會顯示分析資料。

如需如何啟用平台之監視公用程式的相關資訊：

 - [在 Android 裝置上監視推送通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring)。
 - [在 iOS 應用程式上監視推送通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring)。
 



 
