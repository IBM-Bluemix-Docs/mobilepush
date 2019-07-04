---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, faq, frequently asked questions

subcollection: mobile-pushnotification

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 常见问题 
{: #faq}

### 为什么令牌会失效？
{: #faq-tokens}	

对于设备、浏览器和 Chrome Apps & Extensions 注册，Push Notifications 服务会保持对通知提供程序颁发的令牌的唯一引用。对于 Apple，通知提供程序为 APNs；而对于 Google，则为 FCM。该服务通知提供程序可能出于几种原因使令牌失效。 

例如，在设备上卸载应用程序期间。在这种情况下，如果有传递通知的尝试，通知提供者就会给出有关设备已失效的响应，{{site.data.keyword.mobilepushshort}} 服务会根据该响应来除去设备或 Web 浏览器注册。这样会抑制后续的尝试，阻止将通知发送给这些已失效的设备。 

如果注销了设备，也可能会遇到此问题。

确保获取有效的“服务器 API 密钥”和“发送方标识”以继续。请参阅[获取通知提供程序凭证](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)。

### 尝试初始化 Web 推送 SDK 时，为什么会收到消息称*通知对 WEB_Chrome 无效*？
{: #faq-web-chrome}	

您可能更改了用于 Web 推送 SDK 的 FCM 凭证，因此对于 Chrome 浏览器，消息传递可能会失败。请确保调用 *bmsPush.unRegisterDevice* 以避免失败。

### 尝试初始化 Web 推送的 SDK 时，收到消息称*此浏览器中不支持服务工作程序*。问题可能出在哪里？ 
{: #faq-service-workers}	

执行[第 3 步：设置 Push 服务客户机 SDK](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3) 中提到的步骤。另请确保：

1. 使用正确的启动方法。 
2. 将 `manifest.json` 文件包含在根文件夹中。
3. 托管 Web 站点。最好在 IBM Cloud 中创建 `node.js` 入门模板以试用。例如：https://<mysamplewebsite>.cloud.ibm.com/。	

### 如何解决 Web 推送 Web 配置错误？
{: #faq-web-config-errors}	

来自 `BMSPushSDK.js` 的 Web 推送错误包含失败的相关信息。请参阅[故障诊断](/docs/services/mobilepush?topic=mobile-pushnotification-errors)。	

### 如果设备脱机，通知会持久存储吗？
{: #faq-notification-persist}	

此功能取决于通知提供程序。	

### messageID 对于应用程序是否唯一，其大小是多少？
{: #faq-messageid}	

messageID 对于应用程序唯一，其大小限制为 8 个字符。可以为字母数字。

### Push Notifications 在有效内容大小方面有哪些限制？
{: #faq-limits-push-payload-size}	

{{site.data.keyword.mobilepushshort}} 消息有效内容大小取决于网关（FCM、APNs）和客户机平台规定的约束。 

对于 iOS 8 和更高版本，允许的最大大小为 4 KB。请注意，APNs 不会发送超过此限制的通知。对于 Android、Firefox 浏览器、Chrome 浏览器和 Chrome Apps & Extensions，允许的消息有效内容最大大小限制为 4 KB。	

### 已发送的通知是存储在 BMS 服务器中吗？
{: #faq-bms-servers}	

是的，通知会存储九十天时间。建议不要将任何保密消息作为通知发送。

### 能向打盹方式下的设备发送通知吗？
{: #faq-doze-mode}	

不支持此功能。	

### Push Notifications 服务有哪些可用的价格套餐？
{: #faq-pricing-plans}	

* <b>高级套餐</b>：使用此套餐的价格是 100.00 美元/实例、0.50 美元/百万条数字消息、0.50 美元/百万个可寻址设备。运用高级套餐，您可以向 1 百万个可寻址设备和 1 亿条数字消息发送推送通知。高级套餐包括参数化消息和端到端消息生命周期跟踪之类的功能。

* <b>基本套餐</b>：使用此套餐的价格是 1.00 美元/百万条数字消息。使用基本套餐，可以向唯一的设备、浏览器、端点或基于 Webhook 的事件发送推送通知。 

* <b>轻量套餐</b>：这是免费套餐，每个月可以免费使用 10 万条数字消息。但是，轻量套餐服务在处于不活动状态 30 天后会被删除。	

### 在哪里能找到诸如教程或新增内容之类的更多信息？
{: #faq-what-is-new}	

请浏览 Push Notifications 服务[视频](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA)。	

### 通知和消息之间有差别吗？
{: #faq-diff-notification-message}	

有。_消息_是用户向 {{site.data.keyword.mobilepushshort}} 服务提交的内容。该服务会将此内容作为_通知_分派给通知网关 (APNs/FCM)，然后此内容会传递到设备或 Web 浏览器。

对于您提交给该服务的每条消息，目标受众都会收到一个通知。	

### Push Notifications 监视仪表板针对所发送消息会显示任何状态吗？
{: #faq-push-monitor-dashboard}	

监视实用程序针对每条已发送消息都会显示状态。消息可能处于以下状态：
	
* 已发送：向其发送通知的目标设备数。
* 已显示：通知到达的目标设备数。
* 已打开：已打开通知的设备数。
* 无效：令牌在其中无效的设备数。

有关更多信息，请参阅 [IBM Push Notifications REST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/) 中的“通过 GET 操作获取消息报告”。	

### 推送通知会监视推送通知传递至最终用户设备吗？对于 Android 和 iOS 都是这样吗？
{: #faq-end-user-device}	

将基于最终用户设备中已显示或已打开的通知数监视推送通知。此功能对于 Android 和 iOS 均可用。不支持基于设备标识的监视。 

### 我收到消息称，服务器当前无法处理请求。我该如何解决此问题？
{: #faq-server-unable-to-handle-requests}	

您可能会看到此错误及错误代码 FPWSE0025E。这可能是因为服务器要处理的请求太多。可以尝试稍后重新提交请求。	

### 我要通过标记发送通知，但标记列表太长，手动添加可能很麻烦。 
{: #faq-tag-based-notification}	

可以使用 REST API 来自动添加标记。请参阅[通过 POST 操作发布批量消息](https://eu-gb.imfpush.cloud.ibm.com/imfpush/)。

### 我该如何按用户移动设备中存储的消息来过滤推送通知传递？
{: #faq-filter-device}	

这应该在应用程序开发上下文中进行处理。

### 我能进一步定制推送通知监视以添加定制报告（例如，按分段列出的传递报告）吗？
{: #faq-customize-delivery-report}	

不支持此功能。

### 我能为新应用程序用户或有一段时间未访问移动应用程序的用户创建分段吗？
{: #faq-create-segment}	

这应该在应用程序开发上下文中进行处理。
	
### 我可以使用 REST API 成批注册/更新移动设备吗？
{: #faq-register-mobile-devices}	

根据设计，将使用 SDK 从移动应用程序调用注册/更新设备的操作。不支持通过 REST API 批量注册/更新。如果使用 REST API 同时调用许多设备注册/更新，那么可能需要很长时间或者可能失败。	

### 我没有 appSecret 时，如何发送 Push Notifications 或使用 Rest API？
{: #faq-rest-api-appsecret}	

由于 {{site.data.keyword.mobilepushshort}} 服务采用了 IAM，在用户创建服务凭证时会显示 `apiKey` 而不是 `appSecret`。

要使用任何 REST API，您必须使用以下 curl 命令生成访问令牌：

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```

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
{: codeblock}

使用上述 curl 命令生成访问令牌时，您现在可以通过在 Authorization 头中传递 `Bearer <value of access_token>` 来操作 REST API。

例如：

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
