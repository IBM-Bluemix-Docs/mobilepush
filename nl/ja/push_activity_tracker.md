---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Activity Tracker のイベント
{: #push_activity_tracker}

{{site.data.keyword.cloudaccesstrailfull}} サービスは、IBM Cloud サービスとのユーザーの対話をモニターします。ユーザーやアプリケーションが IBM Cloud サービスとどのように対話しているかを検索して分析することができます。

クラウド管理者、セキュリティー担当者と開発者は以下のことが可能です。

<dl>
	<dt>ご使用環境の状況を把握してセキュリティー・ブリーチをモニターおよび調査する</dt>
	<dd>プロビジョンされた IBM クラウド・リソースとのユーザーやアプリケーションの対話をキャプチャーします。セキュリティー・ブリーチや無許可アクセスの危険性を調査します。</dd>
	<dt>規制、コンプライアンス、およびレコード保存のニーズを達成する</dt>
	<dd>収集したイベントを必要な期間だけ保管し、クラウド・クラスの経済的なストレージ・ソリューションで保護します。収集されたイベント・データを API 経由で照会したり、クラウド・アクティビティー・データをエクスポートしたりします。</dd>
	<dt>DevOps チームがデバッグおよびキャパシティー・プランニングを実行するためのクラウドの透明性</dt>
	<dd>クラウド・アクティビティー・イベントは、IBM Cloud での IT 運用に透明性をもたらします。アプリケーションの切り分けとデバッグのために、いつどのようにクラウド・サービスが使用されたかを特定します。クラウドの拡大と周期的なニーズを予測するために、収集されたデータを長期間にわたって照会します。</dd>
	<dt>収集を簡素化してクラウドのセキュリティーを向上させる</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}} が IBM Cloud のイベントを自動的にキャプチャーします。</dd>
</dl>


{{site.data.keyword.cloudaccesstrailshort}} のアクティビティー・ログを使用すると、以下の情報を特定できます。

- クラウド・サービスに対して API 呼び出しを行ったユーザー。
- API 呼び出しが行われたソース IP アドレス。
- API 呼び出しが行われたタイム・スタンプ。
- API 呼び出しの状況。

## イベント・リスト
{: #actions}

以下の表は、{{site.data.keyword.mobilepushshort}} の {{site.data.keyword.cloudaccesstrailshort}} イベントをリストします。
<table>
  <caption>表 1. イベントを生成するアクションのリスト</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>アプリケーションの更新</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>アプリケーション構成の削除</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>アプリケーション構成の更新</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>タグの作成</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>タグの削除</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>タグの更新</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Web フックの作成</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Web フックの削除</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Web フックの更新</td>
  </tr>   
</table>


{{site.data.keyword.cloudaccesstrailshort}} での作業について詳しくは、[こちらの資料](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}を参照してください。


現時点で、Activity Tracker イベントは、`IBM Cloud - 米国南部地域`でのみ使用可能です。
{: note}
