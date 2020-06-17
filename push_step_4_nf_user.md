---

copyright:
  years: 2015, 2020
lastupdated: "2020-06-18"

keywords: push notification, push notifications, notifications, user-based, register device with user ID, synchronize user login and logout

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

# User-based notifications
{: #user_based_notifications}

User ID-based {{site.data.keyword.mobilepushshort}} are targeted at mobile app users with customized messages. With user-based notifications, you can choose to notify specific individuals based on their preferences.

## Register device with User ID
{: #register_device_wh_userid}

To enable {{site.data.keyword.mobilepushshort}} targeted by User ID, ensure that you register the device with a User ID field set.     

The User ID can be any string that the application provides to the device registration API. Typically, a mobile application will first run an authentication cycle where the mobile app user is authenticated against an authentication service such as {{site.data.keyword.amafull}}. On successful authentication, the authenticated user ID is then passed into the Push Device Registration API. 

To register for userId-based notification, go through:
- [Registering an Android application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [Registering an iOS application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Registering a Cordova application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Registering a web application](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)

## Using userId-based notifications
{: #using_userid}

The userId-based notifications are notification messages that are targeted to a specific user. Many devices can be registered with one user. The following steps describe how to send user ID-based notifications.

1. From the {{site.data.keyword.mobilepushshort}} console, click **Notifications** on the left navigation menu.
1. Click **Create**, and compose a message.
   - Compose a new notification by providing the following information: **Notification text**, **Notification title** (optional), **Additional payload** (optional).
   - Select the **Target audience** by one of the following targets:
      - **Platforms** - Options are: **Android**, **iOS**, **Web Notifications**, **Chrome Apps and Extensions**, **Chrome Browser**, **Firefox**, **Safari**, and **All Devices**.
      - **Tags** - Enter the Tag, topic name or create a new tag.
      - **Devices/user IDs** - Select the **User ID** and enter the user ID detail for the selection.
1. Click **Send**.

## Synchronizing user login and logout 
{: #sync_login_logout}

You can choose to send notifications only if the user is logged in. 

For example, consider a device that is shared by members of a team at work, and there is a need to address specific users. In such a use case, there would be a user log-in and log out sequence. This authentication mechanism allows the application to track the identity of the present user of the application. This ensures that notifications that are targeted to a specific user are always received by that user only. After a successful log-in, start the device registration API passing the User ID of the logged-in user. Likewise, before logging out, start the device `unregistration` API. Sequencing these Push APIs with log-in and log out will ensure that notifications that are intended for a specific user is sent to that user only.
