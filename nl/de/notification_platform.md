---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Plattformbasierte Benachrichtigungen
{: #notification_platform}


Benachrichtigungen können zielgruppenspezifisch an eine bestimmte Geräteplattform gerichtet werden. Eine Benachrichtigung kann beispielsweise nur an alle Android-Benutzer oder an alle Google Chrome-Benutzer gesendet werden. Stellen Sie zum Senden einer plattformbasierten Benachrichtigung mithilfe der REST-API sicher, dass die Zielplattformen während der Übergabe an eine Nachrichtenressource bereitgestellt werden. Geben Sie die Plattformen als Array an. Folgende Plattformen werden unterstützt:

* A (Apple)
* G (Google)
* WEB_CHROME (Google Chrome-Browser Web Push)
* WEB_FIREFOX (Mozilla Firefox-Browser Web Push)
* WEB_SAFARI (Safari-Browser Web Push)
* APPEXT_CHROME (Google Chrome-Apps & Erweiterungen)
