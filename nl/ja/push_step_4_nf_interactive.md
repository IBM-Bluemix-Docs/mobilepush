---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, interactive notification, silent notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 対話式通知とサイレント通知  
{: #interactive-notifications}

対話式通知により、ユーザーはアプリケーションを開かずに通知に応答することができます。 対話式通知が到着すると、デバイスは通知メッセージとともにアクション・ボタンを表示します。 

**注:** バージョン 8 より前の iOS デバイスでは、対話式通知はサポートされていません。 

## 対話式通知の送信
{: #send_interactive_notifications}

Push Notifications Push コンソールを使用するか、[REST API 資料](https://cloud.ibm.com/apidocs/push-notifications)を使用することによって、対話式通知を送信できます。


{{site.data.keyword.mobilepushshort}} コンソールから以下を実行します。 

1. 「通知」タブで、**「通知の送信」**をクリックします。 
2. 通知の受信側を選択して、**「次へ」**をクリックします。 
3. 「通知の作成」ページで、「タイプ」を「デフォルト」または「混合」のいずれかに設定し、「詳細オプション」タブの下で「カテゴリー」値を指定することで、対話式プッシュを送信できます。 

## 対話式通知の処理 
{: #handle_interactive_notifications}

- iOS の場合、[Swift アプリケーションでの対話式通知の有効化および処理](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications)に関する資料を参照してください。
- Cordova の場合、[Cordova アプリケーションでの対話式通知の有効化および処理](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications)に関する資料を参照してください。
- Android の場合、[Android アプリケーションでの対話式の有効化および処理](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications)に関する資料を参照してください。


## iOS のサイレント通知の処理
{: #send_silent_notifications_for_ios}

サイレント通知は、デバイス画面には表示されず、アプリケーションによってバックグラウンドで受信されます。 詳しくは、[iOS デバイスでのサイレント通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification)に関する資料を参照してください。
