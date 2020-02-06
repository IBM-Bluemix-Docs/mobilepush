---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-04"

keywords: push notifications, notifications, sending a notification

subcollection: mobile-pushnotification

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

# Step 5: Sending a notification
{: #push_step_4}

After you have developed your applications, you can send basic push notifications.

To send basic push notifications, complete the following steps:

1. Select **Messages**, and compose a message by choosing a **Send to** option. The supported options are **Device by Tag**, **Device Id**, **User Id**, **Android devices**, **iOS devices**, **Web Notifications**, **Chrome Apps and Extensions**, **Chrome Browser**, **Firefox**, **Safari**, and **All Devices**.
**Note**: When you select the **All Devices** option, all devices that are subscribed to {{site.data.keyword.mobilepushshort}} will receive notifications.

   ![Notifications screen](images/tag_notification.jpg "Send notifications screen showing Send to, Message, and Additional payload fields")

1. In the **Message** field, compose your message. Choose to configure the optional settings as required.
1. Click **Send**.
1. Verify that your devices or browser has received the notification.

The following screen capture shows an alert box handling a push notification in the foreground on an Android device.

![Foreground push notification on Android](images/Android_Screenshot.jpg "Alert box with test notification")

The following screen capture shows a push notification in the background for Android.

![Background push notification on Android](images/background.jpg "Push notification on an Android device")

## Optional Android settings 
{: #push_step_4_Android}

You can further customize the {{site.data.keyword.mobilepushshort}} settings for sending notifications to Android devices. 

![Android custom settings](images/android_custom_settings.jpg "Push notifications custom settings page")

The following optional customization options are supported:

- Collapse Key:  Collapse keys are attached to notifications. If multiple notifications arrive sequentially with the same collapse key when the device is offline, they are collapsed. When a device comes online, it receives notifications from the FCM server, and displays only the latest notification bearing the same collapse key. If the collapse key is not set, both the new and old messages are stored for the future delivery.
- Sound: Indicates a sound clip to be played on the receipt of a notification. Supports default or the name of a sound resource that is	 bundled in the app.
- Icon: Specify the name of the icon to display for the notification. Ensure that you have packaged the icon in the `res/drawable` folder, with the client application.
- Priority: Specifies the options for assigning delivery priority to messages. 
   - A priority `high` or `max` result in heads-up notification.
   - A priority `low` or `default` will not open network connections on a sleeping device. 
   - A priority `min` will be a silent notification.
- Visibility: You can choose to set the notification visibility option to either `public` or `private`. 
   - The `private` option restricts public viewing and you can choose to enable it if your device is secure with a pin or pattern, and the notification setting is set to **Hide sensitive notification content**. When the visibility is set as `private`, a `redact` field must be mentioned. Only the content that is specified in the `redact` field shows up on a secure locked screen on the device. 
   - The `public` option would render the notifications to be freely read.
- Time to live: This value is set in seconds. If this parameter is not specified, the FCM server stores the message for four weeks and will try to deliver. The validity expires after four weeks. The possible value range is 0 - 2,419,200 seconds.
- Delay when idle: You can set this to either of the following values:
   - `True` - Instructs the FCM server not to deliver the notification if the device is idle. 
   - `False` - Ensures notification delivery even if the device is idle.
- Sync: By setting this option to `true`, notifications across all your registered devices are in sync. If the user with a username has multiple devices with the same application installed, reading the notification on one device ensures deletion of notifications in the other devices. You need to ensure that you are registered with {{site.data.keyword.mobilepushshort}} service with userId for this option to work.
- Additional payload: Specifies the custom payload values for your notifications.
- Expandable notification: This provides customers an option to expand a notification with more information, while a basic notification would be visible with the notification collapsed. The following options are supported:
   - Big Picture Notifications: You can choose to include a picture when the notification is expanded. Ensure that you provide a Title text and URL for the picture.
   - Big Text Notifications: You can choose to include additional text with a title. Ensure that the Big Text message and Title text information are furnished.
   - Inbox Style Notifications: You can send the notification that is styled as an inbox notification. Provide a Title text and furnish the message in Lines.	 

## Optional iOS settings 
{: #push_step_4_ios}

You can customize the {{site.data.keyword.mobilepushshort}} settings for sending notifications to iOS devices. The following optional customization options are supported.
- **Badge**:  Indicates the number that is displayed on the application badge. The default value is zero (0), and this would not display a badge. 
- **Sound**: Indicates a sound clip to be played on the receipt of a notification. Supports default or the name of a sound resource that is bundled in the app.
- **Additional payload**: Specifies the custom payload values for your notifications.

You can also choose to enable [interactive notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications) and [rich media notifications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications).

## Monitoring for delivered notifications 
{: #push_step_4_monitor}

The {{site.data.keyword.mobilepushshort}} service provides a monitoring utility to help you check the status of messages that are sent. To configure your monitoring utility, go through either of the following options:
- [Enable monitoring for Android applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
- [Enable monitoring for iOS applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
