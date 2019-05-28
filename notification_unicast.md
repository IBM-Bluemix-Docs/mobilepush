---

copyright:
  years: 2015, 2017, 2019
lastupdated: "28 May 2019"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Unicast notifications
{: #notification_unicast}

Unicast notifications are messages targeted to a particular device or user. Unicast notifications targeted to devices does not require any additional setup and are enabled by default when the application is enabled for {{site.data.keyword.mobilepushshort}}.

However, Unicast notifications targeted at users require associating a user ID with a device at the time of registering the client mobile device or web browser or Chrome Apps and Extensions for {{site.data.keyword.mobilepushshort}}.   

Typically, a client application will first run an authentication cycle where the mobile app user is authenticated against a authentication service like Mobile Client Access. On successful authentication, the authenticated user ID is then passed into the Push Device Registration API. 

To send a Unicast notifications through REST API, ensure that the deviceIds or userIds are provided when posting to a message resource.
