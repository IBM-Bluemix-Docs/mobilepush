----

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Push Notifications でのセキュリティー 
{: #overview-push}
最終更新日; 2017 年 6 月 27 日
{: .last-updated}


{{site.data.keyword.mobilepushshort}} API は、次の 2 つのタイプの Secret によって保護されています。

- **appSecret**: `appSecret` は、バックエンド・アプリケーションによって通常呼び出される API を保護します。例えば、{{site.data.keyword.mobilepushshort}} を送信する API や設定を構成する API などです。
- **clientSecret**: `clientSecret` は、モバイル・クライアント・アプリケーションによって通常呼び出される API を保護します。この `clientSecret` を必要とする API は、関連 UserId を使用したデバイスの登録に関与する API 1 つのみです。モバイル・クライアントから呼び出されるその他の API は `clientSecret` を必要としません。 

`appSecret` と `clientSecret` は、アプリケーションと {{site.data.keyword.mobilepushshort}} サービスとのバインド時にすべてのサービス・インスタンスに割り振られます。secret の受け渡しの方法や、対象の API について詳しくは、[REST APIs ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://mobile.{DomainName}/imfpush/)の資料を参照してください。

## appSecret 
{: #push-api-rest-secret}

アプリケーションが {{site.data.keyword.mobilepushshort}} にバインドされると、サービスは appSecret (固有キー) を生成し、それを応答ヘッダーで渡します。IBM {{site.data.keyword.mobilepushshort}} for Bluemix Rest API を使用している場合は、REST API リファレンスを使用して、保護する必要のある API に関する情報を取得してください。詳しくは、[Push REST API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://mobile.{DomainName}/imfpush/){: new_window}を参照してください。

要求ヘッダーには appSecret が含まれている必要があります。含まれていない場合、サーバーは 401 無許可エラー・コードを返します。{{site.data.keyword.mobilepushshort}} がアプリケーションに追加されると、特定の AppID が作成されます。応答の一部として、タグの作成やメッセージの送信に使用される appSecret というヘッダーを取得します。操作は、カタログまたはボイラープレートのサービスを介して行われます。

appSecret 値を取得するには、以下のようにします。

1. プッシュ・サービスにバインドされている *app-name* をクリックします。
2. **「資格情報の表示」**リンクをクリックして appSecret (AppID) を表示します。

**「資格情報の表示」**画面に、AppSecret に関する情報が表示されます。
```
	{
    "imfpush_Dev": [
    {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://imfpush.ng.bluemix.net/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.ng.bluemix.net/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**注**: 以前のアプリケーションでは、userId フィールドが設定されたデバイスを登録または更新する場合にのみ、clientSecret の受け渡しが必要とされました。モバイル・クライアントおよびブラウザー・クライアントによって呼び出されるその他のすべての API では、clientSecret は不要でした。これらの古いアプリケーションでは引き続き、デバイスの登録や呼び出しの更新時にオプションで clientSecret を使用できます。ただし、すべてのクライアント API 呼び出しで clientSecret チェックを実施することを強くお勧めします。これを既存のアプリケーションでも実施するために、新規の `verifyClientSecret` API が公開されています。新規アプリケーションの場合、clientSecret チェックがすべてのクライアント API 呼び出しに対して実施され、この動作は `verifyClientSecret` API を使用して変更することはできません。

デフォルトでは、クライアント秘密鍵検証は新規アプリケーションに対してのみ実施されます。既存のアプリケーションと新規アプリケーションはどちらも、verifyClientSecret REST API を使用して、クライアント秘密鍵検証を使用可能または使用不可にすることができます。applicationId および deviceId を知っている可能性のあるユーザーにデバイスが公開されないようにするために、クライアント秘密鍵検証を実施することをお勧めします。

`clientSecret` は常に機密とし、モバイル・アプリケーションへのハードコーディングは絶対に行わないでください。アプリケーションの実行時に `clientSecret` を動的にプルするために使用できる、さまざまなアプリケーション初期化パターンがあります。以下のシーケンス図に、可能なパターンの概要を示します。
![Enable_Push](images/init_client_secret.jpg) 



