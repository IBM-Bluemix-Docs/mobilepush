---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, tag-based, creating tags, managing tags, get tag, subscribe tag

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# タグ・ベースの通知
{: #tag_based_notifications}

タグ・ベースの通知は、特定のタグにサブスクライブしているすべてのデバイスをターゲットとするメッセージです。 タグ・ベースの通知では、サブジェクト・エリアまたはトピックに基づいて通知を分割できます。 通知の受信側は、関心のあるサブジェクトまたはトピックに関するものであった場合にのみ通知を受信するように選択できます。 そのため、タグ・ベースの通知は、受信側を分割する手段を提供します。 この機能により、タグを定義した後、タグ別にメッセージの送受信を行うことが可能になります。 メッセージは、タグにサブスクライブしている (モバイル上、ブラウザー上、あるいはアプリケーションまたはエクステンションとしての) クライアント・アプリケーション・インスタンスのみをターゲットにします。 まず、アプリケーションのタグを作成し、タグ・サブスクリプションをセットアップしてから、タグ・ベースの通知を開始する必要があります。 REST API を使用するタグ・ベースの通知を送信する場合は、メッセージ・リソースに投稿する際に「tagNames」が指定されていることを確認してください。

タグを定義して、タグを使用したメッセージの送受信を行うことが可能です。 最初にアプリケーションのタグを作成し、サブスクリプションを作成し、次にタグ・ベースの通知を開始する必要があります。 [REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: new_window} を使用してタグ・ベースの通知を送信する場合には、メッセージ・リソースにポストする際に「tagNames」が指定されていることを確認してください。


## タグの管理
{: #manage_tags}

{{site.data.keyword.mobilepushshort}} コンソールを使用して、アプリケーション向けのタグを作成および削除し、タグ・ベースの通知を開始します。 タグ・ベースの通知は、タグにサブスクライブしているデバイスが受け取ります。


### タグの作成
{: #create_tags}

タグ・ベースの通知は、特定のタグにサブスクライブしているすべてのデバイスをターゲットとするメッセージです。 各デバイスは、任意の数のタグにサブスクライブできます。 

1. {{site.data.keyword.mobilepushshort}} コンソールで、**「タグの管理」**タブを選択します。
1. **「+ タグを作成 (+ Create Tag)」**ボタンをクリックします。   
   1. **「名前」**フィールドで、タグの名前を入力します。 例えば、「クーポン」と入力します。
   1. **「説明」**フィールドで、タグの説明を入力します。
   1. **「保存」**をクリックします。

1. **「コード・スニペット (Code Snippets)」**エリアで、ご使用のモバイル・アプリケーションのプラットフォームを選択します。
1. エラー処理をするコード・スニペットを変更し、各タグに対するコード・スニペットをご使用のモバイル・アプリケーションにコピーします。

### タグの削除
{: #delete_tags}

1. **「タグ」**タブで、削除するタグを選択し**「削除」**アイコンをクリックします。
1. **「OK」**をクリックします。

タグが削除されると、そのタグに関連付けられている情報 (サブスクライバーやデバイスなど) が削除されます。 タグが存在しなくなることから、自動アンサブスクライブは不要です。 クライアント・サイドではそれ以上のアクションは不要です。

### タグの説明の編集
{: #edit_tags}

1. **「タグ」**タブで、編集するタグを選択します。
1. **「編集」**アイコンをクリックします。
1. タグの説明を編集し、**「保存」**ボタンをクリックします。

## タグの取得
{: #get_tags}

タグは、ユーザーの関心に基づいてターゲットを絞った通知をユーザーに送信する手段となります。この点は、すべてのアプリケーションに送信される一般ブロードキャストと異なります。 タグの作成および管理は、{{site.data.keyword.mobilepushshort}} コンソールの「タグ」タブを使用するか、REST API を使用して実行できます。 コード・スニペットを使用して、モバイル・アプリケーションのタグ・サブスクリプションを管理および照会できます。 コード・スニペットを使用して、サブスクリプションの取得、タグへのサブスクライブ、タグからのアンサブスクライブ、または使用可能なタグのリストの取得を行うことができます。 以下のコード・スニペットをモバイル・アプリケーションにコピーしてください。


- Android の場合、[Android での Push Notification によるタグの取得](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)に関する資料で `getTags` API および `getSubscriptions` API を参照してください。

- Cordova の場合、[Cordovaでの Push Notifications によるタグの取得](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags)に関する資料で `retrieveAvailableTags()` API および `retrieveSubscriptions()` API を参照してください。

- iOS の場合、[Swift での Push Notifications によるタグの取得](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags)に関する資料で `retrieveAvailableTagsWithCompletionHandler` API を参照してください。

- Web ブラウザーの場合、[Webブラウザーでの Push Notifications によるタグの取得](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags)に関する資料で `retrieveAvailableTags()` API を参照してください。


## タグのサブスクライブ
{: #Subscribe_tags}

タグの取得、タグへのサブスクライブ、サブスクリプションの取得、タグからのアンサブスクライブをデバイスが行えるようにするには、以下の API を使用します。

- Android の場合、API `getTags`、`subscribe`、`getSubscriptions`、および `unsubscribeFromTags` を使用します。 [Push Notifications による Android でのタグのサブスクライブ](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags)に関する資料を参照してください。

- Cordova の場合、API `retrieveAvailableTags()`、`subscribe()`、`retrieveSubscriptions()`、および `unsubscribe()` を使用します。 [Push Notifications による Cordova でのタグのサブスクライブ](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags)に関する資料を参照してください。

- iOS の場合、API `retrieveAvailableTagsWithCompletionHandler`、`subscribeToTags`、`retrieveSubscriptionsWithCompletionHandler`、および `unsubscribeFromTags` を使用します。 [Push Notifications による Swift でのタグのサブスクライブ](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags)に関する資料を参照してください。

- Web ブラウザーの場合、API `retrieveAvailableTags()`、`subscribe()`、`retrieveSubscriptions()`、および `unSubscribe()` を使用します。 [Push Notifications による Web ブラウザーでのタグのサブスクライブ](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags)に関する資料を参照してください。

## タグ・ベースの通知の使用
{: #using_tags}

タグ・ベースの通知は、特定のタグにサブスクライブしているすべてのデバイスをターゲットとするメッセージです。 各デバイスは、任意の数のタグにサブスクライブできます。 このトピックでは、タグ・ベースの通知の送信方法を説明します。 サブスクリプションは、{{site.data.keyword.mobilepushshort}} サービス IBM Cloud インスタンスによって維持されます。 タグが削除されると、そのタグに関連付けられているすべての情報 (サブスクライバーやデバイスを含む) が削除されます。 このタグはもはや存在せず、クライアント・サイドから必要な追加アクションはないので、このタグの自動アンサブスクライブは必要ありません。

**「タグ」**画面でタグを作成します。 タグの作成方法については、[「タグの作成」](/docs/services/mobilepush?topic=mobile-pushnotification-tag_based_notifications#create_tags)を参照してください。

1. **Push Notification** コンソールで、**「メッセージ (Messages)」**をクリックします。
2. **「送信先 (Send To)」**ドロップダウン・リストで、**「タグ指定によるデバイス  (Device by Tag)」**オプションを選択します。
3. 使用するタグを検索し、それらのタグを選択します。![通知画面](images/tag_notification_new2.jpg "「メッセージ (Messages)」ナビゲーション・オプションが選択され、送信通知ページが示された Push Notifications コンソール。「送信先 (Send to)」フィールドは「タグ指定によるデバイス (Device by Tag)」に設定されています。")
4. **「メッセージ・テキスト」**フィールドに、サブスクライブした対象者に通知として送信されるテキストを入力します。
5. **「送信」**をクリックします。

