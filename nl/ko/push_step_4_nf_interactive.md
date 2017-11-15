---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 대화식 및 자동 알림  
{: #interactive-notifications}
마지막 업데이트 날짜: 2017년 5월 22일
{: .last-updated}

대화식 알림을 사용하면 애플리케이션을 열지 않고 알림에 응답할 수 있습니다. 대화식 알림이 도착하면 디바이스에 알림 메시지와 함께 조치 단추가 표시됩니다.  

**참고:** 대화식 알림은 버전 8 이하의 iOS 디바이스에서는 지원되지 않습니다.  

## 대화식 알림 전송
{: #send_interactive_notifications}

Push Notifications 콘솔을 사용하거나 [REST API 문서](push_restapi.html)를 사용하여 대화식 알림을 전송할 수 있습니다. 

{{site.data.keyword.mobilepushshort}} 콘솔에서 다음을 수행하십시오. 

1. 알림 탭에서 **알림 전송**을 클릭하십시오.  
2. 알림 수신인을 선택하고 **다음**을 클릭하십시오.  
3. 알림 작성 페이지에서 유형을 기본 또는 혼합으로 설정하고 고급 옵션 탭에서 카테고리 값을 지정하여 대화식 푸시를 전송할 수 있습니다.  

## 대화식 알림 처리 
{: #handle_interactive_notifications}

- iOS의 경우, [Swift 애플리케이션에서 대화식 알림 사용 및 처리](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications)를 완료하십시오.
- Cordova의 경우, [Cordova 애플리케이션에서 대화식 알림 사용 및 처리](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications)를 완료하십시오.
- Android의 경우, [Android 애플리케이션에서 대화식 알림 사용 및 처리](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications)를 완료하십시오.


## iOS의 자동 알림 처리
{: #send_silent_notifications_for_ios}

자동 알림은 디바이스 화면에 표시되지 않으며 백그라운드에서 애플케이션에 수신되지 않습니다. 자세한 정보는 [iOS 디바이스에서 자동 알림](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification)을 참조하십시오.
