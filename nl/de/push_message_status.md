---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Nachrichtenübermittlungsstatus
{: #tag_based_notifications}
Letzte Aktualisierung: 21. August 2017
{: .last-updated}


Mit dem {{site.data.keyword.mobilepushshort}}-Service können Sie den Übermittlungsstatus jeder Benachrichtigung anzeigen, die an den Service übergeben wurde. 

Nach dem Absenden einer Nachricht können Sie die Zustellinformationen der Nachricht verfolgen, indem Sie ihren Übermittlungsstatus anzeigen. Zu jedem beliebigen Zeitpunkt zeigt der Service nur den verfügbaren Status der 10 neuesten Nachrichten innerhalb eines Zeitraums von 90 Tagen an.

Auf der Registerkarte **Nachrichten** des {{site.data.keyword.mobilepushshort}}-Service wird der Benachrichtigungsstatus angezeigt.

![Benachrichtigungsstatus](images/notification_status_new.png)

1. **Nachrichten-ID** - Eindeutige ID zur Identifizierung einer Nachricht.

2. **Nachrichtentext** - Nachrichtenvorlage, die an die App-Benutzer gesendet wurde.

3. **Datum** - Zeitpunkt (Datum und Uhrzeit), an dem die Nachricht an den Service übergeben wurde.

4. **Status** - Kurzer Zusammenfassungsstatus einer Nachricht. Abhängig vom Übermittlungsstatus der Nachricht kann eine der folgenden Statusinformationen angezeigt werden:

 - Akzeptiert: Die Nachricht wurde vom Push Notifications-Service zur Übermittlung akzeptiert.
   
 - Zuteilung wird ausgeführt: Die Benachrichtigung wurde vom Benachrichtigungsprovider - APNs, FCM oder Web - empfangen und wird demnächst zum Versand zugeteilt. Für eine Benachrichtigung, für die zum aktuellen Zeitpunkt eine Zuteilung ausgeführt wird, kann auch ein Fehler zurückgegeben werden (Status **Zuteilung fehlgeschlagen**.
 
 - Zugeteilt: Die Benachrichtigung wurde durch den Benachrichtigungsprovider zum Versand zugeteilt.
 
 - Verarbeitung wird ausgeführt: Die Nachricht wird verarbeitet und demnächst an das Gateway des Benachrichtigungsproviders gesendet. Für eine Benachrichtigung, die zum aktuellen Zeitpunkt verarbeitet wird, kann auch ein Fehler zurückgegeben werden (Status **Verarbeitung fehlgeschlagen**.
 
 - Unbekannt: Der Status der Benachrichtigung kann nicht bestimmt werden.
 
5. **Anzeigen** - Zeigt den Übermittlungsstatus der zum Versand zugeteilten Benachrichtigung an. Informationen können auf der Basis der folgenden Aspekte angezeigt werden:

 - Kategorie: Alle, Mobile, Web<!---and HTTP--->.
 
 - Nachrichtenstatus: Gesendet (SENT), Gesehen (SEEN), Geöffnet (OPEN) und Ungültig (INVALID). 

![Benachrichtigungsstatus](images/message_delivery_status_new.png)

6. **Optionen** - Zeigt einen detaillierten Status einer Benachrichtigung an. Zur Verfolgung des Status kann entweder die `Geräte-ID` oder die `Benutzer-ID` im Dropdown-Menü ausgewählt werden. Eine detaillierte benutzer- oder gerätespezifische Statusnachricht kann bei der Verfolgung einer fehlgeschlagenen Nachricht nützlich sein.

![Detaillierter Status](images/detailed_message_delivery.png)

**Hinweis**: Das Feature ist nur für Benutzer aktiviert, die den `Erweiterten Plan` ausgewählt haben. Wählen Sie **Plan** in der {{site.data.keyword.mobilepushshort}}-Servicekonsole aus, um ein [Upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing) durchzuführen.


