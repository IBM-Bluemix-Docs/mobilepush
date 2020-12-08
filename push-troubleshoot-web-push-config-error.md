---

copyright:
  years: 2015, 2020
lastupdated: "2020-12-08"

keywords: push notifications, push notification, notifications, troubleshooting, service error messages

subcollection: mobilepush

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Resolving web push configuration errors
{: #troubleshoot-web-push-config-errors}
{: troubleshoot}

You can diagnose web push configuration-related errors by going through the `BMSPushSDK.js` file. The file contains information on the failure. 

To parse an error returned in the callback, consider the following sample code:

```
function showStatus(response) {
 if(response.statusCode == 200 || response.statusCode == 201) {
   		document.getElementById("status").innerHTML = "Response is " + response.response;
   	}
   	else if(response.statusCode == 0) {
  		if(response.response) {
  			document.getElementById("status").innerHTML = response.response;	
    		}
    		else {
    			document.getElementById("status").innerHTML = "There is a possible CORS or access issue while attempting the request.";	
   		}   		
   	}
   	else {
   		document.getElementById("status").innerHTML = "Response is " + response.response + " with the error " 
		+ response.error + " and the status code " + response.statusCode;
   	}
 	}
```
{: codeblock}

- If the `applicationId` is incorrectly configured, the initial request to {{site.data.keyword.mobilepushshort}} service fails, hence the statusCode is set to zero (0).
- A status code of 200 or 201 denotes a successful response.
- In case the `clientSecret` is invalid. A 401 response will be set on the statusCode. The `response.reponse` element contains description of the error.

