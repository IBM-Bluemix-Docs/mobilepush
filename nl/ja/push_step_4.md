---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# ステップ 5: 通知の送信
{: #push_step_4}
最終更新日; 2017 年 6 月 27 日
{: .last-updated}


アプリケーションの開発が完了したら、基本プッシュ通知を送信できます。

基本プッシュ通知を送信するには、以下の手順を実行します。

1. **「通知の送信 (Send Notifications)」**を選択し、**「送信先 (Send To)」**オプションを選択することでメッセージを構成します。サポートされるオプションは、**「タグ指定によるデバイス (Device by Tag)」**、**「デバイス ID (Device Id)」**、**「ユーザー ID」**、**「Android デバイス (Android devices)」**、**「iOS デバイス (iOS devices)」**、**「Web 通知 (Web Notifications)」**、および**「すべてのデバイス」**です。
**注**: **「すべてのデバイス」**オプションを選択すると、{{site.data.keyword.mobilepushshort}}をサブスクライブしているすべてのデバイスが通知を受け取ることになります。
	
	![「通知」画面](images/tag_notification.jpg)

2. **「メッセージ」**フィールドで、メッセージを構成します。必要に応じてオプションの設定を構成してください。
3. **「送信」**をクリックします。
3. デバイスまたはブラウザーが通知を受信したことを確認します。

次のスクリーン・ショットは、Android デバイスのフォアグラウンドでプッシュ通知を処理しているアラート・ボックスを示しています。
	![Android のフォアグラウンドでのプッシュ通知](images/Android_Screenshot.jpg)

次のスクリーン・ショットは、Android のバックグラウンドでのプッシュ通知を示しています。
	![Android のバックグラウンドでのプッシュ通知](images/background.jpg)

## オプションの Android 設定 
{: #push_step_4_Android}

Android デバイスに通知を送信するための{{site.data.keyword.mobilepushshort}}設定をさらに詳細にカスタマイズできます。 

![Android カスタム設定](images/android_custom_settings.jpg)

以下の任意指定のカスタマイズ・オプションがサポートされます。

- 省略キー (Collapse Key): 省略キーは通知にアタッチされます。デバイスがオフラインのときに、同じ省略キーを持つ複数の通知が連続して到着すると、それらは省略されます。デバイスがオンラインになると、FCM/GCM サーバーから通知を受け取り、同じ省略キーを持つ最新の通知のみを表示します。省略キーが設定されていない場合、新しいメッセージと古いメッセージの両方が将来の配信のために保管されます。
- 音 (Sound): 通知の受信時に音声クリップを再生するかどうかを示します。デフォルト、またはアプリにバンドルされている音声リソースの名前がサポートされます。
- アイコン (Icon): 通知用に表示するアイコンの名前を指定します。クライアント・アプリケーションと一緒に、アイコンを `res/drawable` フォルダーにパッケージしてあることを確認してください。
- 優先度 (Priority): メッセージに配信の優先度を割り当てるためのオプションを指定します。 
	- 優先度を `high` または `max` にすると、警告通知になります。
	- 優先度を `low` または `default` にすると、スリープ状態のデバイスではネットワーク接続はオープンされなくなります。 
- 可視性 (Visibility): 通知の可視性オプションは `public` または `private` のいずれかに設定できます。 
	- `private` オプションにすると、公開表示は制限されます。デバイスが PIN またはパターンによって保護されており、通知設定が**「プライベートな通知内容を非表示にする (Hide sensitive notification content)」**に設定されている場合は、公開表示を有効にするように選択できます。可視性を `private` に設定する場合は、`redact` フィールドの指定が必要です。`redact` フィールドに指定された内容のみが、保護されてロックされているデバイスの画面に表示されます。 
	- `public` オプションにすると、通知は自由に読み取りされる状態になります。
- 存続時間: この値は秒単位で設定します。このパラメーターを指定しないと、FCM/GCM サーバーはメッセージを 4 週間保管し、配信を試行します。4 週間が経過すると、有効期限が切れます。可能な値の範囲は、0 から 2,419,200 秒です。
- アイドル時は遅延 (Delay when idle): これは次のいずれかの値に設定できます。
	- `True` は、デバイスがアイドル状態の場合は通知を配信しないように FCM/GCM サーバーに指示します。 
	- `False` は、デバイスがアイドル状態であっても通知が配信されるようにします。
- 同期: このオプションを `true` に設定すると、ユーザーのすべての登録済みデバイス間で通知が同期化されます。あるユーザー名を持つユーザーが、同じアプリケーションがインストールされている複数のデバイスを所持している場合、1 台のデバイスで通知を読むと、その他のデバイスの通知は削除されます。
このオプションが機能するためには、ユーザーが userId を指定して
{{site.data.keyword.mobilepushshort}}サービスに登録されていることを確認する必要があります。
- 追加のペイロード (Additional payload): 通知用のカスタム・ペイロードの値を指定します。
- 拡張可能な通知 (Expandable notification): これは、より詳しい情報を含むよう通知を拡張するが、通知を縮小すれば基本的な通知を表示することもできるというオプションをお客様に提供します。次のオプションがサポートされています。
	- Big Picture Notifications: 通知が拡張されたときに画像を組み込むことを選択できます。タイトル・テキストと、画像の URL を提供する必要があります。
	- Big Text Notifications: 追加テキストおよびタイトルを組み込むことを選択できます。Big Text メッセージおよびタイトル・テキスト情報を提供する必要があります。
	- Inbox Style Notifications: インボックス通知のスタイルで通知を送信できます。タイトル・テキストと複数行のメッセージを提供する必要があります。	 

## オプションの iOS 設定 
{: #push_step_4_ios}

iOS デバイスに通知を送信するための {{site.data.keyword.mobilepushshort}} 設定をカスタマイズできます。以下の任意指定のカスタマイズ・オプションがサポートされます。

- **バッジ**: アプリケーション・バッジに表示される数値を示します。デフォルト値はゼロ (0) で、この場合、バッジは表示されません。 
- **音 (Sound)**: 通知の受信時に音声クリップを再生するかどうかを示します。デフォルト、またはアプリにバンドルされている音声リソースの名前がサポートされます。
- **追加のペイロード (Additional payload)**: 通知用のカスタム・ペイロードの値を指定します。

[対話式通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications)および[リッチ・メディア通知](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications)を有効にすることを選択することもできます。

## 配信された通知のモニター 
{: #push_step_4_monitor}

{{site.data.keyword.mobilepushshort}} サービスは、送信されるメッセージの状況の検査に役立つモニタリング・ユーティリティーを提供します。モニター・ユーティリティーを構成するには、以下のいずれかのオプションを実行してください。

- [Android アプリケーションでのモニターの有効化](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
- [iOS アプリケーションでのモニターの有効化](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
