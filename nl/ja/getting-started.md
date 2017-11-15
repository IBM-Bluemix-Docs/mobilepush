---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# チュートリアルの概説
{: #getting-started-with-push}

この {{site.data.keyword.mobilepushfull}} チュートリアルの解説では、Android アプリでのプッシュ通知の受信の有効化とデバイスへの基本的なプッシュ通知の送信のプロセスを詳しく説明します。
{:shortdesc}

<div id="prerequisites"></div>

## 始めに
{: #prereqs}

[Bluemix アカウント](https://console.bluemix.net/registration/)、{{site.data.keyword.mobilepushshort}} サービスのインスタンス、および以下のツールおよび要件が必要です。

  * Android API 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android helloPush サンプル・アプリ](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * Android Studio または Gradle のいずれかを使用してインストールされた [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} SDK および [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} SDK
  

## ステップ 1: Android デバイス用に {{site.data.keyword.mobilepushshort}} インスタンスを構成する

1. サンプル `AndroidManifest.xml` ファイルからパッケージ名をコピーします。

2. FCM アプリを作成し、Android アプリのパッケージ名を追加します。
  1. [Firebase コンソール](https://console.firebase.google.com){: new_window}で、**「プロジェクトを追加」**をクリックし、プロジェクト名を入力し、**「プロジェクトを作成」**をクリックします。
  2. **「Android アプリに Firebase を追加」**をクリックし、アプリ・パッケージ名を入力し、**「アプリの登録」**をクリックします。その後の 2 回のプロンプトは、**「続行」>「終了」**をクリックしてスキップしてかまいません。 

3. FCM 資格情報を {{site.data.keyword.mobilepushshort}} インスタンスに追加します。
  1. Firebase コンソールで**「設定」>「プロジェクトの設定」>「クラウド・メッセージング」**と進み、サーバー・キーと送信者 ID をコピーします。
  2. {{site.data.keyword.Bluemix_notm}} コンソールで、サービス・インスタンスのダッシュボードを開きます。
  3. **「管理」>「構成」**をクリックします。
  4. 送信者 ID とサーバー・キーを**「GCM/FCM プッシュ資格情報」**フィールドに入力します。

## ステップ 2: Android アプリでのプッシュ通知の送信を有効にする

1. プロジェクト・レベル `build.gradle` ファイルおよびモジュール・レベル `build.gradle` ファイルを構成します。

  * SDK 依存関係をプロジェクト・レベル `build.gradle` ファイルに追加します。
  
  ```
dependencies {
    ........
  compile group: 'com.ibm.mobilefirstplatform.clientsdk.android',
      name: 'push',
      version: '3.+',
      ext: 'aar',
      transitive: true
  .......
	      }
  ```
  {: codeblock}

  * 以下の依存関係をモジュール・レベル `build.gradle` ファイルに追加します。
  
  ```
dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * Google Play Services 依存関係を、モジュール・レベル `build.gradle` ファイルの最後にある、依存関係の後に追加します。
  
  ```
apply plugin: 'com.google.gms.google-services'
	```
  {: codeblock}
  
  * 以下の許可をアプリの `AndroidManifest.xml` ファイルに追加します。
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.USE_CREDENTIALS" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
```
  {: codeblock}
  
  * アクティビティーの通知インテント設定を追加します。 
  
  この設定により、受信した通知をユーザーが通知エリアからクリックすると、アプリが開始します。`<yourAndroidPackageName>` は、アプリで使用されるアプリ・パッケージ名に置き換えてください。
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * `RECEIVE` および `REGISTRATION` イベント通知用に FCM インテント・サービスおよびインテント・フィルターを更新します。
  
  ```
  <service android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushIntentService"
    	android:exported="true" >
    	<intent-filter>
     <action android:name="com.google.firebase.MESSAGING_EVENT" />
  </intent-filter>
  </service>
  <service
  android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPush"android:exported="true" >
  <intent-filter>
   <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
  </intent-filter>
  </service>
  ```
  {: codeblock}
  
2. Android Studio でアプリを開き、アプリ・モジュールのルート・ディレクトリーに `google-services.json` ファイルを追加します。

3. コア SDK および Push SDK を初期化します。 

初期化コードを配置する一般的な場所は、Android アプリ内のメインアクティビティーの onCreate() メソッドです。

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
ここで、`<bluemixRegionSuffix>` は、アプリがホストされている場所です。以下のいずれかの値を使用できます。

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID は、プッシュ・アプリ GUID 値であり、clientSecret はプッシュ・クライアントの秘密値です。 

## ステップ 3: Android デバイスを {{site.data.keyword.mobilepushshort}} インスタンスに登録する

1. アプリを実行します。

2. ユーザー・ベースの通知を有効にするため、MFPPush.register() API を使用してデバイスを登録します。

```
//Register the device to Push Notifications service instance
 push.registerDeviceWithUserId("userId",new MFPPushResponseListener<String>() {
 @Override
    	public void onSuccess(String response) {
    		//Handle successful device registration here
 }
 @Override
    public void onFailure(MFPPushException ex) {
         //Handle failure in device registration here
 }
 });
 ```
 {: codeblock}
 
 
 プッシュ通知の登録用の固有ユーザー ID 値を渡すために userID が使用されます。clientSecret 値も必ず指定してください。
 {: tip}
 
 ## ステップ 4: 基本的なプッシュ通知を送信する
 
 1. {{site.data.keyword.Bluemix_notm}} コンソールで、サービス・インスタンスのダッシュボードに移動します。
 2. **「管理」>「通知の送信」**をクリックします。
 3. **「送信先 (Send To)」**メニューから Android デバイスを選択します。
 4. メッセージを入力し、**「送信」**をクリックします。 
 
