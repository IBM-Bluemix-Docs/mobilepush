---

copyright:
  years:  2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, service access, manage, user roles

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# サービス・アクセスの管理
{: #service-access-management}

{{site.data.keyword.mobilepushshort}} と {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) を使用すると、アカウント所有者は自分のアカウント内でユーザー・アクセスを管理できます。
{: shortdesc}

アカウント所有者は、アカウント内にポリシーを設定して、さまざまなユーザー用にさまざまなレベルのアクセス権限を作成できます。 例えば、特定のユーザーに対して、あるインスタンスについては**「読み取り専用」**アクセス権限を付与し、別のインスタンスについては**「書き込み」**アクセス権限を付与することができます。 どのユーザーに、{{site.data.keyword.mobilepushshort}} のインスタンスの作成、更新、削除を許可するかを決定することができます。

**注:** {{site.data.keyword.mobilepushshort}} サービスは IAM を採用しているため、新規インスタンスのアプリ・シークレットは生成されません。代わりに [API キー](https://cloud.ibm.com/docs/iam?topic=iam-manapikey)を使用する必要があります。

## ユーザー役割
{: #roles}

アクセス・ポリシーの有効範囲は、ユーザーの割り当てられた役割に基づいています。
{: shortdesc}

ポリシーにより、アクセス権限をさまざまなレベルで付与することができます。 オプションには以下のものがあります。
<ul><ul>
  <li>自分のアカウント内のサービスのすべてのインスタンスにわたるアクセス</li>
  <li>自分のアカウント内の個別のサービス・インスタンスへのアクセス</li>
  <li>インスタンス内の特定のリソースへのアクセス</li>
  <li>自分のアカウント内のすべての IAM 対応のサービスへのアクセス</li>
</ul></ul>

ユーザーは、プラットフォーム管理役割を使用して、プラットフォーム・レベルでサービス・リソースに対するタスクを実行できます。 例えば、役割を割り当てることにより、ID の作成や削除、インスタンスの作成、アプリへのインスタンスのバインドを実行できるユーザーを決定できます。 以下の表は、プラットフォーム管理役割と相関するアクションについて詳しく示しています。

<table>
  <tr>
    <th>プラットフォーム役割</th>
    <th>許可</th>
    <th>アクションの例</th>
  </tr>
  <tr>
    <td><i>ビューアー</i></td>
    <td>{{site.data.keyword.mobilepushshort}} インスタンスを表示します。</td>
    <td>クラウド・ディレクトリー・ユーザーのデータや ID プロバイダーの構成を表示できます。</td>
  </tr>
  <tr>
    <td><i>エディター</i></td>
    <td>{{site.data.keyword.mobilepushshort}} インスタンスを表示およびバインドできます。</td>
    <td>アプリケーションを {{site.data.keyword.mobilepushshort}} のインスタンスにバインドできます。</td>
  </tr>
  <tr>
    <td><i>オペレーター</i></td>
    <td>{{site.data.keyword.mobilepushshort}} インスタンスを作成、削除、編集、一時停止、再開、表示、またはバインドすることができます。</td>
    <td>カタログから {{site.data.keyword.mobilepushshort}} インスタンスを作成または削除することができます。</td>
  </tr>
  <tr>
    <td><i>管理者</i></td>
    <td>アカウント内のすべてのサービスに対するすべての管理アクション。</td>
    <td>すべてのオペレーター・アクション、および他のユーザーにポリシーを割り当てる機能を実行できます。</td>
  </tr>
</table>

</br>
</br>
次の表は、サービス・アクセス役割にマップされたアクションについて詳しく示しています。ユーザーは、サービス・アクセス役割を使用して、{{site.data.keyword.mobilepushshort}} にアクセスしたり、{{site.data.keyword.mobilepushshort}} API を呼び出したりできます。


<table>
  <tr>
    <th>サービス役割</th>
    <th>許可</th>
    <th>アクションの例</th>
  </tr>
  <tr>
    <td><i>リーダー</i></td>
    <td>{{site.data.keyword.mobilepushshort}} インスタンス・データを表示します。</td>
    <td>ユーザー・データや ID プロバイダー情報など、サービス・インスタンスの詳細を表示できます。</td>
  </tr>
  <tr>
    <td> <i>ライターまたは管理者</i></td>
    <td>{{site.data.keyword.mobilepushshort}} インスタンスを表示および変更できます。</td>
    <td>リーダーのすべてのアクション、およびサービス・インスタンスの編集 (ID プロバイダー構成の編集など) を実行できます。 </li></ul></td>
  </tr>
</table>

UI でユーザー役割を割り当てる方法について詳しくは、[IAM アクセス権限の管理](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser)を参照してください。


## {{site.data.keyword.mobilepushshort}} アクセス・ポリシー
{: #access}

ご使用のアカウント内の {{site.data.keyword.mobilepushshort}} サービスにアクセスするすべてのユーザーには、IAM ユーザー役割が定義されたアクセス・ポリシーを割り当てる必要があります。そのポリシーにより、選択したサービスまたはインスタンスのコンテキスト内でユーザーが実行できるアクションを決定します。
{: shortdesc}

アクションは、{{site.data.keyword.Bluemix_notm}} サービスで実行が許可された操作として、そのサービスでカスタマイズおよび定義されます。 その後、アクションは IAM ユーザー役割にマップされます。 実行したアクションのいくつかは、{{site.data.keyword.cloudaccesstrailshort}} サービスを使用して追跡できます。 以下の表では、{{site.data.keyword.mobilepushshort}} のアクションと必要な許可がマップされています。

| アクション |説明|必要な役割|
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |アプリ設定の取得 |管理者、ライター、リーダー |
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |アプリ設定の削除 |管理者|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |アプリ設定の更新 |管理者|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |デバイスの取得 |管理者、ライター、リーダー |
|`POST /imfpush/v1/apps/{applicationId}/devices` |デバイスの登録 |管理者、ライター |
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |デバイスの更新 |管理者、ライター |
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |デバイスの削除 |管理者|
|`POST /imfpush/v1/apps/{applicationId}/messages` |メッセージの送信 |管理者、ライター |
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |メッセージの一括送信 |管理者、ライター |
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |メッセージの削除 |管理者|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |メッセージの取得 |管理者、リーダー、ライター|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |メッセージ配信状況の更新 |管理者、ライター |
|`POST /imfpush/v1/apps/{applicationId}/tags` |タグの作成 |管理者、ライター |
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |タグの更新 |管理者、ライター |
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |タグの削除 |管理者|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |タグの取得 |管理者、リーダー、ライター|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |サブスクリプションの作成 |管理者、ライター |
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |サブスクリプションの削除 |管理者|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |サブスクリプションの取得 |管理者、リーダー、ライター|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |Web フックの作成 |管理者、ライター |
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Web フックの更新 |管理者、ライター |
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Web フックの削除 |管理者|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |Web フックの取得 |管理者、リーダー、ライター|-|

## API キーの処理
{: #apikeys}

サービス資格情報の作成時、appSecret ではなく apiKey が表示されていることがわかります。

REST API を使用するには、以下の curl コマンドを使用してアクセス・トークンを生成する必要があります。

### パラメーター

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### 応答

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

前述の curl コマンドを使用してアクセス・トークンを生成したら、Authorization ヘッダーで「ベアラー <value of access_token>」を渡すことで、REST API を操作できるようになります。

以下に例を示します。

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

IAM について詳しくは、[IAM のアクセス権限](https://cloud.ibm.com/docs/iam?topic=iam-userroles)を参照してください。
