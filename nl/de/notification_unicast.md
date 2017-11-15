---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Unicast-Benachrichtigungen
{: #notification_unicast}


Unicast-Benachrichtigungen sind Nachrichten, die ein bestimmtes Gerät oder einen bestimmten Benutzer zum Ziel haben. Unicast-Benachrichtigungen, die auf Geräte abzielen, benötigen keine zusätzliche Konfiguration und werden standardmäßig aktiviert, wenn die Anwendung für Push-Benachrichtigungen aktiviert wird.

Unicast-Benachrichtigungen an spezifische Benutzer erfordern zum Zeitpunkt der Registrierung des mobilen Clientgeräts oder Web-Browsers oder von Chrome-Apps und Erweiterungen bei {{site.data.keyword.mobilepushshort}} die Zuordnung einer Benutzer-ID zum Gerät.   

Normalerweise führt eine Clientanwendung zuerst einen Authentifizierungszyklus aus, bei dem der Benutzer der mobilen App bei einem Authentifizierungsservice wie [Mobile Client Access](docs/services/mobileaccess/index.html) authentifiziert wird. Nach der erfolgreichen Authentifizierung wird die ID des authentifizierten Benutzers dann an die API für Push-Geräteregistrierungen übergeben. 

Zum Senden einer Unicast-Benachrichtigung über die REST-API müssen Sie sicherstellen, dass während der Übergabe an die Ressource der Nachricht die Geräte- oder Benutzer-IDs ('deviceId' bzw. 'userId') angegeben werden.
