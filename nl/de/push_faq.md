---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Häufig gestellte Fragen 
{: #faq}


1. Warum werden meine Tokens inaktiviert?
	
	Für Registrierungen von Geräten, Browsern sowie Chrome-Apps & Erweiterungen pflegt der Push Notifications-Service eine eindeutige Referenz auf Tokens, die von Benachrichtigungsprovidern ausgegeben werden (APNs für Apple bzw. FCM für Google). Der Benachrichtigungsprovider des Service kann diese Tokens aus diversen Gründen inaktivieren. 

	Ein Beispiel wäre die Inaktivierung bei der Deinstallation einer App auf dem Gerät. Bei einem Szenario, bei dem der Versuch unternommen wird, eine Benachrichtigung auf Grundlage der Providerantwort über die Inaktivierung des Geräts zuzustellen, entfernt der {{site.data.keyword.mobilepushshort}}-Service die Geräte- oder Web-Browserregistrierungen. Dadurch werden wiederum nachfolgende Versuche, die Benachrichtigung an diese inaktivierten Geräte zu senden, blockiert. 

	Dieses Problem kann ebenfalls auftreten, wenn sie die Registrierung für ein Gerät aufgehoben haben.

	Stellen Sie sicher, dass Sie einen gültigen Server-API-Schlüssel und eine gültige Absender-ID abgerufen haben. Siehe [Berechtigungsnachweise des Benachrichtigungsproviders abrufen](push_step_1.html).


2. Warum wird die Nachricht angezeigt, dass Benachrichtigungen für WEB_Chrome nicht funktionieren, wenn das Web-Push-SDK initialisiert wird?

	Wenn Ihre FCM/GCM-Berechtigungsnachweise für das Web-Push-SDK geändert werden, kann die Nachrichtenübermittlung für den Chrome-Browser fehlschlagen. Stellen Sie sicher, dass Sie 'bmsPush.unRegisterDevice' aufrufen, um ein Fehlschlagen zu vermeiden.

3. Bei der Initialisierung des Web-Push-SDK wird die Nachricht angezeigt, dass in diesem Browser keine Servicebearbeiter unterstützt werden. Was könnte das Problem sein? 

	Führen Sie die in [Schritt 3: Client-SDKs für Push-Service einrichten](push_step_3.html) beschriebenen Schritte aus.	Stellen Sie außerdem Folgendes sicher:
 
	1. Sie verwenden die richtige Startmethode. 
	1. Sie haben die Datei `manifest.json` in den Stammordner eingefügt.
	1. Ihre Website wird gehostet. Erstellen Sie am besten einen `node.js`-Starter in IBM Cloud, um es auszuprobieren. Beispiel: https://<mysamplewebsite>.mybluemix.net/.	

4. Wie können Web-Push-Konfigurationsfehler behoben werden?

	Web-Push-Fehler aus der Datei `BMSPushSDK.js` enthalten Informationen zu dem Fehler.  Siehe [Fehlerbehebung](push_troubleshooting.html).	

5. Bleiben Benachrichtigungen bestehen, wenn die Geräte offline sind?

	Dieses Feature ist abhängig vom Benachrichtigungsprovider.	

6. Ist die Nachrichten-ID für eine Anwendung eindeutig, und was ist ihre Größe?

	Die Nachrichten-ID ist für eine Anwendung eindeutig und ihre Größe ist auf acht Zeichen beschränkt. Die ID kann alphanumerisch sein.

7. Welche Grenzwerte gelten für Push Notifications in Bezug auf die Nutzdatengröße?

	Die Größe der {{site.data.keyword.mobilepushshort}}-Nachrichtennutzdaten hängt von den Einschränkungen ab, die durch die Gateways (FCM/GCM, APNs) und Clientplattformen festgelegt sind. 

	Ab iOS 8 beträgt die zulässige maximale Größe 4 Kilobyte. Beachten Sie, dass APNs keine Benachrichtigungen sendet, die dieses Limit überschreiten. Bei Android, Firefox-Browser, Chrome-Browser und Chrome Apps & Erweiterungen gibt es eine Einschränkung von 4 Kilobyte als maximal zulässige Nachrichtennutzdatengröße.	

8. Werden gesendete Benachrichtigungen in BMS-Servern gespeichert?

	Ja, die Benachrichtigungen werden für einen Zeitraum von sieben Tagen gespeichert. Es wird empfohlen, keine vertraulichen Nachrichten als Benachrichtigungen zu senden.

9. Können im Ruhemodus Benachrichtigungen an Geräte gesendet werden?

	Dieses Feature wird nicht unterstützt.	

10. Wie sehen die verschiedenen Preistarife für den Push Notifications-Service aus?

	Basisplan: Verfügbar für 1,00 USD/Million digitaler Nachrichten. Mit dem Basic-Plan können Push-Benachrichtigungen an eindeutige Geräte, Browser, Endpunkte oder Webhook-Ereignisse gesendet werden. 

	Lite-Plan: Plan zur kostenfreien Nutzung mit 100.000 kostenfreien digitalen Nachrichten pro Monat. Services im Rahmen eines Lite-Plans werden jedoch nach einem Inaktivitätszeitraum von 30 Tagen gelöscht.	

11. Wo finde ich weitere Informationen wie Lernprogramme oder Neuerungen?

	Lesen Sie den [Blog](http://push-notification-service.mybluemix.net/) für den Push Notifications-Service.	

12. Gibt es einen Unterschied zwischen einer Benachrichtigung und einer Nachricht?

	Ja. Eine _Nachricht_ ist das, was vom Benutzer an den {{site.data.keyword.mobilepushshort}}-Service übermittelt wird. Der Service sendet diese Nachricht als _Benachrichtigung_ an das Benachrichtigungsgateway (APNs/FCM), das die Benachrichtigung dann an das Gerät oder den Web-Browser sendet.

	Für jede an den Service übermittelte Nachricht wird an die jeweilige Zielgruppe eine Benachrichtigung gesendet.	

13. Enthält das Push Notifications-Überwachungsdashboard Statusangaben zu gesendeten Nachrichten?

	Der Überwachungsdienstprogramm zeigt den Status für jede gesendete Nachricht an. Nachrichten können die folgenden Status aufweisen:
	
	- SENT: Die Anzahl der Geräte, an die Benachrichtigungen gesendet werden.
	- SEEN: Die Anzahl der Geräte, die Benachrichtigungen empfangen haben.
	- OPEN: Die Anzahl der Geräte, auf denen Benachrichtigungen geöffnet wurden.
	- INVALID: Die Anzahl der Geräte, auf denen das Token ungültig ist.

	Weitere Informationen finden Sie im Bericht zu GET-Nachrichten in [IBM Push Notifications: REST-API](https://mobile.ng.bluemix.net/imfpush/).	

14. Überwacht Push Notifications die Zustellung von Push-Benachrichtigungen bis zum Gerät des Endbenutzers? Gilt dies für Android und für iOS?

	Push-Benachrichtigungen werden basierend auf der Anzahl der Benachrichtigungen überwacht, die auf dem Endbenutzergerät angezeigt oder geöffnet werden. Diese Funktionalität ist sowohl für Android als auch für iOS verfügbar. Eine auf der Geräte-ID basierende Überwachung wird nicht unterstützt. 

15. Es wird eine Nachricht angezeigt, dass der Server derzeit keine Anforderungen verarbeiten kann. Wie kann ich dieses Problem beheben?

	Möglicherweise wird der Fehler mit dem Fehlercode FPWSE0025E angezeigt. Dieses Problem kann darauf zurückzuführen sein, dass der Server zu viele Anforderungen verarbeiten muss. Wiederholen Sie die Anforderung zu einem späteren Zeitpunkt.	

16. Ich sende Benachrichtigungen nach Tags, habe aber eine lange Liste mit Tags, und das manuelle Hinzufügen dieser Tags könnte schwierig sein. 
	
	Sie können REST-APIs verwenden, um das Hinzufügen von Tag zu automatisieren. Siehe [POST-Massennachrichten](https://mobile.ng.bluemix.net/imfpush/).

17. Wie kann die Zustellung von Push-Benachrichtigungen nach Informationen gefiltert werden, die im Mobilgerät des Benutzers gespeichert sind?

	Diese Fragestellung sollte im Rahmen der Anwendungsentwicklung behandelt werden.

18. Kann die Überwachung von Push-Benachrichtigungen angepasst werden, um angepasste Berichte wie beispielsweise Zustellungsberichte pro Segmentierung hinzuzufügen?

	Dieses Feature wird nicht unterstützt.

19.  Ist es möglich, für einen neuen App-Benutzer oder für Benutzer, die eine Zeit lang nicht auf die mobile App zugegriffen haben, ein Segment zu erstellen?

	Diese Fragestellung sollte im Rahmen der Anwendungsentwicklung behandelt werden.


	


	
	




	


