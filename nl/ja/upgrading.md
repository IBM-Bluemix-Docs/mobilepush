---

copyright:
  years: 2015, 2017, 2018, 2019
lastupdated: "2019-06-11"

keywords: push notifications, notifications, upgrading plan, lite, basic, advanced

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}


# プランのアップグレード
{: #upgrade-push}

{{site.data.keyword.mobilepushshort}} サービスでは、お客様のニーズに合わせて異なるレベルのリソースと機能を提供する 3 つのプランをご用意しています。
{: shortdesc}

## 価格設定プラン
{: #pricing-plan}

**注:**
 - 固有のデバイス/エンドポイントや Webhook イベントに送信されるプッシュ通知が 1 つのデジタル・メッセージを構成します。 
 - 「アドレス可能デバイス」とは、「クラウド・サービス」によりアドレス指定可能なアプリケーションがインストールされるデバイスです。
 - ライト・プラン・サービスは、非アクティブで 30 日経過すると削除されます。

|                |ライト                           |基本                        |アドバンスト                      |
|----------------|-------------------------------|-----------------------------|------------------------------|
|**機能**    |1 カ月当たり 100,000 デジタル・メッセージ、50 アドレス指定可能デバイス |最初の 100 万デジタル・メッセージおよび 10000 のアドレス指定可能デバイスは無料            |インスタンスあたりの料金 </br> 1 億デジタル・メッセージおよび 100 万アドレス指定可能デバイスを含む<br/> 高度な機能<br/> - [メッセージのパラメーター化](/docs/services/mobilepush?topic=mobile-pushnotification-template_based_notifications)<br/> - [エンドツーエンドのメッセージ・ライフサイクル・トラッキング](/docs/services/mobilepush?topic=mobile-pushnotification-message-delivery-status)<br/>|
|**料金**     |無料|- $1.00 / 1 万アドレス指定可能デバイス <br/> - $1.00 / 100 万デジタル・メッセージ <br /> |- $100.00 / インスタンス <br/> - $0.50 / 100 万デジタル・メッセージ <br/> - $0.50 / 100 万アドレス指定可能デバイス <br/> |-|
{:caption="表 1. サービス・プラン" caption-side="top"}


## サービスのアップグレード
{: #upgrading-a-service}

プランをアップグレードするには、以下の手順を実行します。

1.  {{site.data.keyword.Bluemix_notm}} メニューから、**「サービス」** > **「ダッシュボード」**を選択します。
2.  アップグレードするサービス・インスタンスを選択して開きます。
3.  ナビゲーション・ペインで**「プラン」**をクリックします。
   ここで、現在のプランと他の使用可能なプランのオプションを確認し、変更を行うことができます。

コストの計算については、[{{site.data.keyword.Bluemix_notm}}料金カリキュレーター ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/estimator){: new_window} を参照してください。
