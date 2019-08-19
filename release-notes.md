---

copyright:
  years: 2015, 2017, 2018, 2019
lastupdated: "2019-08-07"

keywords: push notifications, notifications, release notes

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Release notes

The following new features and changes to the service are available. These changes do not break existing code:

## July 2019

### Application Server Keys Support
 
Application Server Keys are used to authenticate the application server. (This is defined by the VAPID spec.) This key is used to provide additional security to verify that the application server triggering the web push message is same as the one subscribed by the user.

## February 2019

### React Native

React Native SDK released to support react native applications for IBM Cloud Push Notifications Service.

## August 2018

### PWA Support

Progressive Web Application support introduced for Web push notifications.

## June 2018

### Managing access to Push Notifications through IBM Cloud Identity and Access Management (IAM)

As an account owner, you can set policies within your account to create different levels of access for different users using [IAM](/docs/services/mobilepush?topic=mobile-pushnotification-service-access-management).

### Activity Tracker

You can monitor a user's interaction with the Push Notifications service. You can search and analyze how your users and applications [interact with the service](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker).

## May 2018

### Resource Controller (RC) based service

IBM Push Notifications service is now a RC based service. Service instances should be created using a Resource controller.

## March 2018

### Track the message delivery status

You can view the delivery status of every notification that has been submitted to the service. 

### Parameterize Notifications

You can parameterize and send custom notifications by creating variables and calling them in your notification templates.
	
