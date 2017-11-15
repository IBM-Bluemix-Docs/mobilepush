---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Broadcastbenachrichtigungen 
{: #broadcast_notifications}

Broadcastbenachrichtigungen sind Benachrichtigungen mit all jenen Anwendungsinstanzen als Ziel, die in verschiedenen Mobilgeräten oder Browsern installiert oder als Instanzen von Chrome-Apps oder Erweiterungen implementiert sind und für den {{site.data.keyword.mobilepushshort}}-Service konfiguriert wurden. Broadcastbbenachrichtigungen sind standardmäßig für jede beliebige Anwendung aktiviert, die Push-Benachrichtigungen empfangen kann.

Wenn sich eine Clientanwendung beim {{site.data.keyword.mobilepushshort}}-Service registriert, kann sie Rundsendungen (Broadcasts) empfangen. Alle Anwendungen, die für den {{site.data.keyword.mobilepushshort}}-Service aktiviert sind, verfügen über eine vordefinierte Subskription für den Tag 'Push.ALL', der vom Server zum Übertragen von Broadcastbenachrichtigungen an alle Geräte verwendet wird. Zum Senden einer Broadcastbenachrichtigung mithilfe der REST-API von Push müssen Sie während der Übergabe an die Ressource der Nachrichten sicherstellen, dass als 'Ziel' eine leere JSON-Datei angegeben ist.
