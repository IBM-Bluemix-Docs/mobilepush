---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notification, security, appsecret, api keys

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Push Notifications 的安全性 
{: #security-in-push-notifications}

{{site.data.keyword.mobilepushshort}} API 以通过以下方式进行保护：

- **appSecret**：`appSecret` 会保护通常由后端应用程序调用的 API，如用于发送 {{site.data.keyword.mobilepushshort}} 的 API 和用于配置设置的 API。
- **clientSecret**：`clientSecret` 会保护通常由移动客户机应用程序调用的 API。只有一个 API 与设备注册相关，且其相关联用户标识需要此 `clientSecret`。从移动客户机调用的其他 API 都不需要 `clientSecret`。 
- **API 密钥**：应用程序编程接口密钥（API 密钥）通过 Cloud IAM 可用，供您使用 API 或 CLI 以用户或服务标识身份进行认证。这些 API 密钥是通过 Cloud IAM 提供的，因此通常无法用于在 IBM Cloud 之外使用 IBM 标识进行认证。 

在将应用程序与 {{site.data.keyword.mobilepushshort}} 服务绑定在一起时，会为每个服务实例分配 `appSecret` 和 `clientSecret`。请参阅 [REST API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://eu-gb.imfpush.cloud.ibm.com/imfpush/) 文档，以获取如何传递私钥以及相关联的 API 的更多信息。

## appSecret 
{: #push-api-rest-secret}

应用程序绑定到 {{site.data.keyword.mobilepushshort}} 后，该服务会生成一个 appSecret（唯一密钥），并会在响应头中传递该密钥。如果是使用 IBM {{site.data.keyword.mobilepushshort}} for IBM Cloud Rest API，请参阅 REST API 参考来获取有关需要保护哪些 API 的信息。有关更多信息，请参阅 [Push REST API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: new_window}。

请求头必须包含 appSecret。如果不包含，服务器会返回“401 未授权”错误代码。将 {{site.data.keyword.mobilepushshort}} 添加到应用程序时，会创建特定的 AppID。作为响应的一部分，您会获取名为 appSecret 的头，其用于创建标记或发送消息。通过目录或样板中的服务，可执行该操作。

要获取 appSecret 值，请执行以下操作：

1. 单击绑定到 Push 服务的 *app-name*。
2. 单击**显示凭证**链接以显示 appSecret (AppID)。

**显示凭证**屏幕将显示有关 appSecret 的信息：
```
	{
    "imfpush_Dev": [
   {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://https://eu-gb.imfpush.cloud.ibm.com/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.cloud.ibm.com/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**注**：仅在使用用户标识字段注册或更新设备时需要较早版本的应用程序来传递 clientSecret。移动和浏览器客户机调用的所有其他 API 不
需要 clientSecret。这些旧应用程序可以选择针对设备注册或更新调用继续使用 clientSecret。但是，强烈建议对所有客户机 API 调用强制执行 clientSecret 检查。为了在现有应用程序中强制执行此检查，已发布了一个新的 `verifyClientSecret` API。对于新的应用程序，将对所有客户机 API 调用强制执行 clientSecret 检查，而此行为无法使用 `verifyClientSecret` API 进行更改。

缺省情况下，客户机密钥验证仅在新应用程序中强制执行。允许现有的和新的应用程序使用 verifyClientSecret REST API 启用或停用客户机密钥验证。建议您强制执行客户机密钥验证，以避免向可能了解 applicationId 和 deviceId 的用户公开设备。

确保秘密保存 `clientSecret`，绝不要将其硬编码到移动应用程序中。可以使用多种应用程序初始化模式，在应用程序运行时期间，动态地拉入 `clientSecret`。时序图概述了此类可能的模式。
![启用推送](images/init_client_secret.jpg "显示拉入 clientSecret 的初始化模式的时序图") 

## 用于用户认证的 API 密钥
{: #push-api-key}

API 密钥是传入 API 的唯一代码，用于标识调用应用程序或用户。API 密钥用于跟踪和控制 API 的使用情况，例如阻止恶意使用或滥用 API。API 密钥经常充当进行认证的唯一标识和私钥令牌，而且通常有一组特定于其关联身份的访问权。

请参阅[此处](https://cloud.ibm.com/docs/iam?topic=iam-manapikey)以获取有关管理和使用 API 密钥的更多详细信息。

