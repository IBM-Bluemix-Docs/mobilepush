----

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# 푸시 알림의 보안 
{: #overview-push}
마지막 업데이트 날짜: 2017년 6월 27일
{: .last-updated}


{{site.data.keyword.mobilepushshort}} API는 다음 두 유형의 시크릿으로 보호됩니다.

- **appSecret**: `appSecret`은 일반적으로 백엔드 애플리케이션에서 호출하는 API를 보호합니다(예: {{site.data.keyword.mobilepushshort}}를 전송하는 API 및 설정을 구성하는 API). 
- **clientSecret**: `clientSecret`은 일반적으로 모바일 클라이언트 애플리케이션에서 호출하는 API를 보호합니다. 오직 하나의 API만 이 `clientSecret`이 필요한 연관된 사용자 ID의 디바이스 등록과 관련되어 있습니다. 모바일 클라이언트에서 호출된 기타 API에서는 `clientSecret`이 필요하지 않습니다.  

`appSecret` 및 `clientSecret`은 애플리케이션을 {{site.data.keyword.mobilepushshort}} 서비스와 바인딩하는 시점에 모든 서비스 인스턴스에 할당됩니다. 시크릿을 전달하는 방법과 전달 대상 API에 대한 정보는 [REST API![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://mobile.{DomainName}/imfpush/) 문서를 참조하십시오. 

## appSecret 
{: #push-api-rest-secret}

애플리케이션이 {{site.data.keyword.mobilepushshort}}에 바인드되는 경우 서비스에서 appSecret(고유 키)을 생성하여 응답 헤더를 통해 전달합니다. IBM {{site.data.keyword.mobilepushshort}} for IBM Cloud Rest API를 사용 중인 경우 보호해야 하는 API에 대한 정보를 얻으려면 REST API 참조를 사용하십시오. 자세한 정보는 [Push REST API![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://mobile.{DomainName}/imfpush/){: new_window}를 참조하십시오. 

요청 헤더에 appSecret이 포함되어야 합니다. 그렇지 않으면 서버가 401 권한 없음 오류 코드를 리턴합니다. {{site.data.keyword.mobilepushshort}}가 애플리케이션에 추가되면 특정 AppID가 작성됩니다. 응답 과정에서 태그를 작성하거나 메시지를 전송하는 데 사용되는 appSecret 헤더를 받습니다. 카탈로그 또는 표준 유형의 서비스를 통해 오퍼레이션이 발생합니다.

appSecret 값을 가져오려면 다음을 수행하십시오. 

1. 푸시 서비스에 바인드되는 *app-name*을 클릭하십시오.
2. **신임 정보 표시** 링크를 클릭하여 appSecret(AppID)을 표시하십시오.

**신임 정보 표시** 화면에 다음과 같이 AppSecret에 대한 정보가 표시됩니다. 
```
	{
    "imfpush_Dev": [
   {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://imfpush.ng.bluemix.net/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.ng.bluemix.net/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**참고**: 이전 애플리케이션에서는 사용자 ID 필드에서 디바이스를 등록하거나 업데이트하는 경우에만 clientSecret을 전달해야 했습니다. 모바일 클라이언트와 브라우저 클라이언트에서 호출한 기타 모든 API에는 clientSecret이 필요하지 않았습니다. 이와 같은 이전 애플리케이션에서 디바이스 등록 또는 호출 업데이트에 선택적으로 clientSecret을 계속 사용할 수 있습니다. 그러나 모든 클라이언트 API 호출에 clientSecret 검사를 적용하는 것이 좋습니다. 기존 애플리케이션에서 이를 적용할 수 있도록 공개된 새 `verifyClientSecret` API가 있습니다. 새 애플리케이션의 경우에는 clientSecret 검사가 모든 클라이언트 API 호출에 적용되며, 이 동작은 `verifyClientSecret` API로 변경될 수 없습니다.

기본적으로 클라이언트 시크릿 확인은 새 앱에서만 적용됩니다. 기존 앱과 새 앱 모두 verifyClientSecret REST API를 사용하여 클라이언트 시크릿 확인을 사용 또는 사용 안함으로 설정할 수 있습니다. applicationId와 deviceId를 아는 사용자에게 디바이스가 노출되지 않도록 클라이언트 시크릿 확인을 적용하는 것이 좋습니다. 

`clientSecret`의 기밀이 유지되며 모바일 앱으로 하드코드화되지 않았음을 확인하십시오. 애플리케이션 런타임 중에 동적으로 `clientSecret`의 가져오기에 사용될 수 있는 다양한 애플리케이션 초기화 패턴이 있습니다. 시퀀스 다이어그램은 이와 같은 가능한 패턴을 간략하게 보여줍니다.
![Enable_Push](images/init_client_secret.jpg) 



