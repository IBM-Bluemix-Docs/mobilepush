---

copyright:
  years: 2015, 2020
lastupdated: "2020-12-08"

keywords: push notifications, push notification, notifications, troubleshooting, service issues

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

# Resolving common push notification issues
{: #troubleshoot-common-issues}
{: troubleshoot}

## Permission issues
{: #permission_issue}

You don't have permission to add the instance to any resource group in this account
{: tsSymptoms}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.mobilepushshort}} service is now a Resource Controller (RC) based service. Instances should be created by using an RC. You might notice the following error if a default resource group is not in your account.
{: tsCauses}

![Permission issue](images/RC_error.png "Screen capture showing permission error")

The admin must create a resource group for the user before creating an instance.
{: tsResolve}

## HTTP issues
{: #http_301_redirect}

The HyperText Transfer Protocol (HTTP) 301 Moved Permanently redirect status while accessing the service
{: tsSymptoms}

This error might occur if you are accessing the service by using the `http` protocol. {{site.data.keyword.mobilepushshort}} service requires the website to be accessed with the `https` protocol.
{: tsCauses}

We recommend you to access the service and the Swagger API through the `https` protocol, rather than `http`.
{: tsResolve}

## Postman issues
{: #Postman_issue}

A POST request returns a GET request for the same call
{: tsSymptoms}

If a postman receives a 301 or 302 response code for a POST request, it automatically redirects to the GET request for the same call. The {{site.data.keyword.mobilepushshort}} service requires the website to be accessed with the `https` protocol, rather than `http`.
{: tsCauses}

It is recommended that you try connecting to the website by using `https`, from the browser.
{: tsResolve}

## Internal server error
{: #troubleshooting_notification_internal}

Internal server error occurred. Please contact admin. (Internal error code: PUSHD102E)
{: tsSymptoms}

This error might occur if you have created a push instance before November 2015.  
{: tsCauses}

To resolve the issue, delete the push instance and create a new one. Note that when you delete the push instance, your tags are not be preserved.
{: tsResolve}

## UnauthorizedRegistration
{: #troubleshooting_notification_unauth}

Unauthorized Registration
{: tsSymptoms}

Chrome Web Push does not work with Firebase Cloud Messaging (FCM) Keys. If you are unable to receive web push notifications on Chrome after moving to FCM from GCM, this is because the website was previously configured to work with GCM project and the new project is created in FCM. The generated tokens that identify the browser are cached by the Chrome browser.
{: tsCauses}

You can resolve this issue by removing the cookies and resetting the permissions of the browser. This would request for permissions to enable {{site.data.keyword.mobilepushshort}}. 
{: tsResolve}

## Supported Browsers
{: #troubleshooting_notification_service_workers}

Service workers are not supported in this browser
{: tsSymptoms}

The SDK that was included as a part of `BMSPushSDK.js` using the service worker is not available. 
{: tsCauses}

It is recommended that you switch to a browser that supports the service worker. The supported versions of the browsers are Firefox version 49 or later and Chrome version 53 (64 bit) or later.
{: tsResolve}

## Server Busy
{: #troubleshooting_notification_server_busy}

The server is currently unable to handle the request. Try again later.
{: tsSymptoms}

Users might notice the error while accessing the reports in the Monitoring page. This is an expected behavior when the number of messages that are sent is very high in the past 90 days.
{: tsCauses}
 
messageId based reports can be accessed through REST APIs. Refer "getMessageReport" in [ReST API docs](https://cloud.ibm.com/apidocs/push-notifications#api-documentation-for-push-notifications).
{: tsResolve}

## Security Error
{: #troubleshooting_notification_insecure}

SecurityError: The operation is insecure.
{: tsSymptoms}

You might see the error when enabling the web console in Firefox. Web push support in {{site.data.keyword.mobilepushshort}} service requires the website to be accessed with the `https` protocol, rather than `http`.
{: tsCauses}

It is recommended that you try connecting to the website by using `https`, from the browser.
{: tsResolve}

