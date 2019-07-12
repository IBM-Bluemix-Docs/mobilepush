---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, faq, frequently asked questions

subcollection: mobile-pushnotification

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Häufig gestellte Fragen 
{: #faq}

### Warum werden meine Tokens inaktiviert?
{: #faq-tokens}	

Für Registrierungen von Geräten, Browsern sowie Chrome-Apps & Erweiterungen pflegt der Push Notifications-Service eine eindeutige Referenz auf Tokens, die von Benachrichtigungsprovidern ausgegeben werden (APNs für Apple bzw. FCM für Google). Der Benachrichtigungsprovider des Service kann diese Tokens aus diversen Gründen inaktivieren. 

Ein Beispiel wäre die Inaktivierung bei der Deinstallation einer App auf dem Gerät. Bei einem Szenario, bei dem der Versuch unternommen wird, eine Benachrichtigung auf Grundlage der Providerantwort über die Inaktivierung des Geräts zuzustellen, entfernt der {{site.data.keyword.mobilepushshort}}-Service die Geräte- oder Web-Browserregistrierungen. Dadurch werden wiederum nachfolgende Versuche, die Benachrichtigung an diese inaktivierten Geräte zu senden, blockiert. 

Dieses Problem kann ebenfalls auftreten, wenn sie die Registrierung für ein Gerät aufgehoben haben.

Stellen Sie sicher, dass Sie einen gültigen Server-API-Schlüssel und eine gültige Absender-ID abgerufen haben. Siehe [Berechtigungsnachweise des Benachrichtigungsproviders abrufen](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1).

### Warum wird die Nachricht angezeigt, dass Benachrichtigungen für WEB_Chrome nicht funktionieren, wenn das Web-Push-SDK initialisiert wird?
{: #faq-web-chrome}	

Wenn Ihre FCM-Berechtigungsnachweise für das Web-Push-SDK geändert werden, kann die Nachrichtenübermittlung für den Chrome-Browser fehlschlagen. Stellen Sie sicher, dass Sie *bmsPush.unRegisterDevice* aufrufen, um ein Fehlschlagen zu vermeiden.

### Bei der Initialisierung des Web-Push-SDK wird die Nachricht angezeigt, dass in diesem Browser keine Servicebearbeiter unterstützt werden. Was könnte das Problem sein? 
{: #faq-service-workers}	

Führen Sie die in [Schritt 3: Client-SDKs für Push-Service einrichten](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3) beschriebenen Schritte aus.	Stellen Sie außerdem Folgendes sicher:

1. Sie verwenden die richtige Startmethode. 
2. Sie haben die Datei `manifest.json` in den Stammordner eingefügt.
3. Ihre Website wird gehostet. Erstellen Sie am besten einen `node.js`-Starter in IBM Cloud, um es auszuprobieren. Beispiel: https://<mysamplewebsite>.cloud.ibm.com/.	

### Wie können Web-Push-Konfigurationsfehler behoben werden?
{: #faq-web-config-errors}	

Web-Push-Fehler aus der Datei `BMSPushSDK.js` enthalten Informationen zu dem Fehler.  Siehe [Fehlerbehebung](/docs/services/mobilepush?topic=mobile-pushnotification-errors).	

### Bleiben Benachrichtigungen bestehen, wenn die Geräte offline sind?
{: #faq-notification-persist}	

Dieses Feature ist abhängig vom Benachrichtigungsprovider.	

### Ist die Nachrichten-ID für eine Anwendung eindeutig, und was ist ihre Größe?
{: #faq-messageid}	

Die Nachrichten-ID ist für eine Anwendung eindeutig und ihre Größe ist auf acht Zeichen beschränkt. Die ID kann alphanumerisch sein.

### Welche Grenzwerte gelten für Push Notifications in Bezug auf die Nutzdatengröße?
{: #faq-limits-push-payload-size}	

Die Größe der {{site.data.keyword.mobilepushshort}}-Nachrichtennutzdaten hängt von den Einschränkungen ab, die durch die Gateways (FCM, APNs) und Clientplattformen festgelegt sind. 

Ab iOS 8 beträgt die zulässige maximale Größe 4 Kilobyte. Beachten Sie, dass APNs keine Benachrichtigungen sendet, die dieses Limit überschreiten. Bei Android, Firefox-Browser, Chrome-Browser und Chrome Apps & Erweiterungen gibt es eine Einschränkung von 4 Kilobyte als maximal zulässige Nachrichtennutzdatengröße.	

### Werden gesendete Benachrichtigungen in BMS-Servern gespeichert?
{: #faq-bms-servers}	

Ja, die Benachrichtigungen werden für einen Zeitraum von 90 Tagen gespeichert. Es wird empfohlen, keine vertraulichen Nachrichten als Benachrichtigungen zu senden.

### Können im Ruhemodus Benachrichtigungen an Geräte gesendet werden?
{: #faq-doze-mode}	

Dieses Feature wird nicht unterstützt.	

### Wie sehen die verschiedenen Preistarife für den Push Notifications-Service aus?
{: #faq-pricing-plans}	

* <b>Erweiterter Plan</b>: Verfügbar für 100,00 USD/Instanz, 0,50 USD/Million digitaler Nachrichten und 0,50 USD/Million adressierbarer Geräte. Mit dem erweiterten Plan können Push-Benachrichtigungen an 1 Million addressierbare Geräte und 100 Millionen digitale Nachrichten gesendet werden. Der erweiterte Plan umfasst Funktionen wie das Parametrisieren von Nachrichten und die End-to-End-Verfolgung des Nachrichtenlebenszyklus.

* <b>Basic-Plan</b>: Verfügbar für 1,00 USD/Million digitaler Nachrichten. Mit dem Basic-Plan können Push-Benachrichtigungen an eindeutige Geräte, Browser, Endpunkte oder Webhook-Ereignisse gesendet werden. 

* <b>Lite-Plan</b>: Plan zur kostenfreien Nutzung mit 100.000 kostenfreien digitalen Nachrichten pro Monat. Services im Rahmen eines Lite-Plans werden jedoch nach einem Inaktivitätszeitraum von 30 Tagen gelöscht.	

### Wo finde ich weitere Informationen wie Lernprogramme oder Neuerungen?
{: #faq-what-is-new}	

Sehen Sie sich die [Videos](https://www.youtube.com/watch?v=1wO30GfiLaI&list=PLzJUGEaRNMfvX7-J6gqczEanWBPiOjEmA) für den Push Notifications-Service an.	

### Gibt es einen Unterschied zwischen einer Benachrichtigung und einer Nachricht?
{: #faq-diff-notification-message}	

Ja. Eine _Nachricht_ ist das, was vom Benutzer an den {{site.data.keyword.mobilepushshort}}-Service übermittelt wird. Der Service sendet diese Nachricht als _Benachrichtigung_ an das Benachrichtigungsgateway (APNs/FCM), das die Benachrichtigung dann an das Gerät oder den Web-Browser sendet.

Für jede an den Service übermittelte Nachricht wird an die jeweilige Zielgruppe eine Benachrichtigung gesendet.	

### Enthält das Push Notifications-Überwachungsdashboard Statusangaben zu gesendeten Nachrichten?
{: #faq-push-monitor-dashboard}	

Der Überwachungsdienstprogramm zeigt den Status für jede gesendete Nachricht an. Nachrichten können die folgenden Status aufweisen:
	
* SENT: Die Anzahl der Geräte, an die Benachrichtigungen gesendet werden.
* SEEN: Die Anzahl der Geräte, die Benachrichtigungen empfangen haben.
* OPEN: Die Anzahl der Geräte, auf denen Benachrichtigungen geöffnet wurden.
* INVALID: Die Anzahl der Geräte, auf denen das Token ungültig ist.

Weitere Informationen finden Sie im Bericht zu GET-Nachrichten in [IBM Push Notifications: REST-API](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).	

### Überwacht Push Notifications die Zustellung von Push-Benachrichtigungen bis zum Gerät des Endbenutzers? Gilt dies für Android und für iOS?
{: #faq-end-user-device}	

Push-Benachrichtigungen werden basierend auf der Anzahl der Benachrichtigungen überwacht, die auf dem Endbenutzergerät angezeigt oder geöffnet werden. Diese Funktionalität ist sowohl für Android als auch für iOS verfügbar. Eine auf der Geräte-ID basierende Überwachung wird nicht unterstützt. 

### Es wird eine Nachricht angezeigt, dass der Server derzeit keine Anforderungen verarbeiten kann. Wie kann ich dieses Problem beheben?
{: #faq-server-unable-to-handle-requests}	

Möglicherweise wird der Fehler mit dem Fehlercode FPWSE0025E angezeigt. Dieses Problem kann darauf zurückzuführen sein, dass der Server zu viele Anforderungen verarbeiten muss. Wiederholen Sie die Anforderung zu einem späteren Zeitpunkt.	

### Ich sende Benachrichtigungen nach Tags, habe aber eine lange Liste mit Tags, und das manuelle Hinzufügen dieser Tags könnte schwierig sein. 
{: #faq-tag-based-notification}	

Sie können REST-APIs verwenden, um das Hinzufügen von Tag zu automatisieren. Siehe [POST-Massennachrichten](https://eu-gb.imfpush.cloud.ibm.com/imfpush/).

### Wie kann die Zustellung von Push-Benachrichtigungen nach Informationen gefiltert werden, die im Mobilgerät des Benutzers gespeichert sind?
{: #faq-filter-device}	

Diese Fragestellung sollte im Rahmen der Anwendungsentwicklung behandelt werden.

### Kann die Überwachung von Push-Benachrichtigungen angepasst werden, um angepasste Berichte wie beispielsweise Zustellungsberichte pro Segmentierung hinzuzufügen?
{: #faq-customize-delivery-report}	

Dieses Feature wird nicht unterstützt.

### Ist es möglich, für einen neuen App-Benutzer oder für Benutzer, die eine Zeit lang nicht auf die mobile App zugegriffen haben, ein Segment zu erstellen?
{: #faq-create-segment}	

Diese Fragestellung sollte im Rahmen der Anwendungsentwicklung behandelt werden.
	
### Kann ich mobile Geräte über die REST-APIs massenweise registrieren/aktualisieren?
{: #faq-register-mobile-devices}	

Die Registrierung/Aktualisierung eines Geräts ist so konzipiert, dass sie per SDK von den mobilen Anwendungen aufgerufen wird. Massenregistrierungen/-aktualisierungen über REST-APIs werden nicht unterstützt. Werden viele Registrierungen/Aktualisierungen gleichzeitig über REST-APIs aufgerufen, kann dies lange dauern oder fehlschlagen.	

### Wie kann ich Push-Benachrichtigungen senden oder die Rest-APIs verwenden, wenn ich den geheimen App-Schlüssel (appSecret) nicht habe?
{: #faq-rest-api-appsecret}	

Da der {{site.data.keyword.mobilepushshort}}-Service IAM angenommen hat, wird ein API-Schlüssel (`apiKey`) anstelle des geheimen App-Schlüssels (`appSecret`) angezeigt, wenn der Benutzer die Serviceberechtigungsnachweise erstellt.

Damit Sie REST-APIs verwenden können, müssen Sie das Zugriffstoken mit dem folgenden curl-Befehl generieren:

```
curl -k -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" "https://iam.cloud.ibm.com/identity/token"
```

```
{
 "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```
{: codeblock}

Nach dem Generieren des Zugriffstokens mit dem oben genannten curl-Befehl können Sie die REST-API betreiben, indem Sie `Bearer <value of access_token>` im Berechtigungsheader übergeben.

Beispiel:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \
   "message": { \
     "alert": "Notification alert message" \
   } \
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```	
