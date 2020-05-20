---

copyright:
  years: 2015, 2020
lastupdated: "2020-05-20"

keywords: push notification, push notifications, notifications, troubleshooting, service issues

subcollection: mobilepush

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:java: .ph data-hd-programlang='java'}
{:ruby: .ph data-hd-programlang='ruby'}
{:c#: .ph data-hd-programlang='c#'}
{:objectc: .ph data-hd-programlang='Objective C'}
{:python: .ph data-hd-programlang='python'}
{:javascript: .ph data-hd-programlang='javascript'}
{:php: .ph data-hd-programlang='PHP'}
{:swift: .ph data-hd-programlang='swift'}
{:reactnative: .ph data-hd-programlang='React Native'}
{:csharp: .ph data-hd-programlang='csharp'}
{:ios: .ph data-hd-programlang='iOS'}
{:android: .ph data-hd-programlang='Android'}
{:cordova: .ph data-hd-programlang='Cordova'}
{:xml: .ph data-hd-programlang='xml'}

# Troubleshoot service issues
{: #errors}

This topic guides you in identifying and resolving the likely error scenarios that you might encounter when using the {{site.data.keyword.mobilepushshort}} service.

## Resolving common push notification issues
{: #troubleshooting_notification_errors}

### You don't have permission to add the instance to any resource group in this account
{: #permission_issue}

**Explanation**: {{site.data.keyword.IBM_notm}} {{site.data.keyword.mobilepushshort}} service is now a Resource Controller (RC) based service. Instances should be created by using an RC. You might notice the following error if a default resource group is not in your account.

![Permission issue](images/RC_error.png "Screen capture showing permission error")

**User response**:  The admin must create a resource group for the user before creating an instance.

### The HyperText Transfer Protocol (HTTP) 301 Moved Permanently redirect status while accessing the service
{: #http_301_redirect}

**Explanation**: This error might occur if you are accessing the service by using the `http` protocol. {{site.data.keyword.mobilepushshort}} service requires the website to be accessed with the `https` protocol.

**User response**: We recommend you to access the service and the Swagger API through the `https` protocol, rather than `http`.

### A POST request returns a GET request for the same call
{: #Postman_issue}

**Explanation**: If a postman receives a 301 or 302 response code for a POST request, it automatically redirects to the GET request for the same call. The {{site.data.keyword.mobilepushshort}} service requires the website to be accessed with the `https` protocol, rather than `http`.

**User response**: It is recommended that you try connecting to the website by using `https`, from the browser.

### Internal server error occurred. Please contact admin. (Internal error code: PUSHD102E)
{: #troubleshooting_notification_internal}

**Explanation**: This error might occur if you have created a push instance before November 2015.  

**User response**: To resolve the issue, delete the push instance and create a new one. Note that when you delete the push instance, your tags are not be preserved.

### UnauthorizedRegistration
{: #troubleshooting_notification_unauth}

**Explanation**: Chrome Web Push does not work with Firebase Cloud Messaging (FCM) Keys. If you are unable to receive web push notifications on Chrome after moving to FCM from GCM, this is because the website was previously configured to work with GCM project and the new project is created in FCM. The generated tokens that identify the browser are cached by the Chrome browser.

**User response**: You can resolve this issue by removing the cookies and resetting the permissions of the browser. This would request for permissions to enable {{site.data.keyword.mobilepushshort}}. 

### Service workers are not supported in this browser
{: #troubleshooting_notification_service_workers}

**Explanation**: The SDK that was included as a part of `BMSPushSDK.js` using the service worker is not available. 

**User response**: It is recommended that you switch to a browser that supports the service worker. The supported versions of the browsers are Firefox version 49 or later and Chrome version 53 (64 bit) or later.

### Server Busy: The server is currently unable to handle the request. Try again later.
{: #troubleshooting_notification_server_busy}

**Explanation**: Users might notice the error while accessing the reports in the Monitoring page. This is an expected behavior when the number of messages that are sent is very high in the past 90 days.
 
**User response**: messageId based reports can be accessed through REST APIs. Refer "getMessageReport" in [ReST API docs](https://cloud.ibm.com/apidocs/push-notifications#api-documentation-for-push-notifications).

### SecurityError: The operation is insecure
{: #troubleshooting_notification_insecure}

**Explanation**:  You might see the error when enabling the web console in Firefox. Web push support in {{site.data.keyword.mobilepushshort}} service requires the website to be accessed with the `https` protocol, rather than `http`.

**User response**: It is recommended that you try connecting to the website by using `https`, from the browser.

## Resolving web push configuration errors
{: #troubleshooting_configuration_errors}

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

## Resolving {{site.data.keyword.mobilepushshort}} service error messages
{: #troubleshooting_service_errors}

The following {{site.data.keyword.mobilepushshort}} error messages are returned in response to ReST API requests.

Sample error response:

```
{
   "message": "Missing APNs credentials",
   "code":   "FPWSE0003E"
}
```
{: codeblock}

To obtain additional information about an error, search the docs for the related error code.

### FPWSE0001E
{: #error_fpwse0001e}

**Explanation**: The resource that you are trying to query, such as a tag or subscription, is not available on the server.

**User response**: Create the resource that was reported in the message. You can alternatively provide the correct identifier to query the resource.

### FPWSE0002E
{: #error_fpwse0002e}

**Explanation**: The resource that you are trying to create is already available on the server. The resource might be a tag, subscription, and so on.

**User response**: Create the resource with a different identifier.

### FPWSE0003E
{: #error_fpwse0003e}

**Explanation**: Prerequisite configuration for {{site.data.keyword.mobilepushshort}} service is not complete. You might be attempting to get Apple Push Notification service (APNs) credentials before they are configured.

**User response**: Ensure that {{site.data.keyword.mobilepushshort}} service has been configured with valid security certificates for the APNs. For more information, see [Obtaining your notification provider credentials](/docs/mobilepush?topic=mobilepush-push_step_1).

### FPWSE0004E
{: #error_fpwse0004e}

**Explanation**: The JSON body included in the request is not valid.

**User response**: Ensure that you use a valid JSON syntax in the request.

### FPWSE0005E
{: #error_fpwse0005e}

**Explanation**: The request to the {{site.data.keyword.mobilepushshort}} server is incorrect or incomplete because the JSON body does not contain the property values that are needed to complete the API request. For example, a password is not valid or a device token is missing.

**User response**: Review the message to learn which property value is missing or not valid and then provide the required information.

### FPWSE0006E
{: #error_fpwse0006e}

**Explanation**: The JSON body of the request has parameters that are not understood by the {{site.data.keyword.mobilepushshort}} server.

**User response**: Verify that the JSON body in the request follows the format of the request that is expected by the {{site.data.keyword.mobilepushshort}} server. For more information, see [ReST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: external}.

### FPWSE0007E 
{: #error_fpwse0007e}

**Explanation**: The request URL has a query string with unrecognized parameters. For example, if the request for deleting the subscription has parameters other than deviceId and tagName, this error might occur.

**User response**:  Verify that the JSON body in the request follows the format of the request that is expected by the {{site.data.keyword.mobilepushshort}} server. For more information, see [ReST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: external}.

### FPWSE0008E
{: #error_fpwse0008e}

**Explanation**: The request URL has a query string with missing required parameters. For example, the deviceId and tagName parameters might be missing from the request for deleting the subscription.

**User response**:  Verify that the JSON body in the request follows the format of the request that is expected by the {{site.data.keyword.mobilepushshort}} server. For more information, see [ReST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: external}.

### FPWSE0009E
{: #error_fpwse0009e}

**Explanation**: An attempt was made to send notifications but no devices are registered with the application.

**User response**: Ensure that devices have registered with the application before attempting to send notifications.

### FPWSE0010E
{: #error_fpwse0010e}

**Explanation**: The request that was submitted to the server resulted in an exception condition. One of the following conditions might have caused this error:
- An internal subsystem that {{site.data.keyword.mobilepushshort}} uses is not responding.
- The request resulted in an error condition that might not be handled by {{site.data.keyword.mobilepushshort}}.
- The {{site.data.keyword.mobilepushshort}} service requires attention from administrator.

**User response**: Retry the request. If the issue persists, contact IBM software support.

### FPWSE0011E
{: #error_fpwse0011e}

**Explanation**: The subscription for the tag already exists on the server. For example, when you create a subscription that exists.

**User response**: Create the subscription with a unique tag name.

### FPWSE0012E
{: #error_fpwse0012e}

**Explanation**: The subscription for the tag does not exist on the server. This error occurs when a request is submitted to retrieve or delete a subscription that does not exist.

**User response**: Use the correct tag name and device identifier in the request.

### FPWSE0013E
{: #error_fpwse0013e}

**Explanation**: The JSON payload in the request is not valid.

**User response**: Ensure that the JSON payload is valid.

### FPWSE0025E
{: #error_fpwse0025e}

**Explanation**: The server is currently unable to handle the request.

**User response**: Resubmit the request later.

### FPWSE1007E 
{: #error_fpwse1007e}

**Explanation**: The {{site.data.keyword.mobilepushshort}} service has been disabled for this application. This might be due to billing, or the app might have been disabled by the administrator.

**User response**: See the troubleshooting topics in the IBM Cloud Docs to check service status, review troubleshooting information, or for information about getting help.

### FPWSE1079E
{: #error_fpwse1079e}

**Explanation**: The offset value that was provided for the query operation is not valid.

**User response**: Ensure that the offset value is greater than or equal to zero.

### FPWSE1080E 
{: #error_fpwse1080e}

**Explanation**: The size value that was provided for the query operation is not valid.

**User response**: Ensure that the size value is greater than zero.
