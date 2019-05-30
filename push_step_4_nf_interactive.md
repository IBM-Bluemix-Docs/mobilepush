---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-05-30"

keywords: push notifications, notifications, interactive notification, silent notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Interactive and silent notifications  
{: #interactive-notifications}

Interactive notifications enable users to respond to a notification without opening the application. When an interactive notification arrives, the device shows the action buttons along with the notification message. 

**Note:** Interactive notifications are not supported on iOS devices with versions earlier than 8. 

## Sending interactive notifications
{: #send_interactive_notifications}

Interactive notification can be sent by using the Push Notifications console or by using the [REST API documentation](https://cloud.ibm.com/apidocs/push-notifications).


From the {{site.data.keyword.mobilepushshort}} console: 

1. On the notification tab, click **Send Notification**. 
2. Choose your notification recipients and click **Next**. 
3. In the compose notification page, interactive push can be sent by setting the Type to either Default or Mixed and specifying the Category value under Advanced Options tab. 

## Handling interactive notifications 
{: #handle_interactive_notifications}

- For iOS, go through [Enable and handle interactive notifications on Swift applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications).
- For Cordova, go through [Enable and handle interactive notifications on Cordova applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications).
- For Android, go through [Enable and handle interactive notifications on Android applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications).


## Handling silent notifications for iOS
{: #send_silent_notifications_for_ios}

Silent notifications do not appear on the device screen and are received by the application in the background. For more information, see [Silent Notifications on iOS devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification).
