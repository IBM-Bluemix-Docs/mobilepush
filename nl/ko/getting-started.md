---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 시작하기 튜토리얼
{: #getting-started-with-push}

이 {{site.data.keyword.mobilepushfull}} 시작하기 튜토리얼에서 Android 앱이 푸시 알림을 수신할 수 있도록 설정하고 기본 푸시 알림을 디바이스에 전송하는 프로세스를 연습합니다.
{:shortdesc}

<div id="prerequisites"></div>

## 시작하기 전에
{: #prereqs}

[IBM Cloud 계정](https://console.bluemix.net/registration/), {{site.data.keyword.mobilepushshort}} 서비스의 인스턴스 및 다음과 같은 도구와 요구사항이 필요합니다. 

  * Android API 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android helloPush 샘플 앱](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * Android Studio 또는 Gradle을 사용하여 설치된 [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} 및
  [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window} SDK

## 1단계: Android 디바이스용 {{site.data.keyword.mobilepushshort}} 인스턴스 구성

1. 샘플 `AndroidManifest.xml` 파일에서 패키지 이름을 복사하십시오.

2. FCM 앱을 작성하고 Android 앱의 패키지 이름을 추가하십시오. 
  1. [Firebase 콘솔](https://console.firebase.google.com){: new_window}에서 **프로젝트 추가**를 클릭해서
  프로젝트 이름을 제공하고 **프로젝트 작성**을 클릭하십시오.
  2. **Android 앱에 Firebase 추가**를 클릭해서 패키지 이름을 입력하고 **앱 등록**을 클릭하십시오. **계속 > 완료**를 클릭하여 다음 두 개의 프롬프트를 건너뛸 수 있습니다.  

3. FCM 신임 정보를 {{site.data.keyword.mobilepushshort}} 인스턴스에 추가하십시오. 
  1. Firebase 콘솔에서 **설정 > 프로젝트 설정 > 클라우드 메시징**으로 이동해서 서버 키 및 발신인 ID를 복사하십시오.
  2. {{site.data.keyword.Bluemix_notm}} 콘솔에서 사용자의 서비스 인스턴스에 대한 대시보드를 여십시오. 
  3. **관리 > 구성**을 클릭하십시오.
  4. **GCM/FCM 푸시 신임 정보** 필드에 발신인 ID 및 서버 키를 입력하십시오. 

## 2단계: Android 앱을 푸시 알림 전송에 사용

1. 프로젝트 레벨 `build.gradle` 및 모듈 레벨 `build.gradle` 파일을 구성하십시오. 

  * SDK 종속 항목을 프로젝트 레벨 `build.gradle` 파일에 추가하십시오. 
  
  ```
  dependencies {
  ........
  compile group: 'com.ibm.mobilefirstplatform.clientsdk.android',
      name: 'push',
      version: '3.+',
      ext: 'aar',
      transitive: true
  .......
	      }
  ```
  {: codeblock}

  * 다음 종속 항목을 모듈 레벨 `build.gradle` 파일에 추가하십시오. 
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * Google 플레이 서비스 종속 항목을 종속 항목 이후의 모듈 레벨 `build.gradle` 파일의 끝에 추가하십시오. 
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * 앱의 `AndroidManifest.xml` 파일에 다음 권한을 추가하십시오. 
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.USE_CREDENTIALS" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
```
  {: codeblock}
  
  * 활동에 대한 알림 의도 설정을 추가하십시오.  
  
  사용자가 알림 영역에서 수신한 알림을 클릭할 때 이 설정을 통해 앱이 시작됩니다. `<yourAndroidPackageName>`을 사용자의 앱에 사용된 앱 패키지 이름으로 대체하십시오. 
  
  ```
  <intent-filter>
  <action android:name="Your_Android_Package_Name.IBMPushNotification"/>
  <category android:name="android.intent.category.DEFAULT"/>
 	</intent-filter>
  ```
  {: codeblock}
  
  * `RECEIVE` 및 `REGISTRATION` 이벤트 알림에 대한 FCM 의도 서비스 및 의도 필터를 업데이트하십시오.
  
  ```
  <service android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushIntentService"
    	android:exported="true" >
    	<intent-filter>
     <action android:name="com.google.firebase.MESSAGING_EVENT" />
  </intent-filter>
  </service>
  <service
  android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPush"android:exported="true" >
  <intent-filter>
   <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
  </intent-filter>
  </service>
  ```
  {: codeblock}
  
2. Android Studio에서 앱을 열고 `google-services.json` 파일을 모듈 루트 디렉토리에 추가하십시오.

3. 코어 SDK 및 푸시 SDK를 초기화하십시오. 

초기화 코드를 배치하는 공통 위치는 Android 앱에서 기본 활동의 onCreate() 메소드입니다. 

```
// Initialize the SDK
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
... 여기서 `<bluemixRegionSuffix>`는 앱이 호스팅된 위치입니다. 다음 값 중에서 사용할 수 있습니다.

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

appGUID는 푸시 앱 GUID 값이며 clientSecret은 푸시 클라이언트 시크릿 값입니다. 

## 3단계: Android 디바이스를 {{site.data.keyword.mobilepushshort}} 인스턴스로 등록

1. 앱을 실행하십시오.

2. MFPPush.register() API를 사용하여 사용자 기반 알림을 사용할 수 있도록 디바이스를 등록하십시오. 

```
//Register the device to Push Notifications service instance
 push.registerDeviceWithUserId("userId",new MFPPushResponseListener<String>() {
 @Override
		public void onSuccess(String response) {
		//Handle successful device registration here
 }
 @Override
	    public void onFailure(MFPPushException ex) {
	    //Handle failure in device registration here
 }
 });
 ```
 {: codeblock}
 
 
 userId는 푸시 알림을 등록하기 위한 고유 사용자 ID 값을 전달하기 위해 사용됩니다. clientSecret 값도 제공하십시오.
 {: tip}
 
 ## 4단계: 기본 푸시 알림 전송
 
 1. {{site.data.keyword.Bluemix_notm}} 콘솔에서 사용자의 서비스 인스턴스에 대한 대시보드로 이동하십시오. 
 2. **관리 > 알림 전송**을 클릭하십시오.
 3. **받는 사람** 메뉴에서 Android 디바이스를 선택하십시오.
 4. 메시지를 입력하고 **전송**을 클릭하십시오.  
 
