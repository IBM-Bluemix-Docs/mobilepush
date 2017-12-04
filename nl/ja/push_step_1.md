
---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# ステップ 2: 通知プロバイダーの資格情報の取得
{: #push_step_1}
最終更新日; 2017 年 6 月 27 日
{: .last-updated}

{{site.data.keyword.mobilepushshort}} サービスをセットアップするには、必要な資格情報をプッシュ通知プロバイダーから入手する必要があります。 

## Android の場合
{: #push_step_1_android}

Firebase Cloud Messaging (FCM) は、Android デバイス、Google Chrome ブラウザー、Chrome のアプリケーションおよび拡張機能にプッシュ通知を配信するために使用されるゲートウェイです。コンソール上で {{site.data.keyword.mobilepushshort}} サービスをセットアップするには、FCM 資格情報 (送信側 ID および API キー) を取得する必要があります。 

API キーは、{{site.data.keyword.mobilepushshort}} サービスによって安全に保管され、FCM サーバーに接続するために使用されます。送信側 ID (プロジェクト番号) は、クライアント側の Android SDK (Google Chrome の場合) および JS SDK (Mozilla Firefox の場合) によって使用されます。 

FCM をセットアップし、資格情報を取得するには、次のステップを実行します。

1. [Firebase コンソール![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.firebase.google.com/?pli=1){: new_window}にアクセスします。Google ユーザー・アカウントが必要です。 
2. **「プロジェクトの追加」**を選択します。 
3. 「プロジェクトの作成」ウィンドウで、プロジェクト名を指定し、国/地域を選択して、**「プロジェクトを作成」**をクリックします。
3. ナビゲーション・ペインで、**「設定」** > **「プロジェクトの設定」**を選択します。
4. プロジェクト資格情報 (サーバー API キーおよび送信側 ID) を取得するため、「クラウド・メッセージング」タブを選択します。FCM でリストされるサーバー・キーはサーバー API キーと同じであることに注意してください。
   
	![FCM の資格情報の取得](images/FCM_settings_2.jpg)

`google-services.json` ファイルも生成する必要があります。以下のステップを実行します。

1. Firebase コンソールで、**「Project Settings (プロジェクト設定)」** アイコンをクリックします。

    
	     ![Firebase のプロジェクト設定](images/FCM_settings_6.jpg)

3. アプリケーション・ペインの「一般」タブから、**「ADD APP」**または**「Android アプリへの Firebase の追加」**アイコンを選択します。

    
4. 「Android アプリへの Firebase の追加 (Add Firebase to your Android app)」ウィンドウで、パッケージ名として **com.ibm.mobilefirstplatform.clientsdk.android.push** を追加します。「アプリのニックネーム (App nickname)」フィールドはオプションです。**「ADD APP」**をクリックします。 
    
	![「Android への Firebase の追加」ウィンドウ](images/FCM_1.jpg)

5. 「Android アプリへの Firebase の追加 (Add Firebase to your Android app)」ウィンドウにパッケージ名を入力して、アプリケーションのパッケージ名を組み込みます。「アプリのニックネーム (App nickname)」フィールドはオプションです。**「REGISTER APP」**をクリックします。 

	![アプリケーションのパッケージ名の追加](images/FCM_settings_4.jpg)

6. `google-services.json` ファイルが生成されます。 


FCM 資格情報を取得し、`google-services.json` ファイルを生成したら、次のステップでは、[サービス・インスタンスを作成](push_step_2.html)します。

**注:** FCM は、Google Cloud Messaging (GCM) の新バージョンです。新規アプリケーションには必ず FCM 資格情報を使用してください。既存のアプリケーションは、引き続き GCM 構成で機能します。

## iOS の場合
{: #push_step_1_ios}

iOS デバイスおよびアプリケーションの場合、Apple Push Notification Service (APNs) を使用して、アプリケーション開発者は IBM Cloud (プロバイダー) 上の {{site.data.keyword.mobilepushshort}} サービス・インスタンスから iOS デバイスおよびアプリケーションにリモート通知を送信することができます。メッセージは、デバイス上のターゲット・アプリケーションに送信されます。 

APNs 資格情報を取得して構成する必要があります。APNs の証明書は、{{site.data.keyword.mobilepushshort}}サービスによって安全に管理され、プロバイダーとしての APNs サーバーへの接続に使用されます。


### アプリ ID の登録
{: #push_step_1_ios_2}

アプリ ID (バンドル ID) は、特定のアプリケーションを識別する固有の ID です。各アプリケーションにアプリ ID が必要です。{{site.data.keyword.mobilepushshort}}サービスのようなサービスが、特定のアプリ ID に対して構成されます。

[Apple Developers ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com/){: new_window} アカウントを持っていることを確認してください。これは必須の前提条件です。

2. [Apple Developer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com){: new_window}ポータルにアクセスし、**「Member Center」**をクリックし、**「Certificates, Identifiers & Profiles」**を選択します。
3. **「Identifiers」** > **「App IDs」セクション**と進みます。
3. **「Registering App IDs」**ページで、「App ID Description」の「Name」フィールドにアプリ名を入力します。例えば、ACME Push Notifications です。
4. 「App ID Prefix」にストリングを入力します。  
4. 「App ID Suffix」には**「Explicit App ID」**を選択し、「Bundle ID」に値を入力します。ドメイン名を逆にしたスタイルのストリングを指定することをお勧めします。例えば、`com.ACME.push` です。
5. **「Push Notifications」**チェック・ボックスを選択し、**「Continue」**をクリックします。
6. 設定を確認してから、**「Register」** > **「Done」**をクリックします。

これで、アプリケーション ID が登録されました。 

   ![登録済みアプリケーション ID](images/push_ios_register_appid.jpg)
  

### 開発および配布用 APNs SSL 証明書の作成
{: #push_step_1_ios_3}

APNs 証明書を取得する前に、最初に証明書署名要求 (CSR) を生成し、それを Apple の認証局 (CA) にサブミットしておく必要があります。CSR には、ユーザーの会社を識別する情報および Apple プッシュ通知に署名するために使用する公開鍵と秘密鍵が含まれます。次に、iOS 開発者ポータル (iOS Developer Portal) で SSL 証明書を生成します。証明書は、公開鍵および秘密鍵と共に「キーチェーンアクセス」に保管されます。


APNs は、以下の 2 つのモードで使用できます。 

* サンドボックス・モード。開発およびテスト用です。
* 実動モード。App Store (またはその他のエンタープライズ配布メカニズム) を介してアプリケーションを配布するときのモードです。

開発環境と配布環境では別々の証明書を取得する必要があります。証明書は、リモート通知の受信者であるアプリのアプリ ID に関連付けられます。実動の場合、2 つまで証明書を作成できます。IBM Cloud は、その証明書を使用して APNs との SSL 接続を確立します。


<!-- Create a development and distribution SSL certificate. -->

1. [Apple Developer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com){: new_window} Web サイトにアクセスし、**「Member Center」**をクリックし、**「Certificates, Identifiers & Profiles」**を選択します。
2. **「Identifiers (ID)」**エリアで、**「App IDs (アプリ ID)」**をクリックします。
3. アプリ ID のリストからアプリ ID を選択し、**「Edit」**を選択します。
4. **「Push Notifications」**チェック・ボックスを選択してから、以下を行います。
	-  「Development SSL Certificate」ペインで**「Create Certificate..」**をクリックします。
	-  「Production SSL Certificate」ペインで**「Create Certificate..」**をクリックします。

	![プッシュ通知 SSL 証明書](images/certificate_createssl.jpg)

5. **「証明書署名要求 (CSR) の作成について (About Creating a Certificate Signing Request (CSR))」**画面が表示されたら、Mac で**「キーチェーンアクセス」**アプリケーションを開始して、証明書署名要求 (CSR) を作成します。**「Continue」**をクリックします。
6. 「Upload CSR file」オプションで**「Choose File」**をクリックし、ファイル `CertificateSigningRequest.certSigningRequest` を選択します。 
7. **「Continue」**をクリックします。
8. 「Download, Install and Backup」ペインで**「Download」**をクリックします。`aps_development.cer` ファイルがダウンロードされます。
	
	![証明書のダウンロード](images/push_certificate_download.jpg)	
	
6. メニューから、**「キーチェーンアクセス」>「証明書アシスタント」>「認証局に証明書を要求…」**を選択します。 
7. **「証明書情報」**で、アプリ開発者アカウントに関連付けられている E メール・アドレスと通称を入力します。開発用 (サンドボックス) と配布用 (実動) のいずれの証明書であるかを識別するのに役立つ、分かりやすい名前にしてください。例えば、_sandbox-apns-certificate_ または _production-apns-certificate_ などです。
8. **「ディスクに保存」**を選択し、`.certSigningRequest` ファイルをデスクトップにダウンロードしてから、**「続ける」**をクリックします。
9. **「別名で保存」**メニュー・オプションで、`.certSigningRequest` ファイルに名前を指定し、**「保存」**をクリックします。
10. **「完了」**をクリックします。これで CSR を使用できるようになりました。
11. **「証明書署名要求 (CSR) の作成について (About Creating a Certificate Signing Request (CSR))」**ウィンドウに戻り、**「続ける」**をクリックします。 
12. **「Generate (生成)」**画面で、**「Choose File... (ファイルの選択...)」**をクリックして、デスクトップに保存した CSR ファイルを選択します。次に、**「Generate (生成)」**をクリックします。


	![証明書の生成](images/generate_certificate.jpg)
13. 証明書ができたら、**「Done (完了)」**をクリックします。
14. **「Push Notifications (プッシュ通知)」**画面で、**「Download (ダウンロード)」**をクリックして証明書をダウンロードし、次に**「Done (完了)」**をクリックします。 
	
	![証明書のダウンロード](images/certificate_download.jpg)

15. Mac で、**「キーチェーンアクセス」 > 「自分の証明書」**に進み、新規にインストールした証明書を見つけます。証明書をダブルクリックして、それを「キーチェーンアクセス」にインストールします。
16. 「証明書」と「秘密鍵」を選択してから、**「書き出し」**を選択して、個人情報交換形式 (`.p12` 形式) に証明書を変換します。
	

	![証明書および鍵のエクスポート](images/keychain_export_key.jpg)
17. **「別名で保存」**フィールドで、証明書に意味のある名前を指定します。例えば、`sandbox_apns.p12_certifcate` または `production_apns.p12` などです。その後、**「保存」**をクリックします。
	
	
	![証明書および鍵のエクスポート](images/certificate_p12v2.jpg)
18. **「パスワードの入力」**フィールドで、エクスポートされる項目を保護するためのパスワードを入力し、**「OK」**をクリックします。このパスワードは、Push Notifications サービスのコンソールで APNs 設定を構成するために使用できます。
	
	![証明書および鍵のエクスポート](images/export_p12.jpg)
19. **「Key Access.app」**は、**「Keychain」**画面から、キーをエクスポートするように求めるプロンプトを出します。ご使用の Mac の管理パスワードを入力して、システムによるそれらの項目のエクスポートを許可し、**「常に許可」**オプションを選択します。`.p12` 証明書がデスクトップ上に生成されます。


### 開発プロビジョニング・プロファイルの作成
{: #create-push-credentials-dev-profile}

プロビジョニング・プロファイルは、アプリ ID を使用して機能し、アプリをインストールして実行できるデバイス、およびアプリからアクセスできるサービスを判別します。各アプリ ID ごとに、2 つのプロビジョニング・プロファイル、すなわち、開発用に 1 つ、配布用にもう 1 つを作成します。Xcode は、開発プロビジョニング・プロファイルを使用して、アプリケーションのビルドを許可されている開発者と、アプリケーションのテストが許可されているデバイスを判別します。

アプリ ID を登録済みであること、それを {{site.data.keyword.mobilepushshort}} サービス用に使用可能化していること、および開発および実動の APNs SSL 証明書を使用するように構成済みであることを確認します。

以下のように、開発プロビジョニング・プロファイルを作成します。

1. [Apple Developer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com){: new_window}ポータルにアクセスし、**「Member Center」**をクリックし、**「Certificates, Identifiers & Profiles」**を選択します。
2. [Mac Developer Library ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com/library/mac/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW62site){: new_window}にアクセスし、**「Creating Development Provisioning Profiles」**セクションにスクロールし、指示に従って開発プロファイルを作成します。
**注**: 開発プロビジョン・プロファイルを構成する際に、以下のオプションを選択します。
	* **「iOS App Development (iOS アプリ開発)」**
	* **「For iOS and watchOS apps (iOS アプリおよび watchOS アプリ用)」 **


### ストア配布プロビジョニング・プロファイルの作成
{: #create-push-credentials-apns-distribute_profile}

ストア・プロビジョニング・プロファイルを使用して、ご使用のアプリを配布用にアプリ・ストアにサブミットします。

1. [Apple Developer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com){: new_window}ポータルにアクセスし、**「Member Center」**をクリックし、**「Certificates, Identifiers & Profiles」**を選択します。
2. ダウンロードしたプロビジョニング・プロファイルをダブルクリックして、Xcode にインストールします。
                    

資格情報を取得したら、次のステップでは、[サービス・インスタンスを構成](push_step_2.html)します。

## Web ブラウザー、Chrome のアプリケーションおよび拡張機能の場合
{: #configure-credential-for-browsers}

IBM {{site.data.keyword.mobilepushshort}} サービスの機能が拡張され、使用しているブラウザーと、Chrome アプリケーションおよび拡張機能にも通知を送信できるようになりました。

許可が必要な要求を識別するために、{{site.data.keyword.mobilepushshort}} サービスによって Web サイト URL または Web サイトのドメイン・ネームが要求されます。 

例: `https://www.acmebanks.com`

{{site.data.keyword.mobilepushshort}} サービス・インスタンスがサポートするのは、1 度に 1 つのドメイン・ネームのみです。したがって、Chrome、Firefox、および Safari に同じ値を設定するようにしてください。Chrome ブラウザーと Safari ブラウザーには、Web プッシュ用の追加構成が必要です。Chrome ではメッセージを送信するために FCM エンドポイントが使用されるため、FCM API キーが必要になります。 

Chrome ブラウザー、Firefox ブラウザー、および Chrome アプリケーションおよび拡張機能用にサービスをセットアップするには、[サービス・インスタンスの構成](push_step_2.html)を参照してください。


### Safari Web プッシュの構成 
{: #configure-safari}

Safari でサポートされる {{site.data.keyword.mobilepushshort}} サービスのバージョンは 10.0 です。ブラウザーで通知を受信するように構成する前に、Apple Developer アカウントを介して証明書を生成する必要があります。

#### 証明書の生成
{: #certificate-generation}

Apple 開発者アカウントを必ず取得しておいてください。Safari ブラウザーで通知を受け取るように構成するには、Web サイト Push ID を登録し、証明書を生成する必要があります。以下の手順を使用して、開始してください。

1. Apple Developer Member センターで、**「Certificates, ID & Profiles」**をクリックします。 
2. **「Identifiers (ID)」**をクリックして、**「Website Push IDs (Web サイト Push ID)」**をクリックします。
3. 新規エントリーの作成を選択するため、プラス・アイコンを選択します。![Push Notifications コンソール](images/safari_1.jpg)

4. 「Register Website Push ID (Web サイト Push ID の登録)」パネルで、適切な Web サイト Push ID の説明と識別子 ID を入力します。これは、`web` で始まる反転ドメイン名形式にすることをお勧めします。例えば、`web.com.acmebanks` です。
5. Web サイト Push ID を登録します。これで、Web サイト Push ID を使用できるようになりました。 
6. **「編集」**を選択して、Web サイト Push ID 用に使用する証明書を作成します。
7. 「Certificate Information (証明書情報)」の「Certificate Assistant (証明書アシスタント)」ウィンドウで、E メール ID と共通名を入力します。「Certificate Authority email address (認証局 E メール・アドレス)」はブランクのままにします。
8. **「Save to disk (ディスクに保存)」**をクリックし、**「続行」**を選択します。
9. 必要に応じて証明書を適切なフォルダーに保存してください。
10. 証明書を生成するためのウィザードでプロンプトが出されたときにディスク上で作成された `.certSigningRequest` を選択します。必ず `.cer` フォーマットで作成された Web サイト・プッシュ証明書をダウンロードしてください。
11. 「キーチェーンアクセス」ツールで証明書を開きます。右クリックして、p12 証明書としてエクスポートします。p12 証明書の生成時に指定したパスワードをメモしてください。

証明書の生成後、次のステップは、[サービス・インスタンスの構成](push_step_2.html)です。

