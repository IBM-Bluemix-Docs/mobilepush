---

copyright:
  years: 2015, 2017, 2019
lastupdated: "28 May 2019"

keywords: push notifications, notifications, service instance, cordova application

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Step 3: Configure a service instance 
{: #push_step_2}

Ensure that you have gone through [Obtain your notification credentials](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1).

## For Android and Chrome Apps & Extensions
{: #push_step_2_Android}

Ensure that you have gone through [Obtain your notification provider credentials](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) to setup the FCM project and obtain your credentials.

To configure FCM credentials for Android applications and Google Chrome Apps & Extensions, complete the following steps:

1. Open your IBM Cloud catalog and then click the {{site.data.keyword.mobilepushfull}} service instance you have created. 
2. Click **Manage** > **Configure**. 
3. Choose either of the following options: 
	- For Android: Select **Mobile** and then update the FCM Push Credentials tab with the Sender ID/Project number and API Key. 
	- For Google Chrome Apps & Extensions: Select **Web** and then update the Chrome Apps and Extensions tab with the Sender ID/Project number and API Key. 
4. Click **Save**. The Push Notifications service is now configured.

Your next step is to [set up the Push service client SDK's](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3).


## For Cordova applications 
{: #push_step_2_b}


Cordova is a platform for building hybrid applications with JavaScript, CSS, and HTML. The {{site.data.keyword.mobilepushshort}} service supports development of Cordova-based iOS and Android applications.

To enable Cordova applications for receiving push notifications to your devices, go through [Push Notifications Cordova Plugin Push SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).



## For iOS applications and Safari browser 
{: #enable-push-ios-notifications}


To use the {{site.data.keyword.mobilepushshort}} service to send notifications, upload the `.p12` certificates that you had created in Step 1:[Obtain your notification provider credentials](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1). This certificate contains the private key and SSL certificates that are required to build and publish your application. You can also use the REST API to upload an APNs certificate.

**Note**: After the `.cer` file is in your key chain access, export it to your computer to create a `.p12` certificate.

For more information about using the APNs, see [iOS Developer Library: Local and Push Notification Programming Guide ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1){: new_window}.

To set up APNs on the Push Notification services console, complete the steps:

1. Select **Configure** on the Push Notification services console.
2. Choose the **Mobile** option to update the information in the **APNs Push Credentials** form.
3. Choose either of the following options:
	- For **Mobile** option
		1. Select **Sandbox** (development) or **Production** (distribution) as appropriate and then upload the `p.12` certificate that you have created. 
		  ![Set push notifications console](images/wizard.jpg)

		1. In the **Password** field, enter the password that is associated with the `.p12` certificate file, then click **Save**.
	- For **Web** option
		- In the Safari Push section, update the form with the required information. 
		- **Website Name**: This is the name that you have provided in the Notification center.
		- **Website Push ID**: Update with the reverse-domain string for your Website Push ID. For example, web.com.acmebanks.www.
		- **Website URL**: Provide the URL of the website that should be subscribed to push notifications. For example, https://www.acmebanks.com.
		- **Allowed Domains**: This is optional parameter. This is the list of websites that requests permission from the user. Ensure that the URLs are comma separated values. Note that the value in Website URL will be used if this is not provided. 
		- **URL Format String**: The URL to resolve when the notification is clicked. For example, ["https://www.acmebanks.com"]. Ensure that the URL use the http or https scheme.
		-**Safari web push certificate**: Upload the .p12 certificate and provide the password.
4. Click **Save**.	
![Push Notifications console](images/push_configure_safari.jpg)	

After you have set up the service for iOS applications, you need to [Set up Push service client SDK's](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3).


## For Chrome and Firefox browsers 
{: #push_step2_chromefirefox}

1. On the Push Notifications console, select **Configure**.
2. Select the Web tab.
	![WebPush Configurations](images/webpush_configure.jpg)
3. Configure the FCM API key and the URL of your website that will be registered to receive push notifications.
4. Click **Save**.
5. After you have set up the service, you need to [Set up Push service client SDK's](https://cloud.ibm.com/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3).


