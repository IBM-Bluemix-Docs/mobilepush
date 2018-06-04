---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# ユーザー・ベースの通知
{: #user_based_notifications}
最終更新日: 2017 年 5 月 22 日
{: .last-updated}

ユーザー ID ベースの{{site.data.keyword.mobilepushshort}}は、カスタマイズしたメッセージを使用し、モバイル・アプリ・ユーザーをターゲットとします。 ユーザー・ベースの通知では、通知設定に基づいて特定の個人に通知するように選択できます。

## ユーザー ID を使用したデバイスの登録
{: #register_device_wh_userid}

ユーザー ID によってターゲット指定されるプッシュ通知を有効にするには、必ず、「ユーザー ID」フィールドを設定した状態でデバイスを登録してください。     

ユーザー ID には、アプリケーションがデバイス登録 API に提供する任意のストリングが可能です。 通常、モバイル・アプリケーションはまず、[{{site.data.keyword.amafull}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/docs/services/mobileaccess/index.html){: new_window}などの認証サービスに対してモバイル・アプリ・ユーザーを認証する認証サイクルを実行します。 認証に成功すると、認証済みユーザー ID がプッシュ・デバイス登録 API に渡されます。 

ユーザー ID ベースの通知のための登録を行うには、以下を参照してください。

- [Android アプリケーションの登録](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [iOS アプリケーションの登録](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Cordova アプリケーションの登録](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Web アプリケーションの登録](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## userId ベースの通知の使用
{: #using_userid}

userId ベースの通知は、特定のユーザーをターゲットとする通知メッセージです。 1 つのユーザーで複数のデバイスを登録できます。 以下の手順では、ユーザー ID ベースの通知の送信方法を説明します。

1. **Push Notification** コンソールで、**「通知の送信」**オプションを選択します。
1. **「送信先 (Send to)」**リストのオプションで**「UserId」**を選択します。
1. **「ユーザー ID」**フィールドで、使用するユーザー ID を検索し、**「+ 追加 (+Add)」**をクリックします。![「通知」画面](images/user_notification.jpg)
1. **「メッセージ」**フィールドに、通知で送信するテキストを入力します。
1. **「送信」**をクリックします。


## ユーザーのログインおよびログアウトの同期化 
{: #sync_login_logout}

ユーザーがログインしている場合にのみ通知を送信するようにすることができます。 

例えば、1 つのデバイスを職場のチームのメンバーで共有していて、特定のユーザーに対応する必要がある場合を考えてください。 そのようなユース・ケースでは、ユーザー・ログイン/ログアウト・シーケンスを使用できます。 この認証メカニズムを使用すると、アプリケーションが、アプリケーションの現在のユーザーの ID を追跡できるようになります。 これにより、特定のユーザーをターゲットとした通知は、常にそのユーザーのみが受信するようにできます。 正常なログインの後、ログイン・ユーザーのユーザー ID を渡すデバイス登録 API を呼び出します。 ログアウトの前にも同様に、デバイス `unregistration` API を呼び出します。 これらのプッシュ API を、ログインおよびログアウトと共にシーケンスにすると、特定のユーザー向けの通知がそのユーザーだけに送信されるようになります。
