---

copyright:
  years: 2015, 2020
lastupdated: "2020-05-20"

keywords: push notification, push notifications, notifications, interactive notification, silent notification

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

# Interactive and silent notifications  
{: #interactive-notifications}

Interactive notifications enable users to respond to a notification without opening the application. When an interactive notification arrives, the device shows the action buttons along with the notification message. 

Interactive notifications are not supported on iOS devices with versions earlier than 8. 
{: note}

## Sending interactive notifications
{: #send_interactive_notifications}

Interactive notification can be sent by using the {{site.data.keyword.mobilepushshort}} console or by using the [ReST API documentation](https://cloud.ibm.com/apidocs/push-notifications).

1. From the {{site.data.keyword.mobilepushshort}} console, click **Notifications** on the left navigation menu.
1. Click **Create**, and compose a message.
   - Compose a new notification by providing the following information: **Notification text**, **Notification title** (optional), **Additional payload** (optional).
   - Select the **Target audience** by one of the following target:
      - **Platforms** - Options are: **Android**, **iOS**, **Web Notifications**, **Chrome Apps and Extensions**, **Chrome Browser**, **Firefox**, **Safari**, and **All Devices**.
      - **Tags** - Enter the Tag, topic name or create a new tag.
      - **Devices/user IDs** - Select the **User ID** and enter the user ID of the notification recipients.
1. Click **Send**.

In the compose notification page, interactive push can be sent by setting the Type to either Default or Mixed and specifying the Category value under **Advanced Settings**. 
{: note}

## Handling interactive notifications 
{: #handle_interactive_notifications}

- For iOS, go through [Enable and handle interactive notifications on Swift applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications).
- For Cordova, go through [Enable and handle interactive notifications on Cordova applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications).
- For Android, go through [Enable and handle interactive notifications on Android applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications).

## Handling silent notifications for iOS
{: #send_silent_notifications_for_ios}

Silent notifications do not appear on the device screen and are received by the application in the background. For more information, see [Silent Notifications on iOS devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification).
