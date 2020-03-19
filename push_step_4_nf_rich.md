---

copyright:
  years: 2015, 2020
lastupdated: "2020-03-19"

keywords: push notifications, notifications, rich media notification

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

# Rich Media notifications
{: #rich-media-notifications}

You can enable Rich Media {{site.data.keyword.mobilepushshort}} in iOS 10 and later. {{site.data.keyword.mobilepushshort}} can be sent with Audio, Video, GIFs, and images. 

To set up your application to receive rich push on iOS 10, complete the steps:  

1. In Xcode, select **File** > **New** > **Target** > **Notification Service Extension**.
1. On the method `didReceive()` in the `UNNotificationServiceExtension`, add the code.

   ```
   BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
   ```
   {: codeblock}	

To send a Rich Media {{site.data.keyword.mobilepushshort}} from the Push console, ensure that you specify the message, title, subtitle, and attachmentURL fields.
