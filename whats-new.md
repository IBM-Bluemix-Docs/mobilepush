---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-31"

keywords: push notifications, push notification, notifications, release notes

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

# What's New
{: #whats-new}

The following new features and changes to the service are available. These changes do not break existing code:

## August 2020

- {{site.data.keyword.mobilepushshort}} CLI plug-in for {{site.data.keyword.cloud_notm}}<br/>
{{site.data.keyword.mobilepushshort}} CLI plug-in is now available in the {{site.data.keyword.cloud_notm}} plug-in repository. With the {{site.data.keyword.mobilepushshort}} service CLI, you can easily send {{site.data.keyword.mobilepushshort}} by using the CLI commands available. For more information on {{site.data.keyword.mobilepushshort}} CLI plug-in, see [here](/docs/mobilepush?topic=mobilepush-cli-plugin-mobilepush-cli).

## April 2020

- Performance improvement for web notifications - Chrome and Firefox <br/>
Several internal changes were made on web notifications to improve the performances for Firefox and Chrome notifications. 
- [Notification grouping](/docs/mobilepush?topic=mobilepush-channel_based_notifications#creating_channelgroup)<br/>
With channel-based notifications, you can choose to notify specific individuals based on the channel, which they are subscribed.

## March 2020

- The new improved design provides uniform experience across {{site.data.keyword.cloud_notm}} Console and other {{site.data.keyword.cloud_notm}} services.
- No more multiple left navigation menus. You now have more space to work within the console.
- Step-by-step guidance for usage and all SDKs is now downloadable from within the service.
- Ease of use across configuration, sending notifications and monitoring the notifications sent.

## December 2019

- Launch of [{{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} Service in new region](https://www.ibm.com/cloud/blog/announcements/push-notifications-on-ibm-cloud-is-now-available-in-the-tokyo-region) (Tokyo)
- Support for Custom Notifications Channel for Android

## October 2019

- APNS Collapse ID Support<br/>
Support for multiple notifications with the same collapse identifier to be displayed as single notification to the users with iOS devices.

## July 2019

- Application Server Keys Support<br/>
Application Server Keys are used to authenticate the application server. (This is defined by the VAPID spec.) This key is used to provide more security to verify that the application server that triggering the web push message is same as the one subscribed by the user.

## February 2019

- React Native<br/>
React Native SDK released to support react native applications for {{site.data.keyword.cloud_notm}} {{site.data.keyword.mobilepushshort}} Service.

## August 2018

- PWA Support<br/>
Progressive Web Application support introduced for web push notifications.

## June 2018

- Managing access to {{site.data.keyword.mobilepushshort}} through IBM Cloud Identity and Access Management (IAM)<br/>
As an account owner, you can set policies within your account to create different levels of access for different users by using [IAM](/docs/mobilepush?topic=mobilepush-service-access-management).
- Activity Tracker<br/>
You can monitor a user's interaction with the {{site.data.keyword.mobilepushshort}} service. You can search and analyze how your users and applications [interact with the service](/docs/mobilepush?topic=mobilepush-at_events).

## May 2018

- Resource Controller (RC) based service<br/>
{{site.data.keyword.mobilepushshort}} service is now an RC-based service. Service instances must be created by using a Resource controller.

## March 2018

- Track the message delivery status<br/>
You can view the delivery status of every notification that has been submitted to the service. 
- Parameterize Notifications<br/>
You can parameterize and send custom notifications by creating variables and calling them in your notification templates.
