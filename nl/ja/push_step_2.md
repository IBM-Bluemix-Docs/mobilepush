---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, service instance, cordova application

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# ステップ 3: サービス・インスタンスの構成 
{: #push_step_2}

[通知資格情報の取得](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)を必ず実行しておいてください。

## Android、Chrome アプリケーションおよび拡張機能の場合
{: #push_step_2_Android}

[通知プロバイダー資格情報の取得](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)を実行し、FCM プロジェクトのセットアップと資格情報の取得が完了していることを確認してください。

Android アプリケーション、Google Chrome のアプリケーションおよび拡張機能用の FCM 資格情報を構成するために、以下のステップを実行します。

1. IBM Cloud カタログを開き、作成した {{site.data.keyword.mobilepushfull}} サービス・インスタンスをクリックします。 
2. **「管理」** > **「構成」**をクリックします。 
3. 次のいずれかのオプションを選択します。 
	- Android の場合: **「モバイル」**を選択し、「FCM プッシュ資格情報」タブの内容を送信側 ID/プロジェクト番号、および API キーで更新します。 
	- Google Chrome のアプリケーションおよび拡張機能の場合: **「Web」**を選択し、「Chrome Apps and Extensions」タブの内容を送信側 ID/プロジェクト番号、および API キーで更新します。 
4. **「保存」**をクリックします。 これで、Push Notifications サービスが構成されました。

次のステップは、[プッシュ・サービス・クライアント SDK のセットアップ](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)を行うことです。


## Cordova アプリケーションの場合 
{: #push_step_2_b}


Cordova は、JavaScript、CSS、および HTML を使用したハイブリッド・アプリケーションの構築用プラットフォームです。 {{site.data.keyword.mobilepushshort}} サービスは、Cordova ベースの iOS アプリケーションおよび Android アプリケーションの開発をサポートします。

Cordova アプリケーションがデバイスへのプッシュ通知を受信できるようにするには、[Push Notifications Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app) を参照してください。



## iOS アプリケーションおよび Safari ブラウザーの場合 
{: #enable-push-ios-notifications}


{{site.data.keyword.mobilepushshort}} サービスを使用して通知を送信するには、ステップ 1: [通知プロバイダー資格情報の取得](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)で作成した `.p12` 証明書をアップロードします。 この証明書には、アプリケーションのビルドと公開に必要な、秘密鍵と SSL 証明書が含まれています。 REST API を使用して APNs 証明書をアップロードすることもできます。

**注**: `.cer` ファイルがキー・チェーン・アクセスに配置されたら、それをコンピューターにエクスポートして、`.p12` 証明書を作成します。

APNs の使用について詳しくは、[iOS Developer Library: Local and Push Notification Programming Guide ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1){: new_window}を参照してください。

Push Notification サービス・コンソールで APNs をセットアップするには、以下のステップを実行します。

1. Push Notification サービス・コンソールで**「構成」**を選択します。
2. **「モバイル」**オプションを選択し、**「APNs Push Credentials (APNs プッシュ資格情報)」**フォームの情報を更新します。
3. 次のいずれかのオプションを選択します。
	- **「モバイル」**オプションの場合
		1. **「サンドボックス」** (開発) または**「実動」** (配布) の該当する方を選択し、作成した `p.12` 証明書をアップロードします。![プッシュ通知設定のコンソール](images/wizard.jpg "「構成」ナビゲーション・オプションの「モバイル」タブと「APNs Push Credentials (APNs プッシュ資格情報)」が表示された Push Notifications コンソール")

		1. **「パスワード」**フィールドに、`.p12` 証明書ファイルに関連付けられているパスワードを入力し、次に**「保存」**をクリックします。
	- **「Web」**オプションの場合
		- 「Safari Push」セクションで、必要な情報を指定してフォームを更新します。 
		- **Website Name**: これは、「通知」センターで指定した名前です。
		- **Website Push ID**: Web サイト Push ID の反転ドメイン・ストリングを使用して更新します。 例えば、web.com.acmebanks.www です。
		- **Website URL**: プッシュ通知をサブスクライブする必要がある Web サイトの URL を指定します。 例えば、https://www.acmebanks.com です。
		- **Allowed Domains**: これは、オプション・パラメーターです。 これは、ユーザーからの許可を要求する Web サイトのリストです。 URL は、必ずコンマ区切りの値で指定します。 これが指定されていない場合は、Web サイト URL 内の値が使用されます。 
		- **URL Format String**: 通知がクリックされたときに解決される URL。 例えば、["https://www.acmebanks.com"] です。 URL には、http または https 方式を使用してください。
		-**Safari web push certificate**: .p12 証明書をアップロードし、パスワードを指定します。
4. **「保存」**をクリックします。![Push Notifications コンソール](images/push_configure_safari.jpg "Web オプション・ページのフィールド")	

iOS アプリケーション用にサービスをセットアップした後、[プッシュ・サービス・クライアント SDK のセットアップ](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)を行う必要があります。


## Chrome ブラウザーおよび Firefox ブラウザーの場合 
{: #push_step2_chromefirefox}

1. Push Notifications コンソールで**「構成」**を選択します。
2. 「Web」タブを選択します。![Web プッシュ構成](images/webpush_configure.jpg "FCM API キーと Web サイトの URL を定義する Web プッシュ構成のウィンドウ")
3. プッシュ通知を受信するために登録する FCM API キーと Web サイトの URL を構成します。
4. **「保存」**をクリックします。
5. サービスをセットアップした後、[プッシュ・サービス・クライアント SDK のセットアップ](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)を行う必要があります。


