---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# User-based notifications
{: #user_based_notifications}
Last updated: 22 May 2017
{: .last-updated}

User ID-based {{site.data.keyword.mobilepushshort}} are targeted at mobile app users with customized messages. With user-based notifications, you can choose to notify specific individuals based on their preferences.

## Register device with User ID
{: #register_device_wh_userid}

To enable push notifications targeted by User ID, ensure that you register the device with a User ID field set.     

The User ID can be any string that the application provides to the device registration API. Typically, a mobile application will first run an authentication cycle where the mobile app user is authenticated against an authentication service such as [{{site.data.keyword.amafull}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/docs/services/mobileaccess/index.html){: new_window}. On successful authentication, the authenticated user ID is then passed into the Push Device Registration API. 

To register for userId-based notification, go through:

- [Registering an Android application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [Registering an iOS application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Registering a Cordova application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Registering a web application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## Using userId-based notifications
{: #using_userid}

The userId-based notifications are notification messages that are targeted to a specific user. Many devices can be registered with one user. The following steps  describes how to send user ID-based notifications.

1. From the **Push Notification** console, select **Send Notifications** option.
1. Select **UserId** in the **Send to** list of options.
1. In the **User Id** field, search for the user Id that you want to use and then click the **+Add**.![Notifications Screen](images/user_notification.jpg)
1. In the **Message** field, enter text that want to send in your notification.
1. Click **Send**.


## Synchronizing user log-in and log out 
{: #sync_login_logout}

You can choose to send notifications only if the user is logged in. 

For example, consider a device shared by members of a team at work, and there is a need to address specific users. In such a use case, there would be a user log-in and log out sequence. This authentication mechanism allows the application to track the identity of the present user of the application. This ensures that notifications targeted to a specific user are always received by that user only. After a successful log-in, invoke the device registration API passing the User ID of the logged-in user. Likewise, before logging out, invoke the device `unregistration` API. Sequencing these Push APIs with log-in and log out will ensure that notifications intended for a specific user is sent to that user only.