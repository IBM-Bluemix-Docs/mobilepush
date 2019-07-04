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

# 管理服務存取權
{: #service-access-management}

使用 {{site.data.keyword.mobilepushshort}} 和 {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM)，帳戶擁有者可以管理您帳戶中的使用者存取權。
{: shortdesc}

作為帳戶擁有者，您可以在帳戶內設定原則，以便為不同使用者建立不同層次的存取權。例如，某些使用者可以對一個實例具有**唯讀**存取權，而對另一個實例具有**寫入**存取權。您可以決定誰有權建立、更新和刪除 {{site.data.keyword.mobilepushshort}} 的實例。

**附註：**由於 {{site.data.keyword.mobilepushshort}} 服務採用了 IAM，不會為新實例產生應用程式密碼。而是必須使用
[API 金鑰](https://cloud.ibm.com/docs/iam?topic=iam-manapikey)。

## 使用者角色
{: #roles}

存取原則的範圍是以使用者的受指派角色為基礎。
{: shortdesc}

原則可讓您在不同層次授與存取權。部分選項包括：
<ul><ul>
  <li>對帳戶中所有服務實例的存取權</li>
  <li>對帳戶中個別服務實例的存取權</li>
  <li>對實例中特定資源的存取權</li>
  <li>對您帳戶中所有已啟用 IAM 功能之服務的存取權</li>
</ul></ul>

平台管理角色可讓使用者在平台層次對服務資源執行作業。例如，可以指派角色來決定誰可以建立或刪除 ID、建立實例，以及將實例連結至應用程式。下表詳述與平台管理角色產生關聯的動作。

<table>
  <tr>
    <th>平台角色</th>
    <th>許可權</th>
    <th>動作範例</th>
  </tr>
  <tr>
    <td><i>檢視者</i></td>
    <td>檢視 {{site.data.keyword.mobilepushshort}} 實例。</td>
    <td>您可以看到 Cloud Directory 使用者的資料或身分提供者配置。</td>
  </tr>
  <tr>
    <td><i>編輯者</i></td>
    <td>檢視及連結 {{site.data.keyword.mobilepushshort}} 實例。</td>
    <td>您可以將應用程式連結至 {{site.data.keyword.mobilepushshort}} 的實例。</td>
  </tr>
  <tr>
    <td><i>操作員</i></td>
    <td>建立、刪除、編輯、暫停、繼續、檢視或連結 {{site.data.keyword.mobilepushshort}} 實例。</td>
    <td>您可以建立或刪除型錄中的 {{site.data.keyword.mobilepushshort}} 實例。</td>
  </tr>
  <tr>
    <td><i>管理者</i></td>
    <td>帳戶中所有服務的所有管理動作。</td>
    <td>您可以執行所有操作員動作，而且能夠將原則指派給其他使用者。</td>
  </tr>
</table>

</br>
</br>
下表格詳細描述了對映到服務存取角色的動作。服務存取角色讓使用者能夠存取 {{site.data.keyword.mobilepushshort}} 以及呼叫 {{site.data.keyword.mobilepushshort}} API。


<table>
  <tr>
    <th>服務角色</th>
    <th>許可權</th>
    <th>動作範例</th>
  </tr>
  <tr>
    <td><i>讀者</i></td>
    <td>檢視 {{site.data.keyword.mobilepushshort}} 實例資料。</td>
    <td>可以檢視服務實例的詳細資料，例如使用者資料或身分提供者資訊。</td>
  </tr>
  <tr>
    <td> <i>撰寫者或管理員</i></td>
    <td>檢視和變更 {{site.data.keyword.mobilepushshort}} 實例。</td>
    <td>可以執行所有讀者動作並編輯服務實例，例如編輯身分提供者配置。</li></ul></td>
  </tr>
</table>

如需在使用者介面中指派使用者角色的相關資訊，請參閱[管理 IAM 存取](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser)。


## {{site.data.keyword.mobilepushshort}} 存取原則
{: #access}

必須為帳戶中存取 {{site.data.keyword.mobilepushshort}} 服務的每一個使用者指派定義了 IAM 使用者角色的存取原則。該原則確定使用者可在您所選服務或實例的環境定義中執行的動作。
{: shortdesc}

這些動作是自訂的，並由 {{site.data.keyword.Bluemix_notm}} 服務定義為可在服務中執行的作業。然後，這些動作將對映到 IAM 使用者角色。可使用 {{site.data.keyword.cloudaccesstrailshort}} 服務來追蹤所執行的某些動作。在下表中，會對映 {{site.data.keyword.mobilepushshort}} 的動作與必要許可權。

|動作|說明|必要角色|
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |取得應用程式設定 |管理員、撰寫者、讀者|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |刪除應用程式設定 |管理員|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |更新應用程式設定|管理員|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |取得裝置|管理員、撰寫者、讀者|
|`POST /imfpush/v1/apps/{applicationId}/devices` |登錄裝置|管理員、撰寫者|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |更新裝置|管理員、撰寫者|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |刪除裝置|管理員|
|`POST /imfpush/v1/apps/{applicationId}/messages` |傳送訊息|管理員、撰寫者|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |傳送大量訊息|管理員、撰寫者|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |刪除訊息|管理員|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |取得訊息|管理員、讀者、撰寫者|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |更新訊息傳遞狀態|管理員、撰寫者|
|`POST /imfpush/v1/apps/{applicationId}/tags` |建立標籤|管理員、撰寫者|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |更新標籤|管理員、撰寫者|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |刪除標籤|管理員|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |取得標籤|管理員、讀者、撰寫者|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |建立訂閱|管理員、撰寫者|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |刪除訂閱|管理員|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |取得訂閱|管理員、讀者、撰寫者|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |建立 Webhook|管理員、撰寫者|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |更新 Webhook|管理員、撰寫者|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |刪除 Webhook|管理員|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |取得 Webhook|管理員、讀者、撰寫者|-|

## 使用 API 金鑰
{: #apikeys}

建立服務憑證時，您可能注意到顯示 apiKey，而不是 appSecret。

若要使用任何 REST API，您必須使用下列 curl 指令產生存取記號：

### 參數

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### 回應

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

使用上述 curl 指令產生存取記號時，您現在可以透過在 Authorization 標頭中傳遞 "Bearer <value of access_token>" 來操作 REST API。

例如：

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

如需 IAM 的相關資訊，請參閱 [IAM 存取](https://cloud.ibm.com/docs/iam?topic=iam-userroles)。
