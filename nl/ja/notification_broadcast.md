---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# ブロードキャスト通知 
{: #broadcast_notifications}

ブロードキャスト通知は、モバイル・デバイスおよびブラウザーの全体にインストールされているか Chrome アプリケーションまたはエクステンションとして実装されていて、かつ {{site.data.keyword.mobilepushshort}} サービス用に構成されている、1 つのアプリケーションのすべてのインスタンスをターゲットとしたメッセージです。 ブロードキャスト通知は、{{site.data.keyword.mobilepushshort}}が有効になっているすべてのアプリケーションに、デフォルトで有効になっています。

クライアント・アプリケーションは、{{site.data.keyword.mobilepushshort}} サービスに自身を登録すると、ブロードキャストの受信を開始できます。 {{site.data.keyword.mobilepushshort}}サービスが有効になっているアプリケーションでは、Push.ALL タグへのサブスクリプションが事前定義されています。サーバーはこれを使用して、通知メッセージをすべてのデバイスにブロードキャストします。 REST Push API を使用するブロードキャスト通知を送信する場合は、メッセージ・リソースに投稿する際に「target」が空の JSON ファイルであることを確認してください。
