---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-02-17"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Broadcast notifications 
{: #broadcast_notifications}

Broadcast notifications are messages targeted to all instances of an application installed across mobile devices, browsers or implemented as Chrome apps or extension instances and configured for the {{site.data.keyword.mobilepushshort}} service. Broadcast notifications are enabled by default for any application enabled for {{site.data.keyword.mobilepushshort}}.

When a client application registers itself with {{site.data.keyword.mobilepushshort}} service, it can start to receive broadcasts. Applications enabled for {{site.data.keyword.mobilepushshort}} service has a predefined subscription to the Push.ALL tag, which is used by server to broadcast notification messages to all devices. To send a broadcast notification that uses the REST Push API, ensure that the "target" is an empty JSON file when posting to the messages resource.
