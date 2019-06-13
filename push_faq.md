---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, faq, frequently asked questions

subcollection: mobile-pushnotification

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Frequently Asked Questions 
{: #faq}

### Why do my tokens get invalidated?
{: #faq-tokens}	

For device, browser, Chrome Apps & Extensions registrations, the Push Notifications service maintains a unique reference to tokens issued from notification providers - APNs for Apple or FCM for Google. The tokens can be invalidated by the service notification provider for several reasons. 

An example is during the uninstallation of an app on the device. In such a scenario, when a notification is attempted to be delivered based on the providers response that the device is invalidated, the {{site.data.keyword.mobilepushshort}} service will remove the device or web browser registrations. This in turn would restrain consequent attempts in sending notification to those invalidated devices. 

You might also get the problem if you have unregistered a device.

Ensure that you obtain a valid Server API Key and Sender ID to continue. See [Obtain your notification provider credentials](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1).

### Why do I get *Notification is not working for WEB_Chrome.*, when attempting to initialize the Web Push SDK?
{: #faq-web-chrome}	

You might have changed your FCM credentials for Web push SDK and the message delivery might fail for the Chrome browser. Ensure that you invoke *bmsPush.unRegisterDevice* to avoid failure.

### I get the message *Service workers aren't supported in this browser* when attempting to initialize the SDK for Web Push. What might be the problem? 
{: #faq-service-workers}	

Follow the steps mentioned in [Step 3: Set up Push service client SDK's](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3). Also ensure that:

1. You use the correct start method. 
2. Include the `manifest.json` file in the root folder.
3. Host your website. Preferably create a `node.js` starter in IBM Cloud to try it out. For example: https://<mysamplewebsite>.cloud.ibm.com/.	

### How do I resolve Web push web configuration errors?
{: #faq-web-config-errors}	

Web push errors from the `BMSPushSDK.js` contain information on the failure. See [Troubleshooting](/docs/services/mobilepush?topic=mobile-pushnotification-errors).	

### Do notifications persist if the devices are offline?
{: #faq-notification-persist}	

This feature is dependant on the notification provider.	

### Is the messageID unique for an application, and what is its size?
{: #faq-messageid}	

The messageID is unique for an application, and is limited to eight characters. It can be alphanumeric.

### What are the limits for Push Notifications, in terms of payload size?
{: #faq-limits-push-payload-size}	

The {{site.data.keyword.mobilepushshort}} message payload size is dependent on the constraints laid out by the Gateways (FCM, APNs) and client platforms. 

For iOS 8 and later, the maximum size allowed is 4 kilobytes. Note that APNs does not send notifications that exceeds this limit. For Android, Firefox browser, Chrome browser, and Chrome Apps & Extensions, there is a limitation of 4 kilobytes as the maximum allowed message payload size.	

### Are the notifications that are sent stored in BMS servers?
{: #faq-bms-servers}	

Yes, the notifications are stored for a period of ninety days. It is recommended that you do not send any confidential messages as notifications.

### Can I send notification to devices in Doze mode?
{: #faq-doze-mode}	

This feature is not supported.	

### What are the different pricing plans available for the Push Notifications service?
{: #faq-pricing-plans}	

* <b>Advanced plan</b>: This is available for $100.00 USD/Instance, $0.50 USD/Million Digital Messages, and $0.50 USD/Million Addressable Devices. With the advanced plan, you can send push notifications to 1 million addressable devices and 100 million digital messages. Advanced plan includes capabilities like Parameterize messages and End-to-End message lifecycle tracking.

* <b>Basic plan</b>: This is available for $1.00 USD/Million Digital Message. With the basic plan, you can send push notifications to a unique device, browser, end- points or a webhook-based event. 

* <b>Lite plan</b>: This is a free plan that features a hundred thousand free digital messages per month. However, Lite plan services are deleted after 30 days of inactivity.	

### Where can I find more information like tutorials or what's new?
{: #faq-what-is-new}	

Go through the Push Notifications service [videos](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA).	

### Is there a difference between a notification and a message?
{: #faq-diff-notification-message}	

Yes. A _message_ is what that user is submitting to the {{site.data.keyword.mobilepushshort}} service. The service dispatches this as a _notification_ to the notification gateway (APNs/FCM), and this is delivered to the device or web browser.

For every message that you submit to the service, the intended audience receives a notification.	

### Does the Push Notifications monitoring dashboard display any status for the messages that are sent?
{: #faq-push-monitor-dashboard}	

The monitoring utility displays the status for every sent message. The messages might be in the following state:
	
* Sent: The number of devices to which notifications are sent.
* Seen: The number of devices to which notifications had reached.
* Open: The number of devices where notification was opened.
* Invalid: The number of devices on which the token in invalid.

For more information, see the GET messages report in [IBM Push Notifications ReST API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).	

### Does push notification monitor the push notification delivery up to the end user device? For both Android and iOS?
{: #faq-end-user-device}	

Push notifications are monitored based on the number of notifications that are seen or opened from end user device. This is available for both Android and iOS. Device id-based monitoring is not supported. 

### I get the message that the server is currently unable to handle requests? How can I resolve it?
{: #faq-server-unable-to-handle-requests}	

You might see the error with the error code FPWSE0025E. This might be due to too many requests for the server to handle. You can try resubmitting the request at a later time.	

### I am sending notification by tags, but have a long list of tags that might be difficult to add manually. 
{: #faq-tag-based-notification}	

You can use REST APIs to automate the tag additions. See [POST bulk messages](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).

### How can I filter the push notification delivery by information stored in the user's mobile device?
{: #faq-filter-device}	

This should be handled in the context of application development.

### Can I customize the push notification monitoring further to add custom report such as delivery report per segmentation?
{: #faq-customize-delivery-report}	

This feature is not supported.

### Can I create a segment for new app user or users that have not accessed the mobile app for sometime?
{: #faq-create-segment}	

This should be handled in the context of application development.
	
### Can I register/update mobile devices at bulk using the REST APIs?
{: #faq-register-mobile-devices}	

As per the design, registering/updating a device is called from the mobile applications using SDK. Bulk registrations/updates through REST APIs is not supported. If many device registrations/updates are called simultaneously using REST APIs, it may take a long time or may fail.	

### How do I send Push Notifications or use the Rest API’s when I don’t have the appSecret?
{: #faq-rest-api-appsecret}	

As the {{site.data.keyword.mobilepushshort}} service has adopted IAM, an `apiKey` is displayed instead of the `appSecret` when the user creates the service credentials.

To use any REST APIs, you must generate the access token using the following curl command:

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```

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

Upon generating the access token using the preceding curl command, you may now operate the Rest API’s by passing the ‘Bearer <value of access_token>’ in the Authorization header

For example:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
   }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
