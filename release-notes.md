---

copyright:
  years: 2015, 2020
lastupdated: "2020-03-19"

keywords: push notifications, notifications, release notes

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

# Release notes
{: #release-notes}

The following new features and changes to the service are available. These changes do not break existing code:


## December 2019

* Launch of IBM Cloud Push Notifications Service in new region (Tokyo)
* Support for Custom Notifications Channel for Android

## October 2019

### APNS Collapse ID Support

Support for multiple notifications with the same collapse identifier to be displayed as single notification to the users with iOS devices.

## July 2019

### Application Server Keys Support
 
Application Server Keys are used to authenticate the application server. (This is defined by the VAPID spec.) This key is used to provide additional security to verify that the application server triggering the web push message is same as the one subscribed by the user.

## February 2019

### React Native

React Native SDK released to support react native applications for IBM Cloud Push Notifications Service.

## August 2018

### PWA Support

Progressive Web Application support introduced for web push notifications.

## June 2018

### Managing access to Push Notifications through IBM Cloud Identity and Access Management (IAM)

As an account owner, you can set policies within your account to create different levels of access for different users by using [IAM](/docs/services/mobilepush?topic=mobile-pushnotification-service-access-management).

### Activity Tracker

You can monitor a user's interaction with the Push Notifications service. You can search and analyze how your users and applications [interact with the service](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker).

## May 2018

### Resource Controller (RC) based service

IBM Push Notifications service is now an RC-based service. Service instances must be created by using a Resource controller.

## March 2018

### Track the message delivery status

You can view the delivery status of every notification that has been submitted to the service. 

### Parameterize Notifications

You can parameterize and send custom notifications by creating variables and calling them in your notification templates.
