---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# ステップ 4: サービス・クライアント SDK のセットアップ
{: #push_step_3}
最終更新日; 2017 年 6 月 27 日
{: .last-updated}

[通知資格情報の取得](push_step_1.html)および[プッシュ・サービス・インスタンスの構成](push_step_2.html)を実行済みであることを確認してください。次に、プッシュ通知の登録、サブスクライブ、および受信を Push Notifications サービスを使用して行えるようにアプリケーションをセットアップする必要があります。 

サービス・クライアント SDK をセットアップするには、アプリケーション・タイプに応じて以下のステップを実行します。

## Android アプリケーションの場合
{: #push_step_3_Android}

Android アプリケーションでデバイスへのプッシュ通知を受け取れるようにすることができます。Android Studio が前提条件であり、Android プロジェクトをビルドするための推奨方式です。Android Studio の基本知識が必要です。

[通知プロバイダー資格情報の取得](push_step_1.html)を実行し、FCM プロジェクトのセットアップと資格情報の取得が完了していることを確認してください。

[Push Notifications Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) の手順を実行して、サービスから送信されたプッシュ通知を Android アプリケーションが受信できるようにします。 

1. Android Studio でアプリを開きます。[ステップ 2: 資格情報の取得](push_step_1.html)で作成した `google-services.json` ファイルを Android アプリケーション・モジュールのルート・ディレクトリーにコピーします。この `google-service.json` ファイルには、追加されたパッケージ名が含まれていることに注意してください。

    ![アプリケーションのルート・ディレクトリーへの json ファイルの追加](images/FCM_7.jpg)

2. 「Android アプリへの Firebase の追加 (Add Firebase to your Android app)」ウィンドウで、**「続行」**をクリックして、**「終了 (Finish)」**をクリックします。 
3. アプリケーションをビルドして、実行します。ビルドが正常に終了したら、`Gradle build finished` というメッセージが表示されます。
4. Gradle を使用してクライアント Push SDK を組み込みます。
	1. [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) ファイルを構成します。 
	2. [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) ファイルを構成します。
	3. `google-services.json` ファイルを Android アプリケーション・モジュールのルート・ディレクトリーに追加します。
5. SDK を初期化します。[コア SDK および Push SDK の初期化](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk)を参照してください。
6. アプリケーションをビルドします。
7. アプリケーションの「デバイスの登録」ボタンをクリックするか、[Push Android SDK を使用したサービスへの登録](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice)によって、Push Notifications サービスに登録することを選択できます。

次のステップは、[通知の送信](push_step_4.html)です。


## Cordova アプリケーションの場合
{: #push_step_3_Cordova}

Cordova は、JavaScript、CSS、および HTML を使用したハイブリッド・アプリケーションの構築用プラットフォームです。
Push Notifications サービスは、Cordova ベースの iOS アプリケーションおよび Android アプリケーションの開発をサポートします。

Cordova アプリケーションがデバイスへのプッシュ通知を受信できるようにするには、[Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app) を構成する必要があります。

Cordova Plugin Push SDK をセットアップした後、次のステップは、[通知の送信](push_step_4.html)を行うことです。


## iOS アプリケーションの場合
{: #push_step_3_iOS}

iOS アプリケーションがデバイスへの {{site.data.keyword.mobilepushshort}} を受信できるようにするには、[Push Notifications サービス用の iOS SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application) を構成する必要があります。 

iOS SDK をセットアップした後、次のステップは、[通知の送信](push_step_4.html)を行うことです。


## Web ブラウザーの場合
{: #push_step_3_web}

ブラウザー・アプリケーションがプッシュ通知を受信できるようにするには、[Push Notifications サービス用の Web SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md) を構成する必要があります。

Web SDK をセットアップした後、次のステップは、[通知の送信](push_step_4.html)を行うことです。
