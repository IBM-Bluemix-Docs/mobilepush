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

# Resolving {{site.data.keyword.mobilepushshort}} service error messages
{: #troubleshoot-service-errors}
{: troubleshoot}
The {{site.data.keyword.mobilepushshort}} service returns the following error messages in response to ReST API requests.

Sample error response:

```
{
   "message": "Missing APNs credentials",
   "code":   "FPWSE0003E"
}
```
{: codeblock}

To obtain additional information about an error, search the docs for the related error code.

## FPWSE0001E
{: #error_fpwse0001e}

When a resource is missing while running a query, FPWSE0001E error is displayed.
{: tsSymptoms}

The resource that you are trying to query, such as a tag or subscription, is not available on the server.
{: tsCauses}

Create the resource that was reported in the message. You can alternatively provide the correct identifier to query the resource.
{: tsResolve}

## FPWSE0002E
{: #error_fpwse0002e}

If you try to create a resource that is already available in the server, FPWSE0002E error is displayed.
{: tsSymptoms}

The resource that you are trying to create is already available on the server. The resource might be a tag, subscription, and so on.
{: tsCauses}

Create the resource with a different identifier.
{: tsResolve}

## FPWSE0003E
{: #error_fpwse0003e}

When the prerequisite configuration is not complete, FPWSE0003E error is displayed.
{: tsSymptoms}

Prerequisite configuration for {{site.data.keyword.mobilepushshort}} service is not complete. You might be attempting to get Apple Push Notification service (APNs) credentials before they are configured.
{: tsCauses}

Ensure that {{site.data.keyword.mobilepushshort}} service has been configured with valid security certificates for the APNs. For more information, see [Obtaining your notification provider credentials](/docs/mobilepush?topic=mobilepush-push_step_1).
{: tsResolve}

## FPWSE0004E
{: #error_fpwse0004e}

Invalid JSON body in a request displays FPWSE0004E error.
{: tsSymptoms}

The JSON body included in the request is not valid.
{: tsCauses}

Ensure that you use a valid JSON syntax in the request.
{: tsResolve}

## FPWSE0005E
{: #error_fpwse0005e}

When a request sent to {{site.data.keyword.mobilepushshort}} server is incorrect or incomplete, FPWSE0005E is displayed.
{: tsSymptoms}

The request to the {{site.data.keyword.mobilepushshort}} server is incorrect or incomplete because the JSON body does not contain the property values that are needed to complete the API request. For example, a password is not valid or a device token is missing.
{: tsCauses}

Review the message to learn which property value is missing or not valid and then provide the required information.
{: tsResolve}

## FPWSE0006E
{: #error_fpwse0006e}

When the JSON body of a request sent to {{site.data.keyword.mobilepushshort}} server is not understood by the server, FPWSE0006E is displayed.
{: tsSymptoms}

The JSON body of the request has parameters that are not understood by the {{site.data.keyword.mobilepushshort}} server.
{: tsCauses}

Verify that the JSON body in the request follows the format of the request that is expected by the {{site.data.keyword.mobilepushshort}} server. For more information, see [ReST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: external}.
{: tsResolve}

## FPWSE0007E 
{: #error_fpwse0007e}

The request URL for an operation has a query string with unrecognized parameters, resulting in FPWSE0007E error.
{: tsSymptoms}

The request URL has a query string with unrecognized parameters. For example, if the request for deleting the subscription has parameters other than deviceId and tagName, this error might occur.
{: tsCauses}

Verify that the JSON body in the request follows the format of the request that is expected by the {{site.data.keyword.mobilepushshort}} server. For more information, see [ReST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: external}.
{: tsResolve}

## FPWSE0008E
{: #error_fpwse0008e}

The request URL has a query string with missing required parameters, resulting in FPWSE0008E error.
{: tsSymptoms}

The request URL has a query string with missing required parameters. For example, the deviceId and tagName parameters might be missing from the request for deleting the subscription.
{: tsCauses}

Verify that the JSON body in the request follows the format of the request that is expected by the {{site.data.keyword.mobilepushshort}} server. For more information, see [ReST APIs](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: external}.
{: tsResolve}

## FPWSE0009E
{: #error_fpwse0009e}

When no devices are registered with the application, an attempt to send notification through the application results in FPWSE0009E error.
{: tsSymptoms}

An attempt was made to send notifications but no devices are registered with the application.
{: tsCauses}

Ensure that devices have registered with the application before attempting to send notifications.
{: tsResolve}

## FPWSE0010E
{: #error_fpwse0010e}

When a request submitted to the server, and the server responds with exception condition.
{: tsSymptoms}

The request that was submitted to the server resulted in an exception condition. One of the following conditions might have caused this error:
- An internal subsystem that {{site.data.keyword.mobilepushshort}} uses is not responding.
- The request resulted in an error condition that might not be handled by {{site.data.keyword.mobilepushshort}}.
- The {{site.data.keyword.mobilepushshort}} service requires attention from administrator.
{: tsCauses}

Retry the request. If the issue persists, contact IBM software support.
{: tsResolve}

## FPWSE0011E
{: #error_fpwse0011e}

When creating a subscription for the tag already exists on the server, results in FPWSE0011E error.
{: tsSymptoms}

The subscription for the tag already exists on the server. For example, when you create a subscription that exists.
{: tsCauses}

Create the subscription with a unique tag name.
{: tsResolve}

## FPWSE0012E
{: #error_fpwse0012e}

When a request is submitted to retrieve or delete a subscription that does not exist, the FPWSE0012E is displayed.
{: tsSymptoms}

The subscription for the tag does not exist on the server. This error occurs when a request is submitted to retrieve or delete a subscription that does not exist.
{: tsCauses}

Use the correct tag name and device identifier in the request.
{: tsResolve}

## FPWSE0013E
{: #error_fpwse0013e}

An invalid JSON payload results in this error.
{: tsSymptoms}

The JSON payload in the request is not valid.
{: tsCauses}

Ensure that the JSON payload is valid.
{: tsResolve}

## FPWSE0025E
{: #error_fpwse0025e}

When the server is currently unable to handle the current request, this error is displayed.
{: tsSymptoms}

The server is currently unable to handle the request.
{: tsCauses}

Resubmit the request later.
{: tsResolve}

## FPWSE1007E 
{: #error_fpwse1007e}

This error occurs when the {{site.data.keyword.mobilepushshort}} service has been disabled for the application.
{: tsSymptoms}

The {{site.data.keyword.mobilepushshort}} service has been disabled for this application. This might be due to billing, or the app might have been disabled by the administrator.
{: tsCauses}

See the troubleshooting topics in the IBM Cloud Docs to check service status, review troubleshooting information, or for information about getting help.
{: tsResolve}

## FPWSE1079E
{: #error_fpwse1079e}

When the offset value provided for the query operation is not valid, resulting in this error.
{: tsSymptoms}

The offset value that was provided for the query operation is not valid.
{: tsCauses}

Ensure that the offset value is greater than or equal to zero.
{: tsResolve}

## FPWSE1080E 
{: #error_fpwse1080e}

The size value provided for the query operation is not greater than zero.
{: tsSymptoms}

The size value that was provided for the query operation is not valid.
{: tsCauses}

Ensure that the size value is greater than zero.
{: tsResolve}
