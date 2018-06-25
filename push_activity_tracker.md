----

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Activity Tracker Events
{: #push_activity_tracker}
Last updated: 22 June 2018
{: .last-updated}

The {{site.data.keyword.cloudaccesstrailfull}} service monitors a user's interaction with the IBM Cloud services. You can search and analyze how your users and applications interact with IBM Cloud services.

Your Cloud Administrators, Security and Developers can -

- **Gain insights into your environment to monitor and investigate security breaches**
    
	Capture user and application interactions with your provisioned IBM Cloud resources. Investigate possible security breaches or unauthorized access.
	
- **Achieve your regulatory, compliance and record retention needs**

    Store captured events as long as you require, safe guarded on cloud class economical storage solutions. Query your collected event data via API or export your cloud activity data.
	
- **Cloud transparency for your DevOps teams to debug and perform capacity planning**

    Cloud activity events provide transparency into your IT operations on the IBM Cloud. Identify when and how your Cloud services are used to isolate and debug your applications. Query collected data over time to anticipate your cloud growth and seasonal needs.	
	
- **Simplify collection and improve your cloud security**

    {{site.data.keyword.cloudaccesstrailshort}} automatically captures your IBM Cloud events.	


For example, you can use the {{site.data.keyword.cloudaccesstrailshort}} activity logs to identify the following information:

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
    <td>app.create</td>
	  <td> Creation of an Application </td>
  </tr>
  <tr>
    <td>app.delete</td>
	  <td>Deletion of an Application</td>
  </tr>
  <tr>
    <td>app.update</td>
	  <td>Updates to the Application</td>
  </tr>
  <tr>
    <td>app.conf.delete</td>
	  <td>Application configuration deletion</td>
  </tr>
  <tr>
    <td>app.conf.update</td>
	  <td>Application configuration update</td>
  </tr>
  <tr>
    <td>tag.create</td>
	  <td>Tag creation</td>
  </tr>
  <tr>
    <td>tag.delete</td>
	  <td>Tag deletion</td>
  </tr>
  <tr>
    <td>tag.update</td>
	  <td>Tag update</td>
  </tr>  
  <tr>
    <td>webhook.create</td>
	  <td>Webhook creation</td>
  </tr> 
  <tr>
    <td>webhook.delete</td>
	  <td>Webhook deletion</td>
  </tr>   
  <tr>
    <td>webhook.update</td>
	  <td>Webhook update</td>
  </tr>   
</table>


For more information about working with {{site.data.keyword.cloudaccesstrailshort}}, refer the documentation [here](https://console.bluemix.net/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov){: new_window}.