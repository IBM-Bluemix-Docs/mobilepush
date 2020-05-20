---

copyright:
  years: 2015, 2020
lastupdated: "2020-05-20"

keywords: push notification, push notifications, notifications, configure sound, payload, ios badge, holding android notification

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

# Enabling advanced {{site.data.keyword.mobilepushshort}}
{: #enabling-advanced-push-notifications}

Configure an iOS badge, sound, additional JSON payload, actionable notifications, and holding notifications.

## Configure sound, and payload and iOS badge
{: #badge-sound-payload}

Configure an iOS badge, sound, and additional JSON payload.

1. In the {{site.data.keyword.mobilepushshort}} service console, click **Notifications** on the left navigation menu.
1. Click **Create**, and compose a message.
   - Compose a new notification by providing the following information: **Notification text**, **Notification title** (optional), **Additional payload** (optional).
   - Select the **Target audience** by one of the following target:
      - **Platforms** - Options are: **Android**, **iOS**, **Web Notifications**, **Chrome Apps and Extensions**, **Chrome Browser**, **Firefox**, **Safari**, and **All Devices**.
      - **Tags** - Enter the Tag, topic name or create a new tag.
      - **Devices/user IDs** - Select either **Device ID** or **User ID** and enter the device/user ID detail for the selection.

   **Note**: When you select the **All Devices** option, all devices that are subscribed to {{site.data.keyword.mobilepushshort}} will receive notifications.

   - Optionally for rich media notifications use **Advanced settings**. Select the **Priority** (valid options are: Default, Max, Min, Low, High) and select the type of notification to be sent (**Default** or **Silent**).
   - Go to the **Advanced Settings** section and click **View All** and configure the {{site.data.keyword.mobilepushshort}} features. 
      - **Sound File** - Enter a string to point to the sound file in your mobile app. In the payload, specify the string name of the sound file to use.
      - **iOS Badge** - For iOS devices, the number to display as the badge of the app icon. If this property is absent, the badge is not changed. To remove the badge, set the value of this property to 0.
1. Choose either of the following options:	
   - On Android
      Add your sound file in `res/raw` directory of your android application. While sending notification, add the sound file name in the sound field of {{site.data.keyword.mobilepushshort}}:

      ```
      "settings":{
         "gcm":{
         "sound":"tt.wav",
    	 }
    	 }  
      ```
      {: codeblock}	
	
   - On iOS
      ```
      "settings": {
         "apns" : {
            "badge": 10,
            "sound": "tt.wav",
         }
      }
      ``` 
      {: codeblock}

**Additional Payload** - This payload can be any key-value pair and must be a JSON object that you want to send with the {{site.data.keyword.mobilepushshort}}.

```
{"key":"value", "key2":"value2"}
```
{: codeblock}

## Holding Android notifications 
{: #hold-notifications-android}

When your application goes into background, you might want {{site.data.keyword.mobilepushshort}} to hold back notifications that are sent to your application. To hold notifications, call the `hold()` method in the `onPause()` method of the activity that is handling {{site.data.keyword.mobilepushshort}}.

```
@Override
protected void onPause() {
    super.onPause();
    if (push != null) {
        push.hold();
    }
} 
```
{: codeblock}
