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

# Activity Tracker 事件
{: #push_activity_tracker}

{{site.data.keyword.cloudaccesstrailfull}} 服務監視使用者與 IBM Cloud 服務的互動。您可以搜尋和分析使用者和應用程式如何與 IBM Cloud 服務互動。

雲端管理者、安全人員和開發人員可以：

<dl>
	<dt>獲取針對環境的洞察以監視和調查安全中斷</dt>
	<dd>擷取使用者和應用程式與您的已佈建 IBM Cloud 資源的互動。調查可能的安全中斷或未獲授權的存取。</dd>
	<dt>達到法律、法規遵循和記錄保留的需要</dt>
	<dd>只要您需要，就可以儲存擷取的事件，並透過雲端類別經濟型儲存空間解決方案進行保護。透過 API 查詢收集到的事件資料或匯出您的雲端活動資料。</dd>
	<dt>DevOps 團隊的雲端透通性用來除錯和執行產能規劃</dt>
	<dd>雲端活動事件可讓您在 IBM Cloud 上的 IT 作業透明化。識別雲端服務何時以及如何用於隔離和除錯應用程式。查詢隨時間推移而收集的資料，以預測雲端成長和季節性需求。</dd>
	<dt>簡化收集和提高雲端安全</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}} 自動擷取 IBM Cloud 事件。</dd>
</dl>


{{site.data.keyword.cloudaccesstrailshort}} 活動日誌可用於識別下列資訊：

- 對雲端服務進行 API 呼叫的使用者。
- 進行 API 呼叫的來源 IP 位址。
- 進行 API 呼叫時的時間戳記。
- API 呼叫的狀態。

## 事件清單
{: #actions}

下表格列出 {{site.data.keyword.mobilepushshort}} 的 {{site.data.keyword.cloudaccesstrailshort}} 事件
<table>
  <caption>表 1. 產生事件的動作的清單</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>應用程式更新</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>應用程式配置刪除</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>應用程式配置更新</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>標籤建立</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>標籤刪除</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>標籤更新</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Webhook 建立</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Webhook 刪除</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Webhook 更新</td>
  </tr>   
</table>


如需使用 {{site.data.keyword.cloudaccesstrailshort}} 的相關資訊，請參閱
[這裡的文件](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}。


目前，Activity Tracker 事件僅可用於 `IBM Cloud - 美國南部地區`。
{: note}
