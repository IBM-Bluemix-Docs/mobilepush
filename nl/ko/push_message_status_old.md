---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 메시지 알림 전달 상태
{: #tag_based_notifications}
마지막 업데이트 날짜: 2017년 8월 21일
{: .last-updated}


{{site.data.keyword.mobilepushshort}} 서비스를 사용하면 서비스에 제출된 모든 알림의 상태를 볼 수 있습니다.  

제출된 메시지의 상태는 다음 항목 중 하나일 수 있습니다. 

- **승인됨**: Push Notifications 서비스가 메시지 전달을 승인했습니다. 
- **처리 중**: 메시지가 알림 제공자 게이트웨이에 디스패치되기 위해 처리되는 중입니다. 처리 중인 알림은 **처리 실패** 상태와 함께 실패를 리턴할 수도 있습니다. 
- **디스패치 중**: 알림 제공자(APN, FCM 또는 웹)가 알림을 수신했으며 곧 알림이 디스패치됩니다. 디스패치 프로세스 중인 알림은 **디스패치 실패** 상태와 함께 실패를 리턴할 수도 있습니다. 
- **디스패치됨**: 알림 제공자가 알림을 디스패치했습니다. 
- **알 수 없음**: 알림의 상태를 판별할 수 없습니다. 

{{site.data.keyword.mobilepushshort}} 서비스 메시지 탭은 알림 상태를 표시합니다. 

![알림 상태](images/notification_status_new.png)

1. **보기** 옵션은 디스패치된 알림의 전달 상태를 표시합니다. 다음 요소를 기반으로 정보를 볼 수 있습니다. 

 - 카테고리: 모두, 모바일, 웹<!---and HTTP--->. 
 - 메시지 상태: 전송됨, 열람됨, 열림 및 올바르지 않음.  

![알림 상태](images/message_delivery_status_new.png)

2. **자세한 메시지 전달 상태**를 가져오려면 **옵션**을 클릭하십시오. 드롭 다운 메뉴에서 `Device Id` 또는 `User Id`를 선택하여 자세한 전달 상태를 추적할 수 있습니다. 특정 사용자 또는 디바이스의 자세한 상태를 페치할 수 있습니다. 

![자세한 상태](images/detailed_message_delivery.png)


이 서비스는 어느 시점에서든 90일 기간 내에서 사용 가능한 최신 10개의 메시지만을 표시합니다. 

**참고**: 이 기능은 `Advanced Pricing Plan`을 선택한 사용자만 사용할 수 있습니다. [업그레이드](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)하려면 {{site.data.keyword.mobilepushshort}} 서비스 콘솔에서 **플랜**을 선택하십시오. 
