---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# メッセージ通知の配信状況
{: #tag_based_notifications}
最終更新日: 2017 年 8 月 21 日
{: .last-updated}


{{site.data.keyword.mobilepushshort}} サービスでは、サービスに送信されたすべての通知の状況を表示できます。 

送信されたメッセージは、以下の状況の可能性があります。

- **受け入れ済み**: メッセージは、Push Notifications サービスによる配信用に受け入れられました。
- **処理中**: メッセージは、通知プロバイダー・ゲートウェイへのディスパッチ処理中です。処理中の通知は、**「処理に失敗 (Processing failed)」**状況で失敗を返すこともあります。
- **ディスパッチ中 (Dispatching)**: 通知は通知プロバイダー (APNs、FCM、または Web) によって受信され、ディスパッチされるところです。ディスパッチ処理中の通知は、**「ディスパッチングに失敗 (Dispatching failed)」**状況で失敗を返すこともあります。
- **ディスパッチ済み (Dispatched)**: 通知は、通知プロバイダーによってディスパッチされました。
- **不明**: 通知の状況を判別できません。

{{site.data.keyword.mobilepushshort}} サービスの「メッセージ」タブに、通知の状況が表示されます。

![通知の状況](images/notification_status_new.png)

1. **「表示」**オプションは、ディスパッチされている通知の配信状況を表示します。以下の状況に基づいて情報を表示できます。

 - カテゴリー: すべて、モバイル、Web<!---and HTTP--->。
 - メッセージ状況: 送信済み、表示済み、オープン、無効。 

![通知の状況](images/message_delivery_status_new.png)

2. **「オプション」**をクリックすると、**詳細なメッセージ配信状況**が表示されます。詳細な配信状況は、ドロップダウン・メニューから「デバイス ID (`Device Id`)」または「ユーザー ID (`User Id`)」のいずれかを選択して追跡できます。特定のユーザーまたはデバイスの詳細な状況を取り出すことができます。

![詳細な状況](images/detailed_message_delivery.png)


サービスはいつでも、90 日の期間内で使用可能な 10 個の最新メッセージの状況のみを表示します。

**注**: この機能は、「アドバンスト価格プラン (`Advanced Pricing Plan`)」を選択したユーザーに対してのみ有効になります。[アップグレード](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)するには、{{site.data.keyword.mobilepushshort}} サービス・コンソールで**「プラン」**を選択してください。
