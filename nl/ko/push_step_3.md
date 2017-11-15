---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 4단계: 서비스 클라이언트 SDK 설정
{: #push_step_3}
마지막 업데이트 날짜: 2017년 6월 27일
{: .last-updated}

[알림 신임 정보 획득](push_step_1.html) 및 [푸시 서비스 인스턴스 구성](push_step_2.html)을 했는지 확인하십시오. 그리고 푸시 알림을 등록, 구독 및 수신하는 데 Push Notifications 서비스를 사용하기 위해 애플리케이션을 설정해야 합니다.  

서비스 클라이언트 SDK를 설정하려면 애플리케이션 유형을 기준으로 다음 단계를 완료하십시오. 

## Android 애플리케이션
{: #push_step_3_Android}

Android 애플리케이션에서 사용자 디바이스에 푸시 알림을 수신하도록 설정할 수 있습니다. Android Studio는 필수 소프트웨어이며 이를 사용하여 Android 프로젝트를 빌드하는 것이 좋습니다. Android Studio에 대한 기본 지식이 반드시 필요합니다. 

[알림 제공자 신임 정보 획득](push_step_1.html)을 수행하여 FCM 프로젝트를 설정하고 신임 정보를 가져왔는지 확인하십시오. 

서비스에서 전송된 푸시 알림을 Android 앱이 수신할 수 있도록 하려면 [Push Notifications Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc)에 대한 단계를 완료하십시오.  

1. Android Studio에서 앱을 여십시오. [2단계: 신임 정보 획득](push_step_1.html)을 통해 작성한 `google-services.json` 파일을 Android 애플리케이션 모듈 루트 디렉토리에 복사하십시오. `google-service.json` 파일에 추가된 패키지 이름이 포함됩니다. 

    ![애플리케이션의 루트 디렉토리에 json 파일 추가](images/FCM_7.jpg)

2. Android 앱에 Firebase 추가 창에서 **계속**을 클릭하고 **완료**를 클릭하십시오. 
3. 애플리케이션을 빌드하고 실행하십시오. 빌드가 완료되면 `Gradle 빌드 완료` 메시지가 표시됩니다.
4. Gradle과 함께 클라이언트 푸시 SDK를 포함하십시오. 
	1. [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle) 파일을 구성하십시오. 
	2. [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest) 파일을 구성하십시오.
	3. `google-services.json` 파일을 Android 애플리케이션 모듈 루트 디렉토리에 추가하십시오. 
5. SDK를 초기화하십시오. [코어 SDK 및 푸시 SDK 초기화](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk)를 참조하십시오.
6. 애플리케이션을 빌드하십시오. 
7. 애플리케이션에서 디바이스 등록 단추를 클릭하거나 [푸시 Android SDK를 사용하여 서비스에 등록](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice)을 통해 Push Notifications 서비스에 등록하도록 선택할 수 있습니다.

다음 단계는 [알림 전송](push_step_4.html)입니다.


## Cordova 애플리케이션
{: #push_step_3_Cordova}

Cordova는 JavaScript, CSS 및 HTML을 사용하여 하이브리드 애플리케이션을 빌드하는 플랫폼입니다. Push Notifications 서비스는 Cordova 기반 iOS 및 Android 애플리케이션의 개발을 지원합니다. 

사용자의 디바이스에 푸시 알림을 수신하기 위해 Cordova 애플리케이션을 사용으로 설정하려면 [Cordova 플러그인 푸시 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)를 구성해야 합니다. 

Cordova 플러그인 푸시 SDK를 설정한 후에 다음 단계는 [알림 전송](push_step_4.html)입니다.


## iOS 애플리케이션
{: #push_step_3_iOS}

사용자의 디바이스에 {{site.data.keyword.mobilepushshort}}를 수신하기 위해 iOS 애플리케이션을 사용으로 설정하려면 [Push Notifications 서비스용 iOS SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application)를 구성해야 합니다.  

iOS SDK를 설정한 후에 다음 단계는 [알림 전송](push_step_4.html)입니다.


## 웹 브라우저
{: #push_step_3_web}

브라우저 애플리케이션이 푸시 알림을 수신하도록 사용으로 설정하려면 [Push Notifications 서비스용 웹 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md)를 구성해야 합니다. 

웹 SDK를 설정한 후에 다음 단계는 [알림 전송](push_step_4.html)입니다.
