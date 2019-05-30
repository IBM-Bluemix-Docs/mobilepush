---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-05-30"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Activity Tracker Events
{: #push_activity_tracker}

The {{site.data.keyword.cloudaccesstrailfull}} service monitors a user's interaction with the IBM Cloud services. You can search and analyze how your users and applications interact with IBM Cloud services.

Cloud Administrators, Security and Developers can -

- **Gain insights into your environment to monitor and investigate security breaches**
    
	Capture user and application interactions with your provisioned IBM Cloud resources. Investigate possible security breaches or unauthorized access.
	
- **Achieve your regulatory, compliance and record retention needs**

    Store captured events as long as you require, safe guarded on cloud class economical storage solutions. Query your collected event data via API or export your cloud activity data.
	
- **Cloud transparency for your DevOps teams to debug and perform capacity planning**

    Cloud activity events provide transparency into your IT operations on the IBM Cloud. Identify when and how your Cloud services are used to isolate and debug your applications. Query collected data over time to anticipate your cloud growth and seasonal needs.	
	
- **Simplify collection and improve your cloud security**

    {{site.data.keyword.cloudaccesstrailshort}} automatically captures your IBM Cloud events.	


The {{site.data.keyword.cloudaccesstrailshort}} activity logs can be used to identify the following information:

- The users who made API calls to cloud services.
- The source IP address from where the API calls were made.
- The time-stamp when the API calls were made.
- The status of the API call.

## List of events
{: #actions}

The following table lists the {{site.data.keyword.cloudaccesstrailshort}} events for {{site.data.keyword.mobilepushshort}}
<table>
  <caption>Table 1. List of actions that genererate an event</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>Updates to the Application</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>Application configuration deletion</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>Application configuration update</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>Tag creation</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>Tag deletion</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>Tag update</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Webhook creation</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Webhook deletion</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Webhook update</td>
  </tr>   
</table>


For more information about working with {{site.data.keyword.cloudaccesstrailshort}}, refer the [documentation here](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}.

**Note:**
 - Currently, the Activity Tracker Events are available only on `IBM Cloud - US South Region`.