---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 태그 기반 알림
{: #tag_based_notifications}
마지막 업데이트 날짜: 2017년 6월 30일
{: .last-updated}

태그 기반 알림은 특정 태그를 구독하는 모든 디바이스를 대상으로 하는 메시지입니다. 태그 기반 알림을 사용하면 제목 영역 또는 주제를 기반으로 알림을 구분할 수 있습니다. 알림 수신인은 관심있는 제목 또는 주제에 대한 알림일 경우에만 알림을 수신하도록 선택할 수 있습니다. 따라서 태그 기반 알림은 수신인을 구분할 수 있는 수단을 제공합니다. 이 기능을 사용하면 태그를 정의한 다음 태그별로 메시지를 전송 및 수신할 수 있는 기능을 사용할 수 있습니다. 태그를 구독하는 클라이언트 애플리케이션 인스턴스(모바일, 브라우저에 있거나 앱 또는 확장 프로그램으로서의 인스턴스)만 메시지의 대상입니다. 먼저 애플리케이션의 태그를 작성하고 태그 구독을 설정한 후 태그 기반 알림을 시작해야 합니다. REST API를 사용하는 태그 기반 알림을 전송하려면 메시지 리소스에 게시할 때 "tagNames"가 제공되는지 확인하십시오. 

태그를 정의한 다음 태그를 사용하여 메시지를 전송 및 수신할 수 있습니다. 먼저 애플리케이션에 대한 태그를 작성하고 구독을 작성한 다음 태그 기반 알림을 시작해야 합니다. [REST API](https://mobile.{DomainName}/imfpush/){: new_window}를 사용하여 태그 기반 알림을 전송하려면 메시지 리소스에 게시하는 중에 "tagNames"가 제공되는지 확인하십시오. 


## 태그 관리
{: #manage_tags}

{{site.data.keyword.mobilepushshort}} 콘솔을 사용하여 애플리케이션의 태그를 작성 및 삭제한 후에 태그 기반 알림을 시작합니다. 태그를 구독하는 디바이스에서 태그 기반 알림이 수신됩니다.


### 태그 작성
{: #create_tags}

태그 기반 알림은 특정 태그를 구독하는 모든 디바이스를 대상으로 하는 메시지입니다. 각 디바이스는 수에 관계 없이 태그를 구독할 수 있습니다.  

1. {{site.data.keyword.mobilepushshort}} 콘솔에서 **태그** 탭을 선택하십시오. 
1.  + **태그 작성** 단추를 클릭하십시오.    
   1. **이름** 필드에 태그의 이름을 입력하십시오. 예를 들어, "coupons"를 입력하십시오. 
   1. **설명** 필드에 태그 설명을 입력하십시오. 
   1. **저장**을 클릭하십시오.

1. **코드 스니펫** 영역에서 모바일 애플리케이션에 대한 플랫폼을 선택하십시오. 
1. 코드 스니펫을 수정하여 오류를 수정한 다음 각 태그의 코드 스니펫을 모바일 애플리케이션에 복사하십시오. 

### 태그 삭제
{: #delete_tags}

1. **태그** 탭에서 삭제할 태그를 선택하고 **삭제** 아이콘을 클릭하십시오.
1. **확인**을 클릭하십시오. 

태그가 삭제되면 그 구독자 및 디바이스를 포함한 해당 태그와 연관된 정보가 삭제됩니다. 태그가 더 이상 존재하지 않으므로 자동 구독 해지가 필요하지 않습니다. 클라이언트 측에서 추가 조치가 필요하지 않습니다.

### 태그 설명 편집
{: #edit_tags}

1. **태그** 탭에서 편집할 탭을 선택하십시오. 
1. **편집** 아이콘을 클릭하십시오. 
1. 태그 설명을 편집하고 **저장** 단추를 클릭하십시오. 

## 태그 가져오기
{: #get_tags}

태그는 모든 애플리케이션에 전송되는 일반 브로드캐스트와 달리 관심사를 기반으로 수신인에게 맞춤형 알림을 전송하는 방법을 제공합니다. {{site.data.keyword.mobilepushshort}} 콘솔의 태그 탭을 사용하여 태그를 작성하고 관리하거나 REST API를 사용할 수 있습니다. 코드 스니펫을 사용하여 모바일 애플리케이션에 대한 태그 구독을 관리 및 조회할 수 있습니다. 코드 스니펫을 사용하여 구독을 가져오고 태그를 구독하며 태그에서 구독을 해지하고 사용 가능한 태그 목록을 가져올 수 있습니다. 이러한 코드 스니펫을 모바일 애플리케이션에 복사하십시오. 


- Android의 경우, [Android에서 Push Notification 태그 가져오기](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app)의 `getTags` API 및 `getSubscriptions` API를 참조하십시오.

- Cordova의 경우, [Cordova에서 Push Notifications 태그 가져오기](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags)의 `retrieveAvailableTags()` API 및 `retrieveSubscriptions()` API를 참조하십시오.

- iOS의 경우, [Swift에서 Push Notifications 태그 가져오기](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags)의 `retrieveAvailableTagsWithCompletionHandler` API를 참조하십시오.

- 웹 브라우저의 경우, [웹 브라우저에서 Push Notifications 태그 가져오기](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags)의 `retrieveAvailableTags()` API를 참조하십시오.


## 태그 구독
{: #Subscribe_tags}

사용자의 디바이스가 태그 검색, 태그 구독, 구독 검색 및 태그에서 구독 해지를 할 수 있도록 하려면 다음 API를 사용하십시오. 

- Android의 경우, `getTags`, `subscribe`, `getSubscriptions` 및 `unsubscribeFromTags` API를 사용하십시오. [Android용 Push Notifications 태그 구독](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags)을 참조하십시오.

- Cordova의 경우, `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` 및 `unsubscribe()` API를 사용하십시오. [Cordova용 Push Notifications 태그 구독](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags)을 참조하십시오.

- iOS의 경우, `retrieveAvailableTagsWithCompletionHandler`, `subscribeToTags`, `retrieveSubscriptionsWithCompletionHandler` 및 `unsubscribeFromTags` API를 사용하십시오. [Swift용 Push Notifications 태그 구독](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags)을 참조하십시오.

- 웹 브라우저의 경우, `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` 및 `unSubscribe()` API를 사용하십시오. [웹 브라우저용 Push Notifications 태그 구독](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags)을 참조하십시오.

## 태그 기반 알림 사용
{: #using_tags}

태그 기반 알림은 특정 태그를 구독하는 모든 디바이스를 대상으로 하는 메시지입니다. 각 디바이스는 원하는 수만큼의 태그에 대해 구독이 가능합니다. 이 주제에서는 태그 기반 알림의 전송 방법에 대해 설명합니다. {{site.data.keyword.mobilepushshort}} 서비스 IBM Cloud 인스턴스에서 구독을 유지보수합니다. 태그가 삭제되면 태그 구독자와 디바이스를 비롯한 해당 태그와 연관된 모든 정보가 삭제됩니다. 이 태그가 더 이상 존재하지 않고 클라이언트측에서 추가 조치가 필요하지 않으므로 이 태그에 대해 자동 구독 해지 조치가 필요하지 않습니다. 

**태그** 화면에서 태그를 작성하십시오. 태그 작성 방법에 대한 정보는 [태그 작성](t_manage_tags.html)을 참조하십시오. 

1. **Push Notification** 콘솔에서 **알림 전송**을 클릭하십시오. 
1. **받는 사람** 드롭 다운 목록에서 **태그별 디바이스** 옵션을 선택하십시오. 
1. 사용하려는 태그를 검색하여 선택하십시오.
![알림 화면](images/tag_notification.jpg)
1. **메시지 텍스트** 필드에서 알림으로 구독자에게 전송될 텍스트를 입력하십시오. 
1. **전송**을 클릭하십시오. 
