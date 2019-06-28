---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, faq, frequently asked questions

subcollection: mobile-pushnotification

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# よくある質問 
{: #faq}

### トークンが無効化されるのはなぜでしょうか?
{: #faq-tokens}	

デバイス、ブラウザー、Chrome のアプリケーションおよび拡張機能の登録のために、Push Notifications サービスは、通知プロバイダー (Apple の場合は APNs、Google の場合は FCM) から発行されたトークンへの固有の参照を維持します。 いくつかの理由で、これらのトークンがサービス通知プロバイダーによって無効化されることがあります。 

例えば、デバイス上のアプリのアンインストール時について考えてみます。 この場合、そのデバイスが無効になったというプロバイダーの応答に基づいて通知の配信が試行されると、{{site.data.keyword.mobilepushshort}}サービスはデバイスまたは Web ブラウザーの登録を削除します。 その結果として、これらの無効にされたデバイスに通知を送信しようとする試みが抑えられることになります。 

デバイスを登録抹消した場合にもこの問題が起こることがあります。

続行するには、有効なサーバー API キーおよび送信者 ID を必ず入手してください。 [通知プロバイダー資格情報の入手](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)を参照してください。

### Web Push SDK を初期化しようとすると *Notification is not working for WEB_Chrome.* というメッセージが出されるのはなぜでしょうか?
{: #faq-web-chrome}	

Web push SDK の FCM 資格情報が変更されている場合、Chrome ブラウザーでメッセージの配信が失敗する可能性があります。 失敗しないようにするために、必ず *bmsPush.unRegisterDevice* を呼び出してください。

### Web Push の SDK を初期化しようとすると *Service workers aren't supported in this browser* というメッセージが出されます。 何が問題なのでしょうか? 
{: #faq-service-workers}	

[ステップ 3: プッシュ・サービス・クライアント SDK のセットアップ](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)で説明されている手順に従ってください。	また、以下を必ず行ってください。

1. 正しい start メソッドを使用する。 
2. ルート・フォルダーに `manifest.json` ファイルを組み込む。
3. Web サイトをホストする。 `node.js` スターターを IBM Cloud に作成して試すことをお勧めします。 例: https://<mysamplewebsite>.cloud.ibm.com/。	

### Web プッシュ Web 構成エラーの解決方法はありますか?
{: #faq-web-config-errors}	

`BMSPushSDK.js` からの Web プッシュ・エラーには、障害に関する情報が含まれています。 [トラブルシューティング](/docs/services/mobilepush?topic=mobile-pushnotification-errors)を参照してください。	

### デバイスがオフラインであっても通知は永続的に保持されますか?
{: #faq-notification-persist}	

この機能は通知プロバイダーに依存します。	

### messageID はアプリケーション固有ですか? そのサイズは?
{: #faq-messageid}	

messageID はアプリケーション固有であり、8 文字までに制限されています。 英数字を使用できます。

### ペイロード・サイズという観点での Push Notifications の制限はどのようなものですか?
{: #faq-limits-push-payload-size}	

{{site.data.keyword.mobilepushshort}} のメッセージ・ペイロード・サイズは、ゲートウェイ (FCM、APNs) およびクライアント・プラットフォームによって課せられる制約によって決まります。 

iOS 8 以降では、許容される最大サイズは 4 キロバイトです。 APNs はこの制限を超える通知を送信しないことに注意してください。 Android、Firefox ブラウザー、Chrome ブラウザー、Chrome のアプリケーションおよび拡張機能では、メッセージ・ペイロードの許容される最大サイズとして、4 キロバイトの制限があります。	

### 送信された通知は BMS サーバーに保管されますか?
{: #faq-bms-servers}	

はい。通知は 90 日間保管されます。 機密メッセージを通知として送信することは推奨されません。

### Doze モードのデバイスに通知を送信できますか?
{: #faq-doze-mode}	

この機能はサポートされていません。	

### Push Notifications サービスの価格プランにはどのようなものがありますか?
{: #faq-pricing-plans}	

* <b>アドバンスト・プラン</b>: これは、インスタンスごとに $100.00 USD、100 万件のデジタル・メッセージあたり $0.50 USD、および 100 万のアドレス指定可能デバイスあたり $0.50 USD で使用可能です。このアドバンスト・プランでは、100 万のアドレス指定可能デバイスと、1 億件のデジタル・メッセージにプッシュ通知を送信できます。アドバンスト・プランには、メッセージのパラメーター化やエンドツーエンドのメッセージ・ライフサイクルのトラッキングなどの機能も含まれています。

* <b>基本プラン</b>: これは、100 万デジタル・メッセージ当たり $1.00 USD で使用可能です。 基本プランをご使用の場合、固有のデバイス、ブラウザー、エンドポイントまたは Web フック・ベースのイベントに、プッシュ通知を送信できます。 

* <b>ライト・プラン</b>: これは無料プランで、1 カ月当たり 10 万件のデジタル・メッセージを使用できます。 ただし、ライト・プラン・サービスは、非アクティブで 30 日経過すると削除されます。	

### チュートリアルや最新情報などの情報はどこで得られますか?
{: #faq-what-is-new}	

Push Notifications サービスの[ビデオ](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA)を参照してください。	

### 通知とメッセージに相違点はありますか?
{: #faq-diff-notification-message}	

はい。 _メッセージ_ は、ユーザーが {{site.data.keyword.mobilepushshort}} サービスに送信するものです。 それがサービスによって_通知_ として通知ゲートウェイ (APNs/FCM) にディスパッチされ、デバイスまたは Web ブラウザーに配信されます。

このサービスにサブミットするメッセージごとに、対象者は通知を受け取ります。	

### 送信されたメッセージの状況は Push Notifications モニター・ダッシュボードに表示されますか?
{: #faq-push-monitor-dashboard}	

モニター・ユーティリティーは、送信されたすべてのメッセージの状況を表示します。 メッセージの状況には以下のものがあります。
	
* Sent: 通知が送信されたデバイスの数。
* Seen: 通知が到着したデバイスの数。
* Open: 通知が開かれたデバイスの数。
* Invalid: トークンが無効であるデバイスの数。

詳しくは、[IBM Push Notifications ReST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/) で GET messages report を参照してください。	

### エンド・ユーザー・デバイスまでのプッシュ通知配信がモニターされますか? それは Android と iOS の両方で行われますか?
{: #faq-end-user-device}	

プッシュ通知のモニターは、エンド・ユーザー・デバイスから表示またはオープンされた通知の数に基づきます。 これは Android と iOS の両方で有効です。 デバイス ID に基づくモニターはサポートされていません。 

### 「現在サーバーは要求を処理できません」というメッセージが出されます。 どうすれば解決できるでしょうか?
{: #faq-server-unable-to-handle-requests}	

エラー・コード FPWSE0025E のエラーが表示されることがあります。 これは、サーバーが処理する要求が多すぎることが原因である可能性があります。 後で要求を再サブミットしてみてください。	

### タグ別に通知を送信しようとしていますが、タグのリストが長くて手動で追加するのは困難です。 
{: #faq-tag-based-notification}	

REST API を使用してタグ追加を自動化できます。 [POST bulk messages](https://eu-gb.imfpush.cloud.ibm.com/imfpush/) を参照してください。

### ユーザーのモバイル・デバイスに保管された情報でプッシュ通知の配信をフィルター操作する方法はありますか?
{: #faq-filter-device}	

これはアプリケーション開発のコンテキストで処理される必要があります。

### プッシュ通知のモニターをさらにカスタマイズして、セグメンテーション別の配信レポートといったカスタム・レポートを追加できますか?
{: #faq-customize-delivery-report}	

この機能はサポートされていません。

### しばらくモバイル・アプリにアクセスしていない新規アプリ・ユーザー用にセグメントを作成できますか?
{: #faq-create-segment}	

これはアプリケーション開発のコンテキストで処理される必要があります。
	
### REST API を使用して一括でモバイル・デバイスを登録/更新できますか?
{: #faq-register-mobile-devices}	

設計に従って、デバイスの登録/更新は、SDK を使用してモバイル・アプリケーションから呼び出されます。REST API を介した一括での登録/更新はサポートされていません。REST API を使用して多数のデバイスの登録/更新が同時に呼び出されると、時間がかかったり、失敗したりする可能性があります。	

### appSecret を持たない場合に、どのようにすれば Push Notifications を送信したり Rest API を使用したりできますか?
{: #faq-rest-api-appsecret}	

{{site.data.keyword.mobilepushshort}} サービスは IAM を採用しているため、ユーザーがサービス資格情報を作成する場合、`apiKey` が `appSecret` の代わりに表示されます。

REST API を使用するには、以下の curl コマンドを使用してアクセス・トークンを生成する必要があります。

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```

```
{
 "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```
{: codeblock}

前述の curl コマンドを使用してアクセス・トークンを生成したら、Authorization ヘッダーで `ベアラー <value of access_token>` を渡すことで、REST API を操作できるようになります。

以下に例を示します。

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
