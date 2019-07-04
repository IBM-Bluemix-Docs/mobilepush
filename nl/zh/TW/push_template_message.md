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

# 參數化通知
{: #template_based_notifications}

藉由建立變數並在通知範本中呼叫它們，您可以參數化並傳送自訂通知。

您的通知範本可以：

 - 在通知中結合靜態及動態元素
 - 新增變數來個人化每個收件者的通知
 - 可以在通知中包含多個變數 

在起始設定期間，在應用程式碼中以 JSON 物件的形式傳遞變數：

    
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


定義變數之後，便可以在訊息範本中呼叫它們。

1. 在 {{site.data.keyword.mobilepushshort}} 主控台上，選取**訊息**標籤。

2. 選擇**傳送至**選項來編寫訊息。

3. 在**訊息**欄位中，編寫訊息。在訊息範本中呼叫已定義的變數。按一下**傳送**。

![訊息範本](images/message_template.png "訊息頁面，其中顯示「傳送至」欄位設定為「所有裝置」的訊息範本、包含有關使用者銀行帳戶餘額的訊息範例的「訊息」欄位，以及新增了 "key":"value" 屬性的「其他有效負載」欄位。")

您的自訂訊息將藉由提取變數資料來傳送：

![訊息範例](images/message_template_example.jpg "以訊息範本為基礎的通知範例")

附註：特性只會針對已選擇 `Advanced Plan` 的使用者啟用。在 {{site.data.keyword.mobilepushshort}} 服務主控台中選取**方案**，以便[升級](https://cloud.ibm.com/docs/account?topic=account-changing#changing)。

## 限制
{: #limitations}

 - 目前在 Safari 上不支援此特性。
 - 如果 iOS 上有應用程式被強制退出，通知範本中的變數可能無法運作。限制不在 SDK 控制範圍中，而是來自 iOS。

