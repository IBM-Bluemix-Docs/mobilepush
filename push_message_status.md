---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Message notification delivery status
{: #tag_based_notifications}
Last updated: 21 August 2017
{: .last-updated}


With the {{site.data.keyword.mobilepushshort}} service, you can view the status of every notification that has been submitted to the service. 

A message that has been submitted might have the following status:

- **Accepted**: The message has been accepted for delivery by the Push Notifications service.
- **Processing**: The message is being processed, to be dispatched to the notification provider gateway. A notification that is being processed can also return a failure with the status **Processing failed**.
- **Dispatching**: The notification has been received by notification provider - APNs, FCM, or Web, and is about to be dispatched. A notification that is in the process of being dispatched can also return a failure with the status **Dispatching failed**.
- **Dispatched**: The notification has been dispatched by the notification provider.
- **Unknown**: The status of the notification cannot be determined.

The {{site.data.keyword.mobilepushshort}} service Messages tab displays the notification status.

![notifications status](images/notification_status.jpg)

The **View** option displays delivery status of the notifications that are dispatched. You can view information based on the following aspects:

- Category: All, Mobile, Web<!---and HTTP--->.
- Message status: Sent, Seen, Open and Invalid. 

![notifications status](images/message_delivery_status.jpg)


Note that at any given point of time, the service only displays status of only the latest 10 messages that is available within a period of 90 days.


