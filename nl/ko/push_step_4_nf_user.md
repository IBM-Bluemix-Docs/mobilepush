---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 사용자 기반 알림
{: #user_based_notifications}
마지막 업데이트 날짜: 2017년 5월 22일
{: .last-updated}

사용자 ID 기반 {{site.data.keyword.mobilepushshort}}는 사용자 정의된 메시지를 사용하는 모바일 앱 사용자가 대상입니다. 사용자 기반 알림에서는 사용자의 환경 설정을 기반으로 특정 개인에게 알림을 전송하도록 선택할 수 있습니다.

## 사용자 ID를 사용하여 디바이스 등록
{: #register_device_wh_userid}

사용자 ID로 대상이 지정되는 푸시 알림을 사용하려면 사용자 ID 필드를 설정하여 디바이스를 등록해야 합니다.     

애플리케이션에서 디바이스 등록 API에 제공하는 모든 문자열이 사용자 ID가 될 수 있습니다. 일반적으로, 모바일 애플리케이션은 먼저 인증 주기를 실행하며, 여기서 모바일 앱 사용자는 인증 서비스(예: [{{site.data.keyword.amafull}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/docs/services/mobileaccess/index.html){: new_window})에 대해 인증됩니다. 인증에 성공하면 인증된 사용자 ID가 푸시 디바이스 등록 API에 전달됩니다.  

사용자 ID 기반 알림에 등록하려면 다음 단계를 완료하십시오. 

- [Android 애플리케이션 등록](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [iOS 애플리케이션 등록](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Cordova 애플리케이션 등록](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [웹 애플리케이션 등록](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## 사용자 ID 기반 알림 사용
{: #using_userid}

사용자 ID 기반 알림은 특정 사용자를 대상으로 하는 알림 메시지입니다. 하나의 사용자에 여러 디바이스를 등록할 수 있습니다. 다음 단계는 사용자 ID 기반 알림을 전송하는 방법에 대해 설명합니다. 

1. **Push Notification** 콘솔에서 **알림 전송** 옵션을 선택하십시오. 
1. **받는 사람** 옵션 목록에서 **사용자 ID**를 선택하십시오. 
1. **사용자 ID** 필드에서 사용하려는 사용자 ID를 검색한 후 **+추가**를 클릭하십시오. ![알림 화면](images/user_notification.jpg)
1. **메시지** 필드에 알림에서 전송할 텍스트를 입력하십시오. 
1. **전송**을 클릭하십시오. 


## 사용자 로그인과 로그아웃 동기화 
{: #sync_login_logout}

사용자가 로그인한 경우에만 알림을 보내도록 선택할 수 있습니다.  

예를 들면, 직장에서 팀의 구성원이 공유하는 디바이스를 고려하고, 특정 사용자를 지정할 필요가 있습니다. 이와 같은 유스 케이스에서는 사용자 로그인/로그아웃 시퀀스가 있습니다. 이러한 인증 메커니즘을 사용하면 애플리케이션에서 애플리케이션 현재 사용자의 ID를 추적할 수 있습니다. 이로 인해 특정 사용자를 대상으로 하는 알림을 항상 해당 사용자만 수신할 수 있습니다. 로그인한 후 로그인한 사용자의 사용자 ID를 전달하여 디바이스 등록 API를 호출하십시오. 마찬가지로 로그아웃하기 전에 디바이스 `unregistration` API를 호출하십시오. 로그인과 로그아웃에서 이러한 푸시 API의 시퀀스를 지정하면 특정 사용자를 대상으로 작성된 알림이 해당 사용자에게만 전송됩니다. 
