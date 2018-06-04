---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# プラットフォーム・ベースの通知
{: #notification_platform}


特定のデバイス・プラットフォームに届くように通知のターゲットを設定することができます。 例えば、すべての Android ユーザーまたは Google Chrome ユーザーにのみ通知を送信するようにできます。 REST API を使用するプラットフォーム・ベースの通知を送信する場合には、メッセージ・リソースに投稿する際にターゲットのプラットフォームが指定されていることを確認してください。 プラットフォームを配列として指定します。 サポートされるプラットフォームは、以下のとおりです。

* A (Apple)
* G (Google)
* WEB_CHROME (Google Chrome ブラウザーの Web プッシュ)
* WEB_FIREFOX (Mozilla Firefox ブラウザーの Web プッシュ)
* WEB_SAFARI (Safari ブラウザーの Web プッシュ)
* APPEXT_CHROME (Google Chrome アプリケーション & エクステンション)
