---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, service instance, cordova application

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 3단계: 서비스 인스턴스 구성 
{: #push_step_2}

[알림 신임 정보 획득](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)을 수행했는지 확인하십시오.

## Android 및 Chrome 앱 & 확장 프로그램의 경우
{: #push_step_2_Android}

[알림 제공자 신임 정보 획득](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)을 수행하여 FCM 프로젝트를 설정하고 신임 정보를 가져왔는지 확인하십시오.

Android 애플리케이션 및 Google Chrome 앱 & 확장 프로그램에 대한 FCM 신임 정보를 구성하려면 다음 단계를 완료하십시오.

1. IBM Cloud 카탈로그를 연 후 작성한 {{site.data.keyword.mobilepushfull}} 서비스 인스턴스를 클릭하십시오. 
2. **관리** > **구성**을 클릭하십시오. 
3. 다음 옵션 중에서 선택하십시오. 
	- Android의 경우: **모바일**을 선택한 다음 FCM 푸시 신임 정보 탭을 발신인 ID/프로젝트 번호 및 API 키로 업데이트하십시오. 
	- Google Chrome 앱 & 확장 프로그램의 경우: **웹**을 선택한 다음 Chrome 앱 및 확장 프로그램 탭을 발신인 ID/프로젝트 번호 및 API 키로 업데이트하십시오. 
4. **저장**을 클릭하십시오. Push Notifications 서비스가 이제 구성됩니다.

다음 단계는 [푸시 서비스 클라이언트 SDK 설정](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)입니다.


## Cordova 애플리케이션의 경우 
{: #push_step_2_b}


Cordova는 JavaScript, CSS 및 HTML을 사용하여 하이브리드 애플리케이션을 빌드하는 플랫폼입니다. {{site.data.keyword.mobilepushshort}} 서비스는 Cordova 기반 iOS 및 Android 애플리케이션의 개발을 지원합니다.

사용자의 디바이스에 푸시 알림을 수신하기 위해 Cordova 애플리케이션을 사용으로 설정하려면 [Push Notifications Cordova 플러그인 푸시 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)를 완료하십시오.



## iOS 애플리케이션 및 Safari 브라우저의 경우 
{: #enable-push-ios-notifications}


알림을 전송하기 위해 {{site.data.keyword.mobilepushshort}} 서비스를 사용하려면 1단계: [알림 제공자 신임 정보 획득](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1)에서 작성한 `.p12` 인증서를 업로드하십시오. 이 인증서에는 애플리케이션 빌드와 공개에 필요한 개인 키와 SSL 인증서가 포함되어 있습니다. REST API를 사용하여 APNs 인증서를 업로드할 수도 있습니다.

**참고**: `.cer` 파일이 키 체인 액세스에 있으면 이를 컴퓨터로 내보내서 `.p12` 인증서를 작성하십시오.

APNs 사용에 대한 자세한 정보는 [iOS Developer Library: Local and Push Notification Programming Guide ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1){: new_window}를 참조하십시오.

Push Notification 서비스 콘솔에서 APNs를 설정하려면 다음 단계를 완료하십시오.

1. Push Notification 서비스 콘솔에서 **구성**을 선택하십시오.
2. **모바일** 옵션을 선택하여 **APNs 알림 신임 정보** 양식의 정보를 업데이트하십시오.
3. 다음 옵션 중에서 선택하십시오.
	- **모바일** 옵션의 경우
		1. **샌드박스**(개발) 또는 **프로덕션**(배포)을 알맞게 선택한 후에 작성한 `p.12` 인증서를 업로드하십시오.
		  ![푸시 알림 콘솔 설정](images/wizard.jpg "모바일 탭 및 APN 푸시 인증 정보를 표시하는, 탐색 구성 옵션이 선택된 푸시 알림 콘솔")

		1. **비밀번호** 필드에서 `.p12` 인증서 파일과 연관된 비밀번호를 입력하고 **저장**을 클릭하십시오.
	- **웹** 옵션의 경우
		- Safari 푸시 섹션에서 필수 정보로 양식을 업데이트하십시오. 
		- **웹 사이트 이름**: 알림 센터에서 입력한 이름입니다.
		- **웹 사이트 푸시 ID**: 웹 사이트 푸시 ID에 대한 역 도메인 문자열로 업데이트하십시오. 예: web.com.acmebanks.www.
		- **웹 사이트 URL**: 푸시 알림에 등록될 웹 사이트의 URL을 입력하십시오. 예: https://www.acmebanks.com.
		- **허용 도메인**: 선택적 매개변수입니다. 사용자에게 권한을 요청하는 웹 사이트 목록입니다. URL은 쉼표로 구분된 값이어야 합니다. 이 값을 입력하지 않으면 웹 사이트 URL 값을 사용합니다. 
		- **URL 형식 문자열**: 알림을 클릭할 때 분석할 URL입니다. 예: ["https://www.acmebanks.com"]. 이 URL은 http 또는 https 체계를 사용해야 합니다.
		  -**Safari 웹 푸시 인증서**: .p12 인증서를 업로드하고 비밀번호를 제공하십시오.
4. **저장**을 클릭하십시오.	
![푸시 알림 콘솔](images/push_configure_safari.jpg "웹 옵션 페이지 필드")	

iOS 애플리케이션에 대한 서비스를 설정한 후에 [푸시 서비스 클라이언트 SDK를 설정](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)해야 합니다.


## Chrome 및 Firefox 브라우저의 경우 
{: #push_step2_chromefirefox}

1. Push Notifications 콘솔에서 **구성**을 선택하십시오.
2. 웹 탭을 선택하십시오.
	![웹 푸시 구성](images/webpush_configure.jpg "웹 사이트의 FCM API 키 및 URL을 정의하기 위한 웹 푸시 구성 창")
3. 푸시 알림을 수신하도록 등록할 웹 사이트의 URL과 FCM API 키를 구성하십시오.
4. **저장**을 클릭하십시오.
5. 서비스를 설정한 후에 [푸시 서비스 클라이언트 SDK를 설정](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3)해야 합니다.


