---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# FAQ's 
{: #faq}


1. Why do my tokens get invalidated?

	For device, browser, Chrome Apps & Extensions registrations, the Push Notifications service maintains a unique reference to tokens issued from notification providers - APNs for Apple or FCM for Google. The tokens can be invalidated by the service notification provider for several reasons. 

	An example is during the uninstallation of an app on the device. In such a scenario, when a notification is attempted to be delivered based on the providers response that the device is invalidated, the {{site.data.keyword.mobilepushshort}} service will remove the device or web browser registrations. This in turn would restrain consequent attempts in sending notification to those invalidated devices. 


1. Why do I get "Notification is not working for WEB_Chrome.", when attempting to initialize the Web Push SDK?

	You might have changed your FCM/GCM credentials for Web push SDK and the message delivery might fail for the Chrome browser. Ensure that you invoke "bmsPush.unRegisterDevice" to avoid failure.


1. I get the message "Service workers aren't supported in this browser" when attempting to initialize the SDK for Web Push. What might be the problem? 

	Follow the steps mentioned in [Step 3: Set up Push service client SDK's](push_step_3.html).

	Also ensure that:
 
	1. You use the right start method. 
	1. Include the `manifest.json` file in the root folder.
	1. Host your website. Preferably create a `node.js` starter in Bluemix to try it out. For example: https://<mysamplewebsite>.mybluemix.net/.
	
	
1. How do I resolve Web push web configuration errors?

	Web push errors from the `BMSPushSDK.js` contain information on the failure.  See [Troubleshooting](push_troubleshooting.html).

1. Do notifications persist if the devices are offline?
	
	This feature is dependant on the notification provider.

2. Is the messageID unique for an application, and what is its size?
	
	The messageID is unique for an application, and is limited to 7 characters. It can be alphanumeric.

2. What are the limits for Push Notifications, in terms of payload size?

	The {{site.data.keyword.mobilepushshort}} message payload size is dependent on the constraints laid out by the Gateways (FCM/GCM, APNs) and client platforms. 

	For iOS 8 and later, the maximum size allowed is 2 kilobytes. Note that APNs does not send notifications that exceeds this limit. For Android, Firefox browser, Chrome browser, and Chrome Apps & Extensions, there is a limitation of 4 kilobytes as the maximum allowed message payload size.
  
3. How scalable is the Push Notifications service?
	Answer:

4. Are the notifications that are sent stored in BMS servers?

	Yes, the notifications are stored for a period of seven days. It is recommended that you do not send any confidential messages as notifications.

5. Can I send notification to devices in Doze mode?

	This feature is not supported.

6. What are the different pricing plans available for the Push Notifications service?

	A basic plan is available for $1.00 USD/Million Digital Message. With the basic plan, you can send push notifications to a unique device, browser, end- points or a webhook-based event. 

7.  Where can I find more information like tutorials or what's new?

	Go through the Push Notifications service [blog](http://push-notification-service.mybluemix.net/).

8. Is there a difference between a notification and a message?

	Yes. A _message_ is what that user is submitting to the {{site.data.keyword.mobilepushshort}} service. The service dispatches this as a _notification_ to the notification gateway (APNs/FCM), and this is delivered to the device or web browser.

	For every message that you submit to the service, the intended audience receives a notification.

	
	




	


