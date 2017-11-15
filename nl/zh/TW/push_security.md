----

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Push Notifications 的安全 
{: #overview-push}
前次更新：2017 年 6 月 27 日
{: .last-updated}


{{site.data.keyword.mobilepushshort}} API 透過兩種類型的密碼來進行保護：

- **appSecret**：`appSecret` 會保護一般由後端應用程式所呼叫的 API（例如，傳送 {{site.data.keyword.mobilepushshort}} 的 API，以及配置設定的 API）。
- **clientSecret**：`clientSecret` 會保護一般由行動用戶端應用程式所呼叫的 API。只有一個 API 與使用需要此 `clientSecret` 的相關聯 UserId 登錄裝置有關。從行動用戶端呼叫的其他 API 都不需要 `clientSecret`。 

連結應用程式與 {{site.data.keyword.mobilepushshort}} 服務時，會將 `appSecret` 及 `clientSecret` 配置給每個服務實例。請參閱 [REST API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://mobile.{DomainName}/imfpush/) 文件，以取得如何傳遞密碼以及針對哪些 API 傳遞的相關資訊。

## appSecret 
{: #push-api-rest-secret}

應用程式連結至 {{site.data.keyword.mobilepushshort}} 時，服務會產生 appSecret（唯一金鑰）並透過回應標頭進行傳遞。如果您使用的是 IBM {{site.data.keyword.mobilepushshort}} for Bluemix Rest API，請使用 REST API 參考資料來取得所需保護之 API 的資訊。如需資訊，請參閱 [Push REST API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://mobile.{DomainName}/imfpush/){: new_window}。

要求標頭必須包含 appSecret。如果沒有，則伺服器會傳回「401 未獲授權」的錯誤碼。將 {{site.data.keyword.mobilepushshort}} 新增至應用程式時，會建立特定的 AppID。在回應中有一個稱為 appSecret 的標頭，它用來建立標籤或傳送訊息。作業是透過型錄或樣板中的服務進行。

若要取得 appSecret 值，請執行下列動作：

1. 按一下連結至 Push 服務的 *app-name*。
2. 按一下**顯示認證**鏈結，以顯示 appSecret (AppID)。

**顯示認證**畫面會顯示 AppSecret 的相關資訊：
```
	{
    "imfpush_Dev": [
   {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://imfpush.ng.bluemix.net/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.ng.bluemix.net/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**附註**：只有在使用 userId 欄位登錄或更新裝置時，才需要舊版應用程式來傳遞 clientSecret。行動及瀏覽器用戶端所呼叫的所有其他 API 都不需要 clientSecret。這些舊應用程式可以選擇性地繼續使用 clientSecret 進行裝置登錄或更新呼叫。不過，強烈建議所有用戶端 API 呼叫都強制執行 clientSecret 檢查。若要在現有應用程式中強制執行此作業，則有一個已發佈的新 `verifyClientSecret` API 可供使用。對於新的應用程式，將會對所有用戶端 API 呼叫強制執行 clientSecret 檢查，而且使用 `verifyClientSecret` API 無法變更此行為。

預設只會在新的應用程式中強制執行用戶端密碼驗證。同時容許現有及新的應用程式，以使用 verifyClientSecret REST API 來啟用或停用用戶端密碼驗證。建議您強制執行用戶端密碼驗證，以避免向可能知道 applicationId 及 deviceId 的使用者公開裝置。

請確定 `clientSecret` 保持機密，而且絕不寫在行動應用程式中。您可以利用各種應用程式起始設定型樣，在應用程式運行環境期間動態地取回 `clientSecret`。序列圖會概述這類可能的型樣。
![Enable_Push](images/init_client_secret.jpg) 



