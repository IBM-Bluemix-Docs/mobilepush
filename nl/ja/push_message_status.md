---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# メッセージの配信状況
{: #tag_based_notifications}
最終更新日: 2017 年 8 月 21 日
{: .last-updated}


{{site.data.keyword.mobilepushshort}} サービスでは、サービスに送信されたすべての通知の配信状況を表示できます。 

メッセージが送信されたら、メッセージの配信状況を表示することによって配信情報を追跡できます。サービスはいつでも、90 日の期間内で使用可能な 10 個の最新メッセージのみの状況を表示します。

{{site.data.keyword.mobilepushshort}} サービスの**「メッセージ」**タブに、通知の状況が表示されます。

![通知の状況](images/notification_status_new.png)

1. **メッセージ ID** -  メッセージを特定するための固有 ID。

2. **メッセージ・テキスト** - アプリケーション・ユーザーに送信されたメッセージ・テンプレート。

3. **日付** - メッセージがサービスに送信された日時。

4. **状況** - メッセージの概要を提供します。メッセージの配信状況に応じて、次のいずれかの状況が表示される可能性があります。

 - 受け入れ済み: メッセージは、Push Notifications サービスによる配信用に受け入れられました。
   
 - ディスパッチ中 (Dispatching): 通知は通知プロバイダー (APNs、FCM、または Web) によって受信され、ディスパッチされるところです。ディスパッチ処理中の通知は、**「ディスパッチングに失敗 (Dispatching failed)」**状況で失敗を返すこともあります。
 
 - ディスパッチ済み (Dispatched): 通知は、通知プロバイダーによってディスパッチされました。
 
 - 処理中: メッセージは、通知プロバイダー・ゲートウェイへのディスパッチ処理中です。処理中の通知は、**「処理に失敗 (Processing failed)」**状況で失敗を返すこともあります。
 
 - 不明: 通知の状況を判別できません。
 
5. **表示** - ディスパッチされている通知の配信状況を表示します。以下の状況に基づいて情報を表示できます。

 - カテゴリー: すべて、モバイル、Web<!---and HTTP--->。
 
 - メッセージ状況: 送信済み、表示済み、オープン、無効。 

![通知の状況](images/message_delivery_status_new.png)

6. **オプション** - 通知の詳細な状況を提供します。状況の追跡は、ドロップダウン・メニューから「デバイス ID (`Device Id`)」または「ユーザー ID (`User Id`)」のいずれかを選択して実行できます。失敗したメッセージを追跡しているときは、ユーザーまたはデバイスに固有の詳細な状況メッセージを取得すると役立つ可能性があります。

![詳細な状況](images/detailed_message_delivery.png)

**注**: この機能は、「アドバンスト・プラン (`Advanced Plan`)」を選択したユーザーに対してのみ有効になります。[アップグレード](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)するには、{{site.data.keyword.mobilepushshort}} サービス・コンソールで**「プラン」**を選択してください。


