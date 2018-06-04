---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Interaktive Benachrichtigungen und Hintergrundbenachrichtigungen  
{: #interactive-notifications}
Letzte Aktualisierung: 22. Mai 2017
{: .last-updated}

Interaktive Benachrichtigungen ermöglichen den Benutzern das Beantworten einer Benachrichtigung, ohne die Anwendung zu öffnen. Wenn eine interaktive Benachrichtigung eingeht, zeigt das Gerät die Aktionsschaltflächen zusammen mit der Benachrichtigung an. 

**Hinweis:** Interaktive Benachrichtigungen werden auf iOS-Geräten mit Versionen vor Version 8 nicht unterstützt. 

## Interaktive Benachrichtigungen senden
{: #send_interactive_notifications}

Interaktive Benachrichtigungen können über die Push Notifications-Konsole oder mithilfe der REST-API (siehe [REST-API-Dokumentation](push_restapi.html)) gesendet werden.


Gehen Sie in der {{site.data.keyword.mobilepushshort}}-Konsole wie folgt vor: 

1. Klicken Sie auf der Registerkarte 'Benachrichtigungen' auf **Benachrichtigung senden**. 
2. Wählen Sie die Benachrichtigungsempfänger aus und klicken Sie auf **Weiter**. 
3. Auf der Seite für die Benachrichtigungserstellung können Sie beim Senden von interaktiven Push-Benachrichtigungen den Typ 'Standard' oder 'Gemischt' festlegen und auf der Registerkarte mit den erweiterten Optionen den Kategoriewert angeben. 

## Interaktive Benachrichtigungen verarbeiten 
{: #handle_interactive_notifications}

- iOS: Lesen Sie die Informationen zur [Aktivierung und Verarbeitung interaktiver Benachrichtigungen bei Swift-Anwendungen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications).
- Cordova: Lesen Sie die Informationen zur [Aktivierung und Verarbeitung interaktiver Benachrichtigungen bei Cordova-Anwendungen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications).
- Android: Lesen Sie die Informationen zur [Aktivierung und Verarbeitung interaktiver Benachrichtigungen bei Android-Anwendungen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications).


## Hintergrundbenachrichtigungen für iOS verarbeiten
{: #send_silent_notifications_for_ios}

Hintergrundbenachrichtigungen werden nicht auf dem Gerät angezeigt und von der Anwendung im Hintergrund empfangen. Weitere Informationen finden Sie in [Hintergrundbenachrichtigungen auf iOS-Geräten](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification).
