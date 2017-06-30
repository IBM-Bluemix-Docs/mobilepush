---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Platform-based notifications
{: #notification_platform}


Notifications can be targeted to reach a particular device platform. For example, a notification can be sent to all Android users or Google Chrome users only. To send a platform-based notification that uses the REST API, make sure that the targeted platforms are provided when posting to a message resource. Specify the platforms as an array. The supported platforms are as follows:

* A (Apple)
* G (Google)
* WEB_CHROME (Google Chrome Browser Web Push)
* WEB_FIREFOX (Mozilla Firefox Browser Web Push)
* WEB_SAFARI (Safari Browser Web Push)
* APPEXT_CHROME (Google Chrome Apps & Extensions)