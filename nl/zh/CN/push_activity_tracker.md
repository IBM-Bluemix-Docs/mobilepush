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

{{site.data.keyword.cloudaccesstrailfull}} 服务监视用户与 IBM Cloud 服务的交互。您可以搜索和分析用户和应用程序如何与 IBM Cloud 服务交互。

云管理员、安全员和开发人员可以：

<dl>
	<dt>获取针对环境的洞察以监视和调查安全违规</dt>
	<dd>捕获用户和应用程序与您的已供应 IBM Cloud 资源的交互。调查可能的安全违规或未经授权的访问。</dd>
	<dt>实现监管、合规性和记录保留需要</dt>
	<dd>将捕获的事件存储所需的任意长时间，并通过云类经济型存储解决方案进行保护。通过 API 查询收集到的事件数据或导出您的云活动数据。</dd>
	<dt>DevOps 团队调试和执行容量规划时的云透明度</dt>
	<dd>云活动事件为您在 IBM Cloud 上的 IT 运营提供透明度。识别云服务何时以及如何用于隔离和调试应用程序。查询随时间推移而收集的数据，以预测云增长和季节性需求。</dd>
	<dt>简化收集和提高云安全性</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}} 自动捕获 IBM Cloud 事件。</dd>
</dl>


{{site.data.keyword.cloudaccesstrailshort}} 活动日志可用于识别以下信息：

- 对云服务发起 API 调用的用户。
- 发起 API 调用的源 IP 地址。
- 发起 API 调用时的时间戳记。
- API 调用的状态。

## 事件列表
{: #actions}

下表列出 {{site.data.keyword.mobilepushshort}} 的 {{site.data.keyword.cloudaccesstrailshort}} 事件
<table>
  <caption>表 1. 生成事件的操作的列表</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>应用程序更新</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>应用程序配置删除</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>应用程序配置更新</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>标记创建</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>标记删除</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>标记更新</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Webhook 创建</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Webhook 删除</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Webhook 更新</td>
  </tr>   
</table>


有关使用 {{site.data.keyword.cloudaccesstrailshort}} 的更多信息，请参阅
[此处的文档](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}。


当前，Activity Tracker 事件仅可用于 `IBM Cloud - 美国南部地区`。
{: note}
