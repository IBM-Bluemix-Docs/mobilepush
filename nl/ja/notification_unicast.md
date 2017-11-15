---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# ユニキャスト通知
{: #notification_unicast}


ユニキャスト通知は、特定のデバイスまたはユーザーをターゲットとするメッセージです。デバイスをターゲットとするユニキャスト通知は、追加のセットアップを必要とせず、アプリケーションが {{site.data.keyword.mobilepushshort}} に対応していればデフォルトで有効になります。

ただし、ユーザーをターゲットとするユニキャスト通知では、{{site.data.keyword.mobilepushshort}} 用のクライアント・モバイル・デバイスまたは Web ブラウザー、あるいは Chrome アプリケーションおよびエクステンションの登録時に、ユーザー ID をデバイスと関連付ける必要があります。   

通常、クライアント・アプリケーションは、最初に認証サイクルを実行します。この認証サイクルで、モバイル・アプリケーション・ユーザーは [Mobile Client Access](docs/services/mobileaccess/index.html) などの認証サービスと照合して認証されます。認証に成功すると、認証済みユーザー ID がプッシュ・デバイス登録 API に渡されます。 

REST API を使用するユニキャスト通知を送信する場合は、メッセージ・リソースに投稿する際に deviceId または userId が指定されていることを確認してください。
