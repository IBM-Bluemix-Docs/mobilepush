---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 플랫폼 기반 알림
{: #notification_platform}


특정 디바이스 플랫폼에 도달하도록 알림의 대상을 설정할 수 있습니다. 예를 들어, 모든 Android 사용자 또는 Google Chrome 사용자에게만 알림을 전송할 수 있습니다. REST API를 사용하는 플랫폼 기반 알림을 전송하려면 메시지 리소스에 게시할 때 대상 플랫폼이 제공되는지 확인하십시오. 플랫폼을 어레이로 지정하십시오. 지원되는 플랫폼은 다음과 같습니다.

* A(Apple)
* G(Google)
* WEB_CHROME(Google Chrome 브라우저 웹 푸시)
* WEB_FIREFOX(Mozilla Firefox 브라우저 웹 푸시)
* WEB_SAFARI(Safari 브라우저 웹 푸시)
* APPEXT_CHROME(Google Chrome 앱 및 확장 프로그램)
