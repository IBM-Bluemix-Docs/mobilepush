---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 브로드캐스트 알림 
{: #broadcast_notifications}

브로드캐스트 알림은 모바일 디바이스, 브라우저에 설치되거나 Chrome 앱 또는 확장 프로그램 인스턴스로 구현되고 {{site.data.keyword.mobilepushshort}} 서비스를 사용할 수 있도록 구성된 애플리케이션의 모든 인스턴스를 대상으로 전송되는 메시지입니다. 브로드캐스트 알림은 {{site.data.keyword.mobilepushshort}}가 사용으로 설정된 애플리케이션에서 기본적으로 사용됩니다.

클라이언트 애플리케이션이 {{site.data.keyword.mobilepushshort}} 서비스에 등록되면 브로드캐스트를 수신할 수 있습니다. {{site.data.keyword.mobilepushshort}} 서비스가 사용 가능하도록 설정된 애플리케이션에는 Push.ALL 태그에 대한 구독이 사전 정의되어 있으며 서버에서 이 태그를 사용하여 알림 메시지를 모든 디바이스에 브로드캐스트합니다. REST Push API를 사용하는 브로드캐스트 알림을 전송하려면 메시지 리소스에 게시할 때 "대상"은 빈 JSON 파일이어야 합니다.
