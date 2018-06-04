---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Benachrichtigungsübermittlungsstatus von Nachrichten
{: #tag_based_notifications}
Letzte Aktualisierung: 21. August 2017
{: .last-updated}


Mit dem {{site.data.keyword.mobilepushshort}}-Service können Sie den Status jeder Benachrichtigung anzeigen, die an den Service übergeben wurde. 

Für eine an den Service übergebene Nachricht sind die folgenden Statusangaben möglich:

- **Akzeptiert**: Die Nachricht wurde vom Push Notifications-Service zur Übermittlung akzeptiert.
- **Verarbeitung wird ausgeführt**: Die Nachricht wird verarbeitet und demnächst an das Gateway des Benachrichtigungsproviders gesendet. Für eine Benachrichtigung, die zum aktuellen Zeitpunkt verarbeitet wird, kann auch ein Fehler zurückgegeben werden (Status **Verarbeitung fehlgeschlagen**.
- **Zuteilung wird ausgeführt**: Die Benachrichtigung wurde vom Benachrichtigungsprovider - APNs, FCM oder Web - empfangen und wird demnächst zum Versand zugeteilt. Für eine Benachrichtigung, für die zum aktuellen Zeitpunkt eine Zuteilung ausgeführt wird, kann auch ein Fehler zurückgegeben werden (Status **Zuteilung fehlgeschlagen**.
- **Zugeteilt**: Die Benachrichtigung wurde durch den Benachrichtigungsprovider zum Versand zugeteilt.
- **Unbekannt**: Der Status der Benachrichtigung kann nicht bestimmt werden.

Auf der Registerkarte 'Nachrichten' des {{site.data.keyword.mobilepushshort}}-Service wird der Benachrichtigungsstatus angezeigt.

![Benachrichtigungsstatus](images/notification_status_new.png)

1. Mit der Option **Anzeigen** wird der Übermittlungsstatus der zum Versand zugeteilten Benachrichtigung angezeigt. Informationen können auf der Basis der folgenden Aspekte angezeigt werden:

 - Kategorie: Alle, Mobile, Web<!---and HTTP--->.
 - Nachrichtenstatus: Gesendet (SENT), Gesehen (SEEN), Geöffnet (OPEN) und Ungültig (INVALID). 

![Benachrichtigungsstatus](images/message_delivery_status_new.png)

2. Klicken Sie auf **Optionen**, um den **Detaillierten Übermittlungsstatus von Nachrichten** abzurufen. Zur Verfolgung des detaillierten Übermittlungsstatus kann entweder die `Geräte-ID` oder die `Benutzer-ID` im Dropdown-Menü ausgewählt werden. Es kann ein detaillierter Status für einen bestimmten Benutzer oder ein bestimmtes Gerät abgerufen werden.

![Detaillierter Status](images/detailed_message_delivery.png)


Zu jedem beliebigen Zeitpunkt zeigt der Service nur den verfügbaren Status der 10 neuesten Nachrichten innerhalb eines Zeitraums von 90 Tagen an.

**Hinweis**: Das Feature ist nur für Benutzer aktiviert, die den `Erweiterten Preissturkturplan` ausgewählt haben. Wählen Sie **Plan** in der {{site.data.keyword.mobilepushshort}}-Servicekonsole aus, um ein [Upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing) durchzuführen.
