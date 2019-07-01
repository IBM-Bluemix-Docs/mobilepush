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

# 서비스 액세스 관리
{: #service-access-management}

{{site.data.keyword.mobilepushshort}} 및 {{site.data.keyword.Bluemix_notm}} IAM(Identity and Access Management)을 사용하여 계정 관리자가 계정 내의 사용자 액세스를 관리할 수 있습니다.
{: shortdesc}

계정 소유자로서 계정 내에 정책을 설정하여 다른 사용자에 대해 다른 레벨의 액세스를 작성할 수 있습니다. 예를 들어, 특정 사용자가 한 인스턴스에 대해서는 **읽기 전용** 액세스 권한을 가지나 다른 인스턴스에는 **쓰기** 액세스 권한을 가질 수 있습니다. 누가 {{site.data.keyword.mobilepushshort}}의 인스턴스를 작성, 업데이트 및 삭제하도록 허용될 것인지 결정할 수 있습니다.

**참고:** {{site.data.keyword.mobilepushshort}} 서비스가 IAM을 채택함에 따라 새 인스턴스에 대해 앱 시크릿이 생성되지 않습니다. [대신 API 키](https://cloud.ibm.com/docs/iam?topic=iam-manapikey)를 사용해야 합니다.

## 사용자 역할
{: #roles}

액세스 정책의 범위는 사용자에게 지정된 역할에 따라 다릅니다.
{: shortdesc}

정책에서는 액세스를 여러 레벨에 부여할 수 있습니다. 몇 가지 옵션은 다음과 같습니다.
<ul><ul>
  <li>사용자 계정의 서비스의 모든 인스턴스에 대한 액세스</li>
  <li>사용자 계정의 개별 서비스 인스턴스에 대한 액세스</li>
  <li>인스턴스 내의 특정 리소스에 대한 액세스</li>
  <li>사용자 계정의 모든 IAM 사용 서비스에 대한 액세스</li>
</ul></ul>

플랫폼 관리 역할은 사용자가 플랫폼 레벨에서 서비스 리소스에 대한 태스크를 수행하도록 할 수 있습니다. 예를 들어, ID 작성 또는 삭제, 인스턴스 작성 및 앱에 인스턴스 바인드를 수행할 수 있는 사용자를 결정하도록 지정될 수 있습니다. 다음 표에는 플랫폼 관리 역할과 관련된 조치에 대한 자세한 설명이 있습니다.

<table>
  <tr>
    <th> 플랫폼 역할 </th>
    <th>권한</th>
    <th>예제 조치</th>
  </tr>
  <tr>
    <td><i>뷰어</i></td>
    <td>{{site.data.keyword.mobilepushshort}} 인스턴스를 볼 수 있습니다.</td>
    <td>Cloud Directory 사용자 데이터 또는 ID 제공자 구성을 볼 수 있습니다.</td>
  </tr>
  <tr>
    <td><i>편집자</i></td>
    <td>{{site.data.keyword.mobilepushshort}} 인스턴스를 보고 바인드할 수 있습니다.</td>
    <td>애플리케이션을 {{site.data.keyword.mobilepushshort}}의 인스턴스에 바인드할 수 있습니다.</td>
  </tr>
  <tr>
    <td><i>운영자</i></td>
    <td>{{site.data.keyword.mobilepushshort}} 인스턴스를 작성, 삭제, 편집, 일시중단, 재개, 보기 또는 바인드할 수 있습니다.</td>
    <td>카탈로그에서 {{site.data.keyword.mobilepushshort}} 인스턴스를 작성 또는 삭제할 수 있습니다.</td>
  </tr>
  <tr>
    <td><i>관리자</i></td>
    <td>계정 내의 모든 서비스에 대한 모든 관리 조치를 수행할 수 있습니다.</td>
    <td>모든 운영자 조치를 수행할 수 있으며 기타 사용자에게 정책을 지정할 수 있습니다.</td>
  </tr>
</table>

</br>
</br>
다음 표에는 서비스 액세스 역할에 맵핑된 조치에 대한 자세한 설명이 있습니다. 서비스 액세스 역할을 사용하여 사용자가 {{site.data.keyword.mobilepushshort}}에 액세스할 수 있으며 {{site.data.keyword.mobilepushshort}} API를 호출할 수 있습니다.


<table>
  <tr>
    <th>서비스 역할</th>
    <th>권한</th>
    <th>예제 조치</th>
  </tr>
  <tr>
    <td><i>독자</i></td>
    <td>{{site.data.keyword.mobilepushshort}} 인스턴스 데이터를 볼 수 있습니다.</td>
    <td>사용자 데이터 또는 ID 제공자 정보와 같은 서비스 인스턴스의 세부사항을 볼 수 있습니다.</td>
  </tr>
  <tr>
    <td> <i>작성자 또는 관리자</i></td>
    <td>{{site.data.keyword.mobilepushshort}} 인스턴스를 보고 변경할 수 있습니다.</td>
    <td>모든 독자 조치를 수행할 수 있으며 ID 제공자 구성 편집 등과 같은 서비스 인스턴스 편집을 수행할 수 있습니다.</li></ul></td>
  </tr>
</table>

UI에서 사용자 역할을 지정하는 방법에 대한 자세한 정보는 [IAM 액세스 관리](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser)를 참조하십시오.


## {{site.data.keyword.mobilepushshort}} 액세스 정책
{: #access}

계정의 {{site.data.keyword.mobilepushshort}} 서비스에 액세스하는 모든 사용자에게는 IAM 사용자 역할이 정의된 액세스 정책이 지정되어야 합니다. 정책은 선택한 서비스 또는 인스턴스의 컨텍스트 내에서 사용자가 수행할 수 있는 조치를 판별합니다.
{: shortdesc}

조치는 {{site.data.keyword.Bluemix_notm}} 서비스에 의해 서비스에서 수행할 수 있는 조작으로 사용자 정의되고 정의됩니다. 그런 다음 조치가 IAM 사용자 역할에 맵핑됩니다. 일부 조치는 {{site.data.keyword.cloudaccesstrailshort}} 서비스로 추적될 수 있습니다. 다음 표에서 조치 및 {{site.data.keyword.mobilepushshort}}에 대한 필수 권한이 맵핑됩니다.

|조치 |설명 |필수 역할 |
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |앱 설정 가져오기 |관리자, 작성자, 독자|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |앱 설정 삭제 |관리자|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |앱 설정 업데이트 |관리자|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |디바이스 가져오기 |관리자, 작성자, 독자|
|`POST /imfpush/v1/apps/{applicationId}/devices` |디바이스 등록 |관리자, 작성자|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |디바이스 업데이트 |관리자, 작성자|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |디바이스 삭제 |관리자|
|`POST /imfpush/v1/apps/{applicationId}/messages` |메시지 보내기 |관리자, 작성자|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |대량 메시지 전송 |관리자, 작성자|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |메시지 삭제 |관리자|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |메시지 가져오기 |관리자, 독자, 작성자|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |메시지 전달 상태 업데이트|관리자, 작성자|
|`POST /imfpush/v1/apps/{applicationId}/tags` |태그 작성 |관리자, 작성자|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |태그 업데이트 |관리자, 작성자|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |태그 삭제 |관리자|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |태그 가져오기 |관리자, 독자, 작성자|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |구독 작성 |관리자, 작성자|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |구독 삭제 |관리자|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |구독 가져오기 |관리자, 독자, 작성자|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |웹훅 작성 |관리자, 작성자|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |웹훅 업데이트 |관리자, 작성자|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |웹훅 삭제 |관리자|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |웹훅 가져오기 |관리자, 독자, 작성자|-|

## API 키 작업
{: #apikeys}

서비스 인증 정보를 작성할 때 appSecret 대신 apiKey가 표시되는 것을 눈치챌 수 있을 것입니다.

임의의 REST API를 사용하려면 다음 curl 명령을 사용하여 액세스 토큰을 생성해야 합니다.

### 매개변수

```
  curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### 응답

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

앞의 curl 명령을 사용하여 액세스 토큰을 생성할 때 권한 헤더에서 'Bearer <value of access_token>'을 전달하여 REST API를 작동할 수 있습니다.

예를 들면, 다음과 같습니다.

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \
   "message": { \
     "alert": "Notification alert message" \
   } \
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

IAM에 대한 자세한 정보는 [IAM 액세스](https://cloud.ibm.com/docs/iam?topic=iam-userroles)를 참조하십시오.
