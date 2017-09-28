---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Frequently Asked Questions 
{: #faq}


1. Why do my tokens get invalidated?
	
	For device, browser, Chrome Apps & Extensions registrations, the Push Notifications service maintains a unique reference to tokens issued from notification providers - APNs for Apple or FCM for Google. The tokens can be invalidated by the service notification provider for several reasons. 

	An example is during the uninstallation of an app on the device. In such a scenario, when a notification is attempted to be delivered based on the providers response that the device is invalidated, the {{site.data.keyword.mobilepushshort}} service will remove the device or web browser registrations. This in turn would restrain consequent attempts in sending notification to those invalidated devices. 

	You might also get the problem if you have unregistered a device.

	Ensure that you obtain a valid Server API Key and Sender ID to continue. See [Obtain your notification provider credentials](push_step_1.html).


2. Why do I get "Notification is not working for WEB_Chrome.", when attempting to initialize the Web Push SDK?

	You might have changed your FCM/GCM credentials for Web push SDK and the message delivery might fail for the Chrome browser. Ensure that you invoke "bmsPush.unRegisterDevice" to avoid failure.

3. I get the message "Service workers aren't supported in this browser" when attempting to initialize the SDK for Web Push. What might be the problem? 

	Follow the steps mentioned in [Step 3: Set up Push service client SDK's](push_step_3.html).	Also ensure that:
 
	1. You use the right start method. 
	1. Include the `manifest.json` file in the root folder.
	1. Host your website. Preferably create a `node.js` starter in Bluemix to try it out. For example: https://<mysamplewebsite>.mybluemix.net/.	

4. How do I resolve Web push web configuration errors?

	Web push errors from the `BMSPushSDK.js` contain information on the failure.  See [Troubleshooting](push_troubleshooting.html).	

5. Do notifications persist if the devices are offline?

	This feature is dependant on the notification provider.	

6. Is the messageID unique for an application, and what is its size?

	The messageID is unique for an application, and is limited to eight characters. It can be alphanumeric.

7. What are the limits for Push Notifications, in terms of payload size?

	The {{site.data.keyword.mobilepushshort}} message payload size is dependent on the constraints laid out by the Gateways (FCM/GCM, APNs) and client platforms. 

	For iOS 8 and later, the maximum size allowed is 4 kilobytes. Note that APNs does not send notifications that exceeds this limit. For Android, Firefox browser, Chrome browser, and Chrome Apps & Extensions, there is a limitation of 4 kilobytes as the maximum allowed message payload size.	

8. Are the notifications that are sent stored in BMS servers?

	Yes, the notifications are stored for a period of seven days. It is recommended that you do not send any confidential messages as notifications.

9. Can I send notification to devices in Doze mode?

	This feature is not supported.	

10. What are the different pricing plans available for the Push Notifications service?

	Basic plan: This is available for $1.00 USD/Million Digital Message. With the basic plan, you can send push notifications to a unique device, browser, end- points or a webhook-based event. 

	Lite plan: This is a free plan that features a hundred thousand free digital messages per month. However, Lite plan services are deleted after 30 days of inactivity.	

11. Where can I find more information like tutorials or what's new?

	Go through the Push Notifications service [blog](http://push-notification-service.mybluemix.net/).	

12. Is there a difference between a notification and a message?

	Yes. A _message_ is what that user is submitting to the {{site.data.keyword.mobilepushshort}} service. The service dispatches this as a _notification_ to the notification gateway (APNs/FCM), and this is delivered to the device or web browser.

	For every message that you submit to the service, the intended audience receives a notification.	

13. Does the Push Notifications monitoring dashboard display any status for the messages that are sent?

	The monitoring utility displays the status for every sent message. The messages might be in the following state:
	
	- Sent: The number of devices to which notifications are sent.
	- Seen: The number of devices to which notifications had reached.
	- Open: The number of devices where notification was opened.
	- Invalid: The number of devices on which the token in invalid.

	For more information, see the GET messages report in [IBM Push Notifications ReST API](https://mobile.ng.bluemix.net/imfpush/).	

14. Does push notification monitor the push notification delivery up to the end user device? For both Android and iOS?

	Push notifications are monitored based on the number of notifications that are seen or opened from end user device. This is available for both Android and iOS. Device id-based monitoring is not supported. 

15. I get the message that the server is currently unable to handle requests? How can I resolve it?

	You might see the error with the error code FPWSE0025E. This might be due to too many requests for the server to handle. You can try resubmitting the request at a later time.	

16. I am sending notification by tags, but have a long list of tags that might be difficult to add manually. 
	
	You can use REST APIs to automate the tag additions. See [POST bulk messages](https://mobile.ng.bluemix.net/imfpush/).

17. How can I filter the push notification delivery by information stored in the user's mobile device?

	This should be handled in the context of application development.

18. Can I customize the push notification monitoring further to add custom report such as delivery report per segmentation?

	This feature is not supported.

19.  Can I create a segment for new app user or users that have not accessed the mobile app for sometime?

	This should be handled in the context of application development.


	


	
	




	


