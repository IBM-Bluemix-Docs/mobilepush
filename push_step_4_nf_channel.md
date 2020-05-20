---

copyright:
  years: 2020
lastupdated: "2020-05-20"

keywords: push notification, push notifications, notifications, channel, channel group, channel id

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

# Channel notifications
{: #channel_based_notifications}

Channel-based {{site.data.keyword.mobilepushshort}} are targeted at mobile app users with specific category. With channel-based notifications, you can choose to notify specific individuals based on the channel which they are subscribed.

Starting in Android 8.0 (API level 26), all notifications must be assigned to a channel. For each channel, you can set the visual and auditory behavior that is applied to all notifications in that channel. Then, users can change these settings and decide which notification channels from your app should be intrusive or visible at all.
{: note}

## Creating Channels
{: #creating_channels}

To enable {{site.data.keyword.mobilepushshort}} targeted by Channel ID, ensure that you register the device with a User ID field set.     

1. In the {{site.data.keyword.mobilepushshort}} service console, click **Channels** on the left navigation menu.
1. Click **Create**.
   - Provide the New Channel's **Basic Information**:
      - **Channel ID**, **Channel Name**, **Group ID**, **Description**.
   - Set the following basic channel properties:
      - **Importance**, **Vibrate** (on or off), **Sound** (provide the sound path), **Vibration pattern** (enter comma separated values for play and pause of sound)
   - Set the **Advanced settings** (optional)
      - **Lights** (on or off), **Lock screen visibility**, **Color**, **Override DND** (on or off), **Display Badge** (on or off)
1. Click **Create**.

## Creating Channel Groups
{: #createing_channelgroup}

To enable {{site.data.keyword.mobilepushshort}} targeted by Channel ID, ensure that you register the device with a User ID field set.     

1. In the {{site.data.keyword.mobilepushshort}} service console, click **Channels** on the left navigation menu.
1. Navigate to **Groups** tab.
1. Click **Create**.
   - Provide the New Group's details:
      - **Group ID**, **Group Name**.
1. Click **Create**.

## Using Channel-based notifications
{: #using_channel_based}

The Channel-based notifications are notification messages that are targeted to a specific channel.

1. From the {{site.data.keyword.mobilepushshort}} console, click **Notifications** on the left navigation menu.
1. Click **Create**, and compose a message.
   - Compose a new notification by providing the following information: **Notification text**, **Notification title** (optional), **Additional payload** (optional).
   - Select the **Target audience** by one of the following target:
      - **Platforms** - Options are: **Android**, **iOS**, **Web Notifications**, **Chrome Apps and Extensions**, **Chrome Browser**, **Firefox**, **Safari**, and **All Devices**.
      - **Tags** - Enter the Tag, topic name or create a new tag.
      - **Devices/user IDs** - Select the **Device ID** or **User ID** and the detail for the selection.
   - In the **Advanced settings** section, click **View All** and select the **Channel ID**.
1. Click **Send**.
