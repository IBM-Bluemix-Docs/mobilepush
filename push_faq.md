---

copyright:
  years: 2015, 2020
lastupdated: "2020-07-01"

keywords: push notification, push notifications, notifications, faq, frequently asked questions, rest api filter, Xcode

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

# Frequently asked questions 
{: #faq}

## Why do my tokens get invalidated?
{: #faq-tokens}	

For device, browser, Chrome Apps & Extensions registrations, the {{site.data.keyword.mobilepushshort}} service maintains a unique reference to tokens issued from notification providers - APNs for Apple or FCM for Google. The tokens can be invalidated by the service notification provider for several reasons. 

An example is during the uninstallation of an app on the device. In such a scenario, when a notification is attempted to be delivered based on the providers response that the device is invalidated, the {{site.data.keyword.mobilepushshort}} service removes the device or web browser registrations. This in turn would restrain consequent attempts in sending notification to those invalidated devices. 

You might also get the problem if you have unregistered a device.

Make sure that you have a valid Server API Key and Sender ID to continue. For more information, see [Obtain your notification provider credentials](/docs/mobilepush?topic=mobilepush-push_step_1).

## Why do I get `Notification is not working for WEB_Chrome.`, when attempting to initialize the Web Push SDK?
{: #faq-web-chrome}	

Your FCM credentials for web push SDK might have changed and the message delivery might fail for the Chrome browser. Ensure that you invoke `bmsPush.unRegisterDevice` to avoid failure.

## I get the message *Service workers aren't supported in this browser* when attempting to initialize the SDK for Web Push. What might be the problem? 
{: #faq-service-workers}	

Follow the steps mentioned in [Step 3: Set up Push service client SDKs](/docs/mobilepush?topic=mobilepush-push_step_3). Also, ensure that:

1. You use the correct start method. 
1. Include the `manifest.json` file in the root folder.
1. Host your website. Preferably create a `node.js` starter in IBM Cloud to try it out. For example, `https://<mysamplewebsite>.cloud.ibm.com/`.	

## How do I resolve web push web configuration errors?
{: #faq-web-config-errors}	

Web push errors from the `BMSPushSDK.js` contain information on the failure. See [Troubleshooting](/docs/mobilepush?topic=mobilepush-errors).	

## Do notifications persist if the devices are offline?
{: #faq-notification-persist}	

This feature depends on the notification provider.	

## Is the messageID unique for an application, and what is its size?
{: #faq-messageid}	

The messageID is unique for an application, and is limited to 8 characters. It can be alphanumeric.

## What are the limits for Push Notifications, in terms of payload size?
{: #faq-limits-push-payload-size}	

The {{site.data.keyword.mobilepushshort}} message payload size depends on the constraints that are laid out by the Gateways (FCM, APNs) and client platforms. 

For iOS 8 and later, the maximum size that is allowed is 4 kilobytes. Note that APNs do not send notifications that exceed this limit. For Android, Firefox browser, Chrome browser, and Chrome Apps & Extensions, there is a limitation of 4 kilobytes as the maximum allowed message payload size.	

## Are the notifications that are sent stored in BMS servers?
{: #faq-bms-servers}	

Yes, the notifications are stored for 90 days. It is recommended that you do not send any confidential messages as notifications.

## Can I send notification to devices in Doze mode?
{: #faq-doze-mode}	

This feature is not supported.	

## What are the different pricing plans available for the Push Notifications service?
{: #faq-pricing-plans}	

- **Advanced plan** - This is available for $100.00 USD/Instance, $0.50 USD/Million Digital Messages, and $0.50 USD/Million Addressable Devices. With the advanced plan, you can send {{site.data.keyword.mobilepushshort}} to 1 million addressable devices and 100 million digital messages. Advanced plan includes capabilities like Parameterize messages and End-to-End message lifecycle tracking.
- **Basic plan** - This is available for $1.00 USD/Million Digital Message. With the basic plan, you can send {{site.data.keyword.mobilepushshort}} to a unique device, browser, end-points, or a webhook-based event. 
- **Lite plan** - This is a free plan that features a hundred thousand free digital messages per month. However, Lite plan services are deleted after 30 days of inactivity.	

## Where can I find more information like tutorials or what's new?
{: #faq-what-is-new}	

Go through the {{site.data.keyword.mobilepushshort}} service [videos](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA){: external}.	

## Is there a difference between a notification and a message?
{: #faq-diff-notification-message}	

Yes. A _message_ is what that user is submitting to the {{site.data.keyword.mobilepushshort}} service. The service dispatches this as a _notification_ to the notification gateway (APNs/FCM), and this is delivered to the device or web browser.

For every message that you submit to the service, the intended audience receives a notification.	

## Does the {{site.data.keyword.mobilepushshort}} monitoring dashboard display any status for the messages that are sent?
{: #faq-push-monitor-dashboard}	

The monitoring utility displays the status for every sent message. The messages might be in the following state:
	
- **Sent** - The number of devices to which notifications are sent.
- **Seen** - The number of devices to which notifications have reached.
- **Open** - The number of devices where notification was opened.
- **Invalid** - The number of devices on which the token in invalid.

For more information, see the GET messages report in [{{site.data.keyword.IBM_notm}} {{site.data.keyword.mobilepushshort}} ReST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).	

## Does push notification monitor the push notification delivery up to the user device? For both Android and iOS?
{: #faq-end-user-device}	

{{site.data.keyword.mobilepushshort}} are monitored based on the number of notifications that are seen or opened from user device. This is available for both Android and iOS. Device id-based monitoring is not supported. 

## I get the message that the server is unable to handle requests? How can I resolve it?
{: #faq-server-unable-to-handle-requests}	

You might see the error with the error code FPWSE0025E. This might be due to too many requests for the server to handle. You can try resubmitting the request later.	

## I am sending notification by tags, but have a long list of tags that might be difficult to add manually. 
{: #faq-tag-based-notification}	

You can use REST APIs to automate the tag additions. See [POST bulk messages](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).

## How can I filter the push notification delivery by information that is stored in the user's mobile device?
{: #faq-filter-device}	

This should be handled in the context of application development.

## Can I customize the push notification monitoring further to add custom report such as delivery report per segmentation?
{: #faq-customize-delivery-report}	

This feature is not supported.

## Can I create a segment for new app user or users that have not accessed the mobile app for sometime?
{: #faq-create-segment}	

This should be handled in the context of application development.
	
## Can I register or update mobile devices at bulk by using the REST APIs?
{: #faq-register-mobile-devices}	

As in the design, registering or updating a device is called from the mobile applications by using SDK. Bulk registrations or updates through REST APIs are not supported. If many device registrations or updates are called simultaneously by using REST APIs, it might take a long time or might fail.	

## How do I send {{site.data.keyword.mobilepushshort}} or use the Rest APIs when I don’t have the appSecret?
{: #faq-rest-api-appsecret}	

As the {{site.data.keyword.mobilepushshort}} service has adopted IAM, an `apiKey` is displayed instead of the `appSecret` when the user creates the service credentials.

To use any ReST APIs, you must generate the access token by using the following curl command:

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```
{: codeblock}

```
{
 "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```
{: codeblock}

Upon generating the access token by using the preceding curl command, you might now operate the ReST APIs by passing the `Bearer <value of access_token>` in the Authorization header.

For example,

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
{: screen}

## What is the meaning of UNKNOWN status in the messageId based status (`GET /apps/{applicationId}/messages/{messageId}/status`)?
{: #faq-unknown-status}	

UNKNOWN status denotes an internal issue that occurred during the processing of the message. {{site.data.keyword.mobilepushshort}} works with best effort delivery, as there are multiple network points including the Providers like FCM, and APNS. To know more details on this message, it is important to check the delivery status (`GET /apps/{applicationId}/messages/{messageId}/deliverystatus`) and report (`GET /apps/{applicationId}/messages/{messageId}/report`) of the messageId. If the `deliverystatus` and `report` is also empty, then this particular message ID should be retried. 

## How to define Push ReST API filters?
{: #push-api-rest-filters}

Filters define a search criteria that restrict data that is returned from a GET API of {{site.data.keyword.mobilepushshort}}. Apply the filters against the result of the Get operation that you want to filter. The filter restricts the number of entries that are included in the result. For example, you can use a filter to search for tags that start with "test". 

Filters can be generated by using the following syntax:
- **name** - The field name on which the filter is being applied.
- **operator** - Either == (Exact Match) or =@ (Contains Substring) that describes filter match to use.
- **expression** - The values to include in the result.

When a comma and a backslash are displayed in an expression, they must be backslash-escaped.

When using multiple filters, they can be combined by using AND and OR logic.
- For AND logic, use multiple filters in the query.
- For OR logic, use a comma(,) inside of the filter expression.
- For both AND and OR logic, a single query can have both AND and OR logic. Each filter is evaluated individually before the filters are combined in an AND expression.

For the device GET API the following combinations are supported:
- The name is the platform field.
- Except for the platform, the operator can be == or =@
- For the platform, the operator must be ==. If operator =@ is used, the value can be a sub string.
- If == is used, the value must be an exact matching string.

For the subscription GET API the following combinations are supported:
- The name can be one of these fields: tagName or deviceId
- Except for the platform, the operator can be == or =@
- For the platform, the operator must be ==
- If the =@ operator is used, the value can be a sub string. If the == operator is used, the value must be an exact matching string.
- For the tag GET API the following combinations are supported:
- The name can be one of these fields: “name” or “description”
- If operator =@ is used, the value can be a sub string.
- If == is used, the value must be an exact matching string.

## How to make the {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} based projects and apps work with new Xcode build system?
{: #push-bms-sdk-failing}

BMS SDKs are failing with the Xcode New Build System. This is due to React Native 0.57+ and Cordova iOS@5.0.0 now supports the Xcode (9 and 10+) New Build System. 
Projects/apps, which are updated to these versions and higher don't need to do any changes to make the Push SDKs' work.
For the project and apps, which are in old versions, you cannot build the project with latest build system. The suggested workaround is:

* **Using Xcode**
   1. Go to **File** &gt; **Project Settings** or **Workspace Settings**.
   1. Select **Legacy Build System** from the **Build System** list.

* **Using Xcode build**
   - For **React Native**, use the **-UseModernBuildSystem=NO** flag to opt out of the new Xcode new build system.
   - For **cordova**, use **--buildFlag="-UseModernBuildSystem=0"** to build.

## Why do the API requests sent to {{site.data.keyword.mobilepushshort}} service through a stand-alone client like Java&trade; program fails with 403 - Forbidden error?
{: #faq-api-standalone-client}	

The API requests sent to the {{site.data.keyword.mobilepushshort}} service must be set to the `user-agent` request header. The user agent header property is a string that helps to identify the application that calling the API.

## How do I resolve a connection exception?
{: #faq-retry-logic}	

Applications that communicate over networks and cloud services are subject to transient connection failures. There can be a short blip in connectivity or trigger a failover. To resolve the connection exception in {{site.data.keyword.mobilepushshort}} service, retrying the API calls will bring the system back to normal.

Open a [support ticket](https://cloud.ibm.com/docs/get-support?topic=get-support-getting-customer-support) with details if you have longer periods with no connectivity.
