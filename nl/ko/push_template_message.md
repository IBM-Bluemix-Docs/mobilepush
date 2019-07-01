---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, parameterize notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 알림 매개변수화
{: #template_based_notifications}

변수를 작성하고 알림 템플리트에서 이를 호출하여 사용자 정의 알림을 매개변수화하고 전송할 수 있습니다.

알림 템플리트는 다음과 같은 기능을 제공할 수 있습니다.

 - 알림의 정적 및 동적 요소 결합
 - 변수 추가를 통한 각 수신인별 알림 개인화
 - 알림에 여러 변수 포함 가능 

초기화 중에 애플리케이션 코드에 변수를 JSON 오브젝트로서 전달하십시오.

    
   ```
    MFPPushNotificationOptions options = new MFPPushNotificationOptions();

    JSONObject tempValue = new JSONObject();
        try {
        
		tempValue.put("username",userName);
        
        tempValue.put("amountSpent",amount);
		
        tempValue.put("currency",currency);
		
        tempValue.put("avilableBalance",balance);
        
		} catch (JSONException e) {
            e.printStackTrace();
        }
        options.setPushVariables(tempValue); 
	   
	   push = MFPPush.getInstance();

       push.initialize(getApplicationContext(),appGuid,clientSecret,options);
   ```
{: codeblock}


변수가 정의되고 나면 이를 메시지 템플리트에서 호출할 수 있습니다.

1. {{site.data.keyword.mobilepushshort}} 콘솔에서 **메시지** 탭을 선택하십시오.

2. **받는 사람** 옵션을 선택하여 메시지를 작성하십시오.

3. **메시지** 필드에 메시지를 작성하십시오.  메시지 템플리트에서 정의된 변수를 호출하십시오. **전송**을 클릭하십시오.

![메시지 템플리트](images/message_template.png "받는 사람 필드가 모든 디바이스로 설정되고 메시지 필드가 사용자의 은행 계정 잔고에 대한 예제 메시지로 설정되고 추가 페이로드 필드에 "key":"value" 속성이 추가된 메시지 템플리트를 표시하는 메시지 페이지")

변수 데이터를 페치하여 사용자 정의 알림 메시지가 전송됩니다.

![메시지 예제](images/message_template_example.jpg "메시지 템플리트를 기반으로 하는 예제 알림")

참고: 이 기능은 `고급 플랜`을 선택한 사용자만 사용할 수 있습니다. [업그레이드](https://cloud.ibm.com/docs/account?topic=account-changing#changing)하려면 {{site.data.keyword.mobilepushshort}} 서비스 콘솔에서 **플랜**을 선택하십시오.

## 제한사항
{: #limitations}

 - 현재 이 기능은 Safari에서 지원되지 않습니다.
 - 앱이 iOS에서 강제 종료되는 경우에는 알림 템플리트의 변수가 작동하지 않을 수 있습니다. 이 제한사항은 SDK의 문제가 아니라 iOS의 문제입니다.

