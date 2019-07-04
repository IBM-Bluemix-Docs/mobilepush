---

copyright:
  years:  2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, service access, manage, user roles

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# 管理服务访问权
{: #service-access-management}

使用 {{site.data.keyword.mobilepushshort}} 和 {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM)，帐户所有者可以管理您帐户中的用户访问权。
{: shortdesc}

作为帐户所有者，您可以在帐户内设置策略，以便为不同用户创建不同级别的访问权。例如，某些用户可以对一个实例具有**只读**访问权，而对另一个实例具有**写**访问权。您可以决定谁有权创建、更新和删除 {{site.data.keyword.mobilepushshort}} 的实例。

**注释：**由于 {{site.data.keyword.mobilepushshort}} 服务采用了 IAM，不会为新实例生成应用程序私钥。而是必须使用
[API 密钥](https://cloud.ibm.com/docs/iam?topic=iam-manapikey)。

## 用户角色
{: #roles}

访问策略的作用域基于用户的已分配角色。
{: shortdesc}

策略支持在不同级别授予访问权。部分选项包括：
<ul><ul>
  <li>对帐户中所有服务实例的访问权</li>
  <li>对帐户中个别服务实例的访问权</li>
  <li>对实例中特定资源的访问权</li>
  <li>对帐户中所有启用 IAM 的服务的访问权</li>
</ul></ul>

平台管理角色支持用户对平台级别的服务资源执行任务。例如，可以分配角色以确定谁可以创建或删除标识、创建实例以及将实例绑定到应用程序。下表详细描述了与平台管理角色相关的操作。

<table>
  <tr>
    <th>平台角色</th>
    <th>许可权</th>
    <th>操作示例</th>
  </tr>
  <tr>
    <td><i>查看者</i></td>
    <td>查看 {{site.data.keyword.mobilepushshort}} 实例。</td>
    <td>您可以查看 Cloud Directory 用户数据或身份提供者配置。</td>
  </tr>
  <tr>
    <td><i>编辑者</i></td>
    <td>查看和绑定 {{site.data.keyword.mobilepushshort}} 实例。</td>
    <td>您可以将应用程序绑定到 {{site.data.keyword.mobilepushshort}} 的实例。</td>
  </tr>
  <tr>
    <td><i>操作员</i></td>
    <td>创建、删除、编辑、暂挂、恢复、查看或绑定 {{site.data.keyword.mobilepushshort}} 实例。</td>
    <td>您可以在目录中创建或删除 {{site.data.keyword.mobilepushshort}} 实例。</td>
  </tr>
  <tr>
    <td><i>管理员</i></td>
    <td>帐户中所有服务的所有管理操作。</td>
    <td>您可以执行所有操作员操作，并可以将策略分配给其他用户。</td>
  </tr>
</table>

</br>
</br>
下表详细描述了映射到服务访问角色的操作。服务访问角色支持用户访问 {{site.data.keyword.mobilepushshort}} 以及调用 {{site.data.keyword.mobilepushshort}} API。


<table>
  <tr>
    <th>服务角色</th>
    <th>许可权</th>
    <th>操作示例</th>
  </tr>
  <tr>
    <td><i>读取者</i></td>
    <td>查看 {{site.data.keyword.mobilepushshort}} 实例数据。</td>
    <td>可以查看服务实例的详细信息，例如用户数据或身份提供者信息。</td>
  </tr>
  <tr>
    <td> <i>写入者或管理者</i></td>
    <td>查看和更改 {{site.data.keyword.mobilepushshort}} 实例。</td>
    <td>可以执行所有读取者操作并编辑服务实例，例如编辑身份提供者配置。</li></ul></td>
  </tr>
</table>

有关在 UI 中分配用户角色的更多信息，请参阅[管理 IAM 访问权](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser)。


## {{site.data.keyword.mobilepushshort}} 访问策略
{: #access}

必须为帐户中访问 {{site.data.keyword.mobilepushshort}} 服务的每一个用户分配定义了 IAM 用户角色的访问策略。该策略确定用户可在您所选服务或实例的上下文中执行的操作。
{: shortdesc}

这些操作由 {{site.data.keyword.Bluemix_notm}} 服务定制和定义，作为允许在服务中执行的操作。然后，这些操作将映射到 IAM 用户角色。可使用 {{site.data.keyword.cloudaccesstrailshort}} 服务来跟踪所执行的某些操作。在下表中，{{site.data.keyword.mobilepushshort}} 的操作和必需的许可权一一对应。

|操作|说明 |所需角色|
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |获取应用程序设置 |管理者、写入者和读取者|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |删除应用程序设置 |管理者|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |更新应用程序设置|管理者|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |获取设备|管理者、写入者和读取者|
|`POST /imfpush/v1/apps/{applicationId}/devices` |注册设备|管理者和写入者|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |更新设备|管理者和写入者|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |删除设备|管理者|
|`POST /imfpush/v1/apps/{applicationId}/messages` |发送消息|管理者和写入者|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |发送批量消息|管理者和写入者|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |删除消息|管理者|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |获取消息|管理者、读取者和写入者|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |更新消息传递状态|管理者和写入者|
|`POST /imfpush/v1/apps/{applicationId}/tags` |创建标记|管理者和写入者|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |更新标记|管理者和写入者|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |删除标记|管理者|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |获取标记|管理者、读取者和写入者|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |创建预订|管理者和写入者|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |删除预订|管理者|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |获取预订|管理者、读取者和写入者|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |创建 Webhook|管理者和写入者|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |更新 Webhook|管理者和写入者|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |删除 Webhook|管理者|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |获取 Webhook|管理者、读取者和写入者|-|

## 使用 API 密钥
{: #apikeys}

创建服务凭证时，您可能注意到显示 apiKey，而不是 appSecret。

要使用任何 REST API，您必须使用以下 curl 命令生成访问令牌：

### 参数

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### 响应

```
{
    "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```

使用上述 curl 命令生成访问令牌时，您现在可以通过在 Authorization 头中传递“Bearer <value of access_token>”来操作 REST API。

例如：

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

有关 IAM 的更多信息，请参阅 [IAM 访问权](https://cloud.ibm.com/docs/iam?topic=iam-userroles)。
