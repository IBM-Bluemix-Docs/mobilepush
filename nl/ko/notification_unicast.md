---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 유니캐스트 알림
{: #notification_unicast}


유니캐스트 알림은 특정 디바이스 또는 사용자를 대상으로 하는 메시지입니다. 디바이스를 대상으로 하는 유니캐스트 알림에는 추가 설정이 필요하지 않으며 애플리케이션을 {{site.data.keyword.mobilepushshort}}에 사용할 수 있을 때 기본적으로 사용으로 설정됩니다.

그러나 사용자를 대상으로 하는 유니캐스트 알림에서는 {{site.data.keyword.mobilepushshort}}를 수신하도록 클라이언트 모바일 디바이스나 웹 브라우저 또는 Chrome 앱 및 확장 프로그램을 등록할 때 사용자 ID와 디바이스를 연관시켜야 합니다.   

일반적으로 클라이언트 애플리케이션은 제일 먼저 인증 주기를 실행하며 여기서 모바일 앱 사용자가 인증 서비스(예: [Mobile Client Access](docs/services/mobileaccess/index.html))에 대해 인증됩니다. 인증에 성공하면 인증된 사용자 ID가 푸시 디바이스 등록 API에 전달됩니다. 

REST API를 통해 유니캐스트 알림을 전송하려면 메시지 리소스에 게시할 때 deviceIds 또는 userIds가 제공되는지 확인하십시오.
