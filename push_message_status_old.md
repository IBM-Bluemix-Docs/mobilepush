---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-05-30"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Message notification delivery status
{: #tag_based_notifications}

With the {{site.data.keyword.mobilepushshort}} service, you can view the status of every notification that has been submitted to the service. 

A message that has been submitted might have the following status:

- **Accepted**: The message has been accepted for delivery by the Push Notifications service.
- **Processing**: The message is being processed, to be dispatched to the notification provider gateway. A notification that is being processed can also return a failure with the status **Processing failed**.
- **Dispatching**: The notification has been received by notification provider - APNs, FCM, or Web, and is about to be dispatched. A notification that is in the process of being dispatched can also return a failure with the status **Dispatching failed**.
- **Dispatched**: The notification has been dispatched by the notification provider.
- **Unknown**: The status of the notification cannot be determined.

The {{site.data.keyword.mobilepushshort}} service Messages tab displays the notification status.

![notifications status](images/notification_status_new.png "Messages page showing notification status")

1. The **View** option displays delivery status of the notifications that are dispatched. You can view information based on the following aspects:

 - Category: All, Mobile, Web<!---and HTTP--->.
 - Message status: Sent, Seen, Open and Invalid. 

![notifications status](images/message_delivery_status_new.png "Message status chart showing open, sent, seen, and invalid status breakdown")

2. Click on **Options** to get **Detailed message delivery status**.  A detailed delivery status can be tracked by selecting either the `Device Id` or the `User Id` from the dropdown menu. A detailed status for a specific user or a device can be fetched.

![detailed status](images/detailed_message_delivery.png "Detailed message delivery status options with User ID selected")


At any given point of time, the service only displays status of only the latest 10 messages that is available within a period of 90 days.

**Note**: The feature is enabled only for users who have opted the `Advanced Pricing Plan`. Select **Plan** in the {{site.data.keyword.mobilepushshort}} service console to [upgrade](https://cloud.ibm.com/docs/account?topic=account-changing)
