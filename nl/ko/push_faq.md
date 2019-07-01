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


# 자주 묻는 질문 
{: #faq}

### 내 토큰이 왜 무효화되었습니까?
{: #faq-tokens}	

디바이스, 브라우저, Chrome 앱 & 확장 프로그램 등록의 경우, Push Notifications 서비스는 알림 제공자(Apple의 경우 APNs 또는 Google의 경우 FCM)에서 발행된 토큰에 대한 고유 참조를 유지보수합니다. 몇 가지 이유로 서비스 알림 제공자가 토큰을 무효화할 수 있습니다. 

하나의 예는 디바이스에서 앱을 설치 제거하는 경우입니다. 이와 같은 시나리오에서 디바이스가 무효화되는 제공자 응답을 기반으로 알림을 전달하려고 하면 {{site.data.keyword.mobilepushshort}} 서비스가 디바이스 또는 웹 브라우저 등록을 제거합니다. 그런 다음 이러한 무효화된 디바이스에 알림을 전송하려는 시도를 제한합니다. 

등록되지 않은 디바이스가 있는 경우에도 문제점이 발생할 수 있습니다.

계속하려면 올바른 서버 API 키 및 발신인 ID를 획득했는지 확인하십시오. [알림 제공자 신임 정보 획득](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)을 참조하십시오.

### 웹 푸시 SDK 초기화를 시도할 때 *Notification is not working for WEB_Chrome.*이라는 메시지가 표시되는 이유는 무엇입니까?
{: #faq-web-chrome}	

사용자가 웹 푸시 SDK에 대한 FCM 신임 정보를 변경했을 수 있으며, 이 경우 Chrome 브라우저에서 메시지 전달이 실패할 수 있습니다. 실패를 방지하려면 *bmsPush.unRegisterDevice*를 호출하십시오.

### 웹 푸시용 SDK 초기화를 시도할 때 *Service workers aren't supported in this browser*라는 메시지가 표시됩니다. 문제점이 무엇입니까? 
{: #faq-service-workers}	

[3단계: 푸시 서비스 클라이언트 SDK 설정](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)에 언급된 단계를 따르십시오. 또한 다음 사항을 확인하십시오.

1. 올바른 시작 메소드를 사용합니다. 
2. 루트 폴더에 `manifest.json` 파일을 포함하십시오.
3. 웹 사이트를 호스팅하십시오. 되도록이면 IBM Cloud에서 `node.js` 스타터를 작성하여 시도해 보십시오. 예: https://<mysamplewebsite>.cloud.ibm.com/.	

### 웹 푸시 웹 구성 오류를 어떻게 해결할 수 있습니까?
{: #faq-web-config-errors}	

`BMSPushSDK.js`의 웹 푸시 오류에는 실패에 대한 정보가 포함되어 있습니다. [문제점 해결](/docs/services/mobilepush?topic=mobile-pushnotification-errors)을 참조하십시오.	

### 디바이스가 오프라인인 경우 알림이 지속됩니까?
{: #faq-notification-persist}	

이 기능은 알림 제공자에 따라 달라집니다.	

### messageID는 애플리케이션에 고유하며 그 크기는 어떻습니까?
{: #faq-messageid}	

messageID는 애플리케이션에 고유하며 8자로 제한됩니다. 영숫자가 가능합니다.

### 페이로드 크기의 관점에서 Push Notifications의 한계는 무엇입니까?
{: #faq-limits-push-payload-size}	

{{site.data.keyword.mobilepushshort}} 메시지 페이로드 크기는 게이트웨이(FCM, APNs) 및 클라이언트 플랫폼의 제한조건에 따라 다릅니다. 

iOS 8 이상의 경우 허용된 최대 크기는 4KB입니다. APNs는 이 한계를 초과하는 알림은 전송하지 않는다는 점을 참고하십시오. Android, Firefox 브라우저, Chrome 브라우저 및 Chrome 앱 & 확장 프로그램의 경우, 허용되는 최대 메시지 페이로드 크기로 4KB의 제한이 있습니다.	

### 전송된 알림이 BMS 서버에 저장됩니까?
{: #faq-bms-servers}	

예, 알림이 90일 동안 저장됩니다. 기밀 메시지를 알림으로 전송하지 않도록 권장합니다.

### Doze 모드에서 디바이스에 알림을 전송할 수 있습니까?
{: #faq-doze-mode}	

이 기능은 지원되지 않습니다.	

### Push Notifications 서비스에 사용할 수 있는 다른 가격 플랜은 무엇입니까?
{: #faq-pricing-plans}	

* <b>고급 플랜</b>: 100.00달러/인스턴스, 0.50달러/백만 개의 디지털 메시지, 0.50달러/백만 개의 주소 지정 가능 디바이스에 대해 사용 가능합니다. 고급 플랜의 경우, 백만 개의 주소 지정 가능 디바이스 및 일억 개의 디지털 메시지에 푸시 알림을 전송할 수 있습니다. 고급 플랜에는 메시지 매개변수화 및 엔드 투 엔드 메시지 라이프사이클 추적과 같은 기능이 포함됩니다.

* <b>기본 플랜</b>: 1.00달러/백만 개의 디지털 메시지에 사용 가능합니다. 기본 플랜으로 푸시 알림을 고유 디바이스, 브라우저, 엔드포인트 또는 웹훅 기반 이벤트에 전송할 수 있습니다. 

* <b>Lite 플랜</b>: 월별 십만 개의 무료 디지털 메시지를 특징으로 하는 무료 사용제입니다. 그러나 라이트 플랜 서비스는 비활성 상태로 30일 후에 삭제됩니다.	

### 튜토리얼 또는 새로운 기능과 같은 자세한 정보를 어디서 찾을 수 있습니까?
{: #faq-what-is-new}	

Push Notifications 서비스 [동영상](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA)을 찾아보십시오.	

### 알림과 메시지 사이에 차이점이 있습니까?
{: #faq-diff-notification-message}	

예. _메시지_는 사용자가 {{site.data.keyword.mobilepushshort}} 서비스에 제출하는 것입니다. 서비스는 이를 _알림_으로 알림 게이트웨이(APNs/FCM)에 디스패치하며, 이는 디바이스 또는 웹 브라우저에 전달됩니다.

서비스에 제출하는 모든 메시지의 경우, 대상이 되는 청취자는 알림을 수신합니다.	

### Push Notifications 모니터링 대시보드에 전송된 메시지의 상태가 표시됩니까?
{: #faq-push-monitor-dashboard}	

모니터링 유틸리티는 모든 전송된 메시지에 대한 상태를 표시합니다. 메시지는 다음과 같은 상태일 수 있습니다.
	
* 전송: 알림이 전송된 디바이스의 수입니다.
* 도달: 알림이 도달했던 디바이스의 수입니다.
* 열림: 알림이 열린 디바이스의 수입니다.
* 올바르지 않음: 토큰이 올바르지 않은 디바이스의 수입니다.

자세한 정보는 [IBM Push Notifications ReST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/)의 GET 메시지 보고서를 참조하십시오.	

### 푸시 알림은 일반 사용자 디바이스에 대한 푸시 알림 전달을 모니터합니까? Android와 iOS 모두의 경우?
{: #faq-end-user-device}	

푸시 알림은 일반 사용자 디바이스에서 열었거나 본 알림의 수를 기준으로 모니터됩니다. Android 및 iOS에 모두 사용 가능합니다. 디바이스 ID 기반 모니터링은 지원되지 않습니다. 

### 서버는 현재 요청을 처리할 수 없다는 메시지가 표시됩니까? 이를 어떻게 해결할 수 있습니까?
{: #faq-server-unable-to-handle-requests}	

오류 코드 FPWSE0025E와 함께 오류가 표시될 수 있습니다. 이는 서버가 처리하기에 너무 많은 요청으로 인한 것입니다. 나중에 요청을 다시 제출해볼 수 있습니다.	

### 태그별로 알림을 전송하고 있지만, 수동으로 추가하기 어려울 수 있는 긴 태그 목록이 있습니다. 
{: #faq-tag-based-notification}	

REST API를 사용하여 태그 추가를 자동화할 수 있습니다. [POST 대형 메시지](https://eu-gb.imfpush.cloud.ibm.com/imfpush/)를 참조하십시오.

### 사용자의 모바일 디바이스에 저장된 정보로 푸시 알림 전달을 어떻게 필터링할 수 있습니까?
{: #faq-filter-device}	

이는 애플리케이션 개발의 컨텍스트에서 처리되어야 합니다.

### 분석 방식별 전달 보고서와 같은 사용자 정의 보고서를 추가하도록 푸시 알림 모니터링을 더 사용자 정의할 수 있습니까?
{: #faq-customize-delivery-report}	

이 기능은 지원되지 않습니다.

### 새 앱 사용자 또는 모바일 앱에 한동안 액세스하지 않은 사용자에 대한 세그먼트를 작성할 수 있습니까?
{: #faq-create-segment}	

이는 애플리케이션 개발의 컨텍스트에서 처리되어야 합니다.
	
### REST API를 사용하여 대량으로 모바일 디바이스를 등록/업데이트할 수 있습니까?
{: #faq-register-mobile-devices}	

디자인별로 SDK를 사용하여 모바일 애플리케이션에서 디바이스 등록/업데이트가 호출됩니다. REST API를 사용하는 대량 등록/업데이트는 지원되지 않습니다. REST API를 사용하여 동시에 많은 디바이스 등록/업데이트가 호출되면 오랜 시간이 걸리거나 실패할 수 있습니다.	

### appSecret이 없는 경우, 어떻게 푸시 알림을 전송하거나 REST API를 사용할 수 있습니까?
{: #faq-rest-api-appsecret}	

{{site.data.keyword.mobilepushshort}} 서비스가 IAM을 채택했으므로 사용자가 서비스 인증 정보를 작성할 때 `apiKey`가 `appSecret` 대신 표시됩니다.

임의의 REST API를 사용하려면 다음 curl 명령을 사용하여 액세스 토큰을 생성해야 합니다.

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

앞의 curl 명령을 사용하여 액세스 토큰을 생성할 때 권한 헤더에서 `Bearer <value of access_token>`를 전달하여 REST API를 작동할 수 있습니다.

예를 들면, 다음과 같습니다.

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \
   "message": { \
     "alert": "Notification alert message" \
   } \
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
