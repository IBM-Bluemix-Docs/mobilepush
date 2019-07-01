---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, sending a notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 5단계: 알림 전송
{: #push_step_4}

애플리케이션을 개발한 후에는 기본 푸시 알림을 전송할 수 있습니다.

기본 푸시 알림을 전송하려면 다음 단계를 완료하십시오.

1. **메시지**를 선택하고 **받는 사람** 옵션을 선택하여 메시지를 작성하십시오. 지원되는 옵션은 **태그별 디바이스**, **디바이스 ID**, **사용자 ID**, **Android 디바이스**, **iOS 디바이스**, **웹 알림**, **Chrome 앱 및 확장기능**, **Chrome 브라우저**, **Firefox**, **Safari** 및 **모든 디바이스**입니다.
**참고**: **모든 디바이스** 옵션을 선택하는 경우 {{site.data.keyword.mobilepushshort}}를 구독하는 모든 디바이스가 알림을 수신합니다.
	
    ![알림 화면](images/tag_notification.jpg "받는 사람, 메시지 및 추가 페이로드 필드를 표시하는 알림 전송 화면")

2. **메시지** 필드에 메시지를 작성하십시오. 필요에 따라 선택적 옵션을 구성하도록 선택하십시오.
3. **전송**을 클릭하십시오.
3. 디바이스 또는 브라우저가 알림을 수신했는지 확인하십시오.

다음 스크린샷은 Android 디바이스의 포그라운드에서 푸시
알림을 처리하는 경보 상자를 표시합니다.

![Android의 포그라운드 푸시 알림](images/Android_Screenshot.jpg "테스트 알림이 있는 경보 상자")

다음 스크린샷은 Android의 백그라운드에 있는 푸시 알림을 보여줍니다.

![Android의 백그라운드 푸시 알림](images/background.jpg "Android 디바이스의 푸시 알림")

## 선택적 Android 설정 
{: #push_step_4_Android}

Android 디바이스에 알림을 전송하기 위해 {{site.data.keyword.mobilepushshort}} 설정을 추가로 사용자 정의할 수 있습니다. 

![Android 사용자 정의 설정](images/android_custom_settings.jpg "푸시 알림 사용자 정의 설정 페이지")

다음과 같은 선택적 사용자 정의 옵션이 지원됩니다.

- 접기 키: 접기 키는 알림에 첨부됩니다. 디바이스가 오프라인 상태일 때 접기 키가 동일한 여러 개의 알림이 순차적으로 도착하는 경우 해당 알림은 접혀 있습니다. 디바이스가 온라인 상태가 되면 FCM 서버에서 알림을 수신하고 동일한 접기 키가 있는 최신 알림만 표시합니다. 접기 키가 설정되어 있지 않는 경우에는 나중에 전달할 수 있도록 새 메시지와 이전 메시지가 모두 저장됩니다.
- 사운드: 알림을 수신할 때 재생되는 사운드 클립을 표시합니다. 기본값 또는 앱에 번들링된 사운드 리소스의 이름을 지원합니다.
- 아이콘: 알림에 대해 표시할 아이콘의 이름을 지정합니다. 클라이언트 애플리케이션에서 `res/drawable` 폴더의 아이콘을 패키징했는지 확인하십시오.
- 우선순위: 메시지에 전달 우선순위를 지정하기 위한 옵션을 지정합니다. 
	- 우선순위 `high` 또는 `max`는 heads-up 알림이 됩니다.
	- 우선순위 `low` 또는 `default`는 휴면 디바이스에서 네트워크 연결을 열지 않습니다. 
	- 우선순위 `min`은 자동 알림입니다.
- 가시성: 알림 가시성 옵션을 `public` 또는 `private`로 설정하도록 선택할 수 있습니다. 
	- `private` 옵션은 공용 보기를 제한하며, 사용자는 디바이스가 핀 또는 패턴으로 보호되고 알림 설정이 **민감한 알림 컨텐츠 숨기기**로 설정된 경우에 이를 사용하도록 선택할 수 있습니다. 가시성이 `private`로 설정되면 `redact` 필드가 언급되어야 합니다. `redact` 필드에 지정된 컨텐츠만 디바이스의 보안 잠금 화면에 나타납니다. 
	- `public` 옵션은 알림을 누구나 읽을 수 있도록 렌더링합니다.
- 유효 기간: 이 값은 초 단위로 설정됩니다. 이 매개변수가 지정되지 않은 경우 FCM 서버는 메시지를 4주 동안 저장하며 이를 전달하려 시도합니다. 4주 후에 유효성이 만료됩니다. 가능한 값 범위는 0 - 2,419,200초입니다.
- 유휴 시 지연: 다음 값 중에서 설정할 수 있습니다.
	- `True`는 디바이스가 유휴 상태인 경우 알림을 전달하지 않도록 FCM 서버에 지시합니다. 
	- `False`는 디바이스가 유휴 상태인 경우에도 알림 전달을 보장합니다.
- 동기화: 이 옵션을 `true`로 설정하면 등록된 모든 디바이스 간에 알림이 동기화됩니다. 하나의 사용자 이름을 갖는 사용자에게 동일한 애플리케이션이 설치된 여러 개의 디바이스가 있는 경우, 하나의 디바이스에서 알림을 읽으면 나머지 디바이스에서 해당 알림이 삭제됩니다. 사용자 ID를 사용하여 {{site.data.keyword.mobilepushshort}} 서비스에 등록한 경우에만 이 옵션이 작동합니다.
- 추가 페이로드: 알림에 대한 사용자 정의 페이로드 값을 지정합니다.
- 펼치기 가능 알림: 더 많은 정보가 있는 알림을 펼치는 옵션을 고객에게 제공하고, 기본 알림은 알림이 접힌 상태로 표시됩니다. 지원되는 옵션은 다음과 같습니다.
	- 큰 그림 알림: 알림이 확장되면 그림을 포함하도록 선택할 수 있습니다. 그림에 대한 제목 텍스트 및 URL을 반드시 제공하십시오.
	- 큰 텍스트 알림: 제목이 있는 추가 텍스트를 포함하도록 선택할 수 있습니다. 큰 텍스트 메시지 및 제목 텍스트 정보가 제공되는지 확인하십시오.
	- 받은 편지함 스타일 알림: 받은 편지함 알림 스타일로 알림을 전송할 수 있습니다. 제목 텍스트를 제공하고 행에 메시지를 입력하십시오.	 

## 선택적 iOS 설정 
{: #push_step_4_ios}

iOS 디바이스에 알림을 전송하기 위해 {{site.data.keyword.mobilepushshort}} 설정을 사용자 정의할 수 있습니다. 다음과 같은 선택적 사용자 정의 옵션이 지원됩니다.

- **배지**: 애플리케이션 배지에 표시되는 숫자를 나타냅니다. 기본값은 영(0)이며, 이 값은 배지를 표시하지 않습니다. 
- **사운드**: 알림을 수신할 때 재생되는 사운드 클립을 표시합니다. 기본값 또는 앱에 번들링된 사운드 리소스의 이름을 지원합니다.
- **추가 페이로드**: 알림에 대한 사용자 정의 페이로드 값을 지정합니다.

[대화식 알림](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications) 및 [리치 미디어 알림](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications)을 사용하도록 선택할 수도 있습니다.

## 전달된 알림에 대한 모니터링 
{: #push_step_4_monitor}

{{site.data.keyword.mobilepushshort}} 서비스는 발송된 메시지의 상태를 확인하는 데 사용하도록 모니터링 유틸리티를 제공합니다. 모니터링 유티리티를 구성하려면 다음 옵션 중에서 완료하십시오.

- [Android 애플리케이션용 모니터링 사용](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
- [iOS 애플리케이션용 모니터링 사용](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
