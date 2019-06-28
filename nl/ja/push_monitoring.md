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

# 通知のモニター 
{: #push_monitoring}

IBM {{site.data.keyword.mobilepushshort}} サービスの機能が拡張され、ユーザー・データからグラフを生成することにより、プッシュのパフォーマンスをモニターできるようになりました。 ユーティリティーを使用して、すべての送信プッシュ通知をリストするか、すべての登録デバイスをリストして、日次、週次、または月次ベースで情報を分析できます。

すべての送信通知のレポートを生成するには、[REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/messages/get_apps_applicationId_messages_report){: new_window} で Push Messages GET レポート・メソッドを使用します。 
	![送信通知レポート - 棒グラフ](images/monitoring_messages1.png "月別データを基準にした送信通知の棒グラフ")
<br>&nbsp;</br>
	![送信通知レポート - セクター図](images/monitoring_messages2.png "プラットフォームを基準にした通知セクターの図")
すべての登録デバイスのレポートを生成するには、[REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/#!/devices/get_apps_applicationId_devices_report){: new_window} で Push Device Registrations GET レポート・メソッドを使用します。
	![登録済みデバイスのレポート - 折れ線グラフ](images/monitoring_devices1.png "登録済みデバイスの折れ線グラフ")
<br>&nbsp;</br>
	![登録済みデバイスのレポート - 円グラフ](images/monitoring_devices2.png "プラットフォームを基準にした登録済みデバイスの円グラフ")

モニタリング・ユーティリティーを有効にする方法については、ご使用のプラットフォームに応じて以下を参照してください。

 - [Android デバイスでのプッシュ通知のモニター](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
 - [iOS アプリケーションでのプッシュ通知のモニター](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).

注:

1. {{site.data.keyword.mobilepushshort}} のモニタリング・タブには分析データは表示されません。
2. REST API を使用して生成されたレポートは、キャッシュに入れられて、キャッシュは 30 分間維持されます。
また、グラフに表されるデータがキャッシュ・データから生成されます。
 
