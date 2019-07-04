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

# 参数化通知
{: #template_based_notifications}

您可以通过创建变量并在通知模板中调用这些变量来对定制通知进行参数化，然后发送这些通知。

通知模板可以 - 

 - 在通知中组合静态和动态元素
 - 通过添加变量来个性化发给每个收件人的通知
 - 可在通知中包含多个变量 

在初始化期间将变量作为应用程序代码中的 JSON 对象传递 -

    
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


定义变量后，即可在消息模板中进行调用。

1. 在 {{site.data.keyword.mobilepushshort}} 控制台上，选择**消息**选项卡。

2. 通过选择**发送至**选项来编写消息。

3. 在**消息**字段中，编辑您的消息。在消息模板中调用所定义的变量。单击**发送**。

![消息模板](images/message_template.png "消息页面，其中显示“发送至”字段设置为“所有设备”的消息模板、包含有关用户银行帐户余额的消息示例的“消息”字段，以及添加了 "key":"value" 属性的“其他有效内容”字段。")

通过访存变量数据来发送定制通知消息 -

![消息示例](images/message_template_example.jpg "基于消息模板的通知示例")

注：此功能仅对选择`高级套餐`的用户启用。在 {{site.data.keyword.mobilepushshort}} 服务控制台中选择**套餐**以进行[升级](https://cloud.ibm.com/docs/account?topic=account-changing#changing)。

## 限制
{: #limitations}

 - 目前，Safari 上不支持此功能
 - 如果在 iOS 上应用程序强制退出，那么通知模板中的变量可能不起作用。此限制不受 SDK 控制，而由 iOS 进行控制。

