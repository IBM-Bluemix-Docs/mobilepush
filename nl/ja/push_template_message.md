---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, parameterize notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 通知のパラメーター化
{: #template_based_notifications}

変数を作成してそれらを通知テンプレートで呼び出すことにより、カスタム通知をパラメーター化して送信することができます。

通知テンプレートは以下のことを実行できます。

 - 通知内の静的エレメントと動的エレメントを結合する
 - 変数を追加して各受信者向けに通知を個別設定する
 - 通知に複数の変数を含めることができる 

以下のように、初期化中にアプリケーション・コード内の JSON オブジェクトとして変数を渡します。

    
   ```
    MFPPushNotificationOptions options = new MFPPushNotificationOptions();

    JSONObject tempValue = new JSONObject();
        try {
        
		tempValue.put("username",userName);
        
        tempValue.put("amountSpent",amount);
		
        tempValue.put("currency",currency);
		
        tempValue.put("avilableBalance",balance);
        
		} catch (JSONException e) {
            e.printStackTrace();
        }
        options.setPushVariables(tempValue); 
	   
	   push = MFPPush.getInstance();

       push.initialize(getApplicationContext(),appGuid,clientSecret,options);
   ```
{: codeblock}


変数を定義したら、メッセージ・テンプレートでそれらを呼び出すことができます。

1. {{site.data.keyword.mobilepushshort}} コンソールで、**「メッセージ」**タブを選択します。

2. **「送信先 (Send to)」**オプションを選択してメッセージを作成します。

3. **「メッセージ」**フィールドで、メッセージを作成します。  メッセージ・テンプレートで定義されている変数を呼び出します。 **「送信」**をクリックします。

![メッセージ・テンプレート](images/message_template.png "「送信先」フィールドが「すべてのデバイス」に設定されており、ユーザーの銀行口座の残高についてのメッセージ例を示す「メッセージ」フィールドと "key":"value" 属性が追加されている「追加ペイロード」フィールドを含むメッセージ・テンプレートを示す「メッセージ」ページ。")

以下のように、変数データを取り出すことにより、カスタム通知メッセージが送信されます。

![メッセージ例](images/message_template_example.jpg "メッセージ・テンプレートを基準にした通知例")

注: この機能は、「アドバンスト・プラン (`Advanced Plan`)」を選択したユーザーに対してのみ有効になります。 [アップグレード](https://cloud.ibm.com/docs/account?topic=account-changing#changing)するには、{{site.data.keyword.mobilepushshort}} サービス・コンソールで**「プラン」**を選択してください。

## 制限
{: #limitations}

 - 現在、この機能は Safari ではサポートされていません。
 - アプリケーションが iOS で強制終了された場合、通知テンプレートの変数は機能しない可能性があります。 この制限は、SDK の制御によるものではなく、iOS の制限になります。

