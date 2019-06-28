---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-24"

keywords: push notifications, notifications, compliance, hipaa, iso, soc 2 type 1 certification, gdpr

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# コンプライアンス
{: #compliance}

IBM Cloud {{site.data.keyword.mobilepushshort}} サービスは、登録されたモバイル・デバイスに通知を送信する場合の信頼できるセキュアな方法を提供します。
{: shortdesc}

## HIPAA
{: #hipaa}

IBM {{site.data.keyword.mobilepushshort}} サービスは、1996 年の医療保険の積算と責任に関する法律 (HIPAA) のセキュリティー・ルールおよびプライバシー・ルールの条件に見合った、必要な IBM コントロールを満たしています。この {{site.data.keyword.mobilepushshort}} サービスは、データを暗号化形式で保存し、暗号化されたデータを転送します。

IBM Cloud {{site.data.keyword.mobilepushshort}} サービスを使用して HIPAA で規制された情報を送信する場合は、Post/message API を使用しないでください。サード・パーティーのプッシュ・プロバイダーを介して送信されるペイロードが、規制のガイドラインを満たさない場合があるためです。その代わりに以下の手順を使用すると、メッセージ ID のみがサード・パーティーのプッシュ・プロバイダーを介して送信される一方で、実際の機密データは安全な (https) 転送経由でクライアント・アプリケーションによってダウンロードすることができます。

1. 新規インスタンスのアドバンスト・プランをプロビジョンするか、既存のインスタンスをアドバンスト・プランにアップグレードします。
2. {{site.data.keyword.mobilepushshort}} サービスを使用して[サイレント通知](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios)を送信します。
3. {{site.data.keyword.mobilepushshort}} サービスは、FCM や APNS などのプッシュ・クラウド・プロバイダーを使用して通知を送信します。サイレント通知の特性によって、アラートは通知の一部として送信されません。
4. 送信された ``message id`` / ``nid`` の通知をデバイスが受け取ると、アプリケーションは {{site.data.keyword.mobilepushshort}} サービスを呼び出して、``GET /message/{messageId}`` を使用してアラート通知を受け取ります。

こうすることで、IBM Cloud {{site.data.keyword.mobilepushshort}} サービスを使用した、セキュア・チャネル経由での機密性の高いテキスト・コンテンツの送信が可能になります。

IBM には APNS/FCM との Business Associate Agreements (BAA) 関係がありません。
{: note}
## 国際標準化機構 (ISO)
{: #iso}

{{site.data.keyword.mobilepushshort}} Service は、サード・パーティーのセキュリティー会社によって監査されており、以下の ISO 条件を満たしています。

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [すべての IBM ISO 証明書の検索![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}。
 
## SOC 2 タイプ 1 認定
{: #soccert}

{{site.data.keyword.IBM_notm}} は、{{site.data.keyword.mobilepushshort}} Service の Service Organization Controls (SOC) 2 タイプ 1 の報告書を提供します。 この報告書は、米国公認会計士協会 (AICPA) Trust サービスの原則により設定されている基準にしたがって IBM の運用管理を評価します。
Trust サービスの原則は、IBM Cloud などのサービス・プロバイダーがその顧客のデータと情報を保護するために、適切な制御システムを定義するものであり、業界標準を制定しています。

SOC 2 タイプ 1 の報告書は、カスタマー・ポータルから要求するか、営業担当員にお問い合わせください。 または、[IBM Cloud サポート![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/support){: new_window} でサポート・チケットをオープンすることができます。

## 一般データ保護規則 (GDPR) 
{: #gdpr}

GDPR は、EU 全域における統一されたデータ保護の法的枠組みを作成しようというものであり、個人データの管理権限を市民の手に取り戻すことを目的とし、世界のどこであろうと個人データをホスティングおよび「処理」するものに対して厳格な規則を課します。また、この規則では、EU 域内と域外における個人データの自由な移動に関するルールが導入されます。 

[一般データ保護規則 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.eugdpr.org/){: new_window} により、{{site.data.keyword.mobilepushshort}} サービスのお客様は、
新たなデータ・プライバシー規格および法律に対する {{site.data.keyword.mobilepushshort}} サービス・チームの理解とコンプライアンスを信頼していただくことができ、さらに、独自の内部データ・ガバナンス要件を持つさまざまな規模のビジネスを支援するために {{site.data.keyword.IBM}} が提供する包括的なソリューション・スイートで安心してご利用いただけます。
