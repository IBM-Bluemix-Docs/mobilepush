---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, user-based, register device with user ID, synchronize user login and logout

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Benutzerbasierte Benachrichtigungen
{: #user_based_notifications}

Auf Benutzer-ID basierte {{site.data.keyword.mobilepushshort}} (Push-Benachrichtigungen) zielen mit angepassten Nachrichten auf Benutzer mobiler Apps ab. Bei benutzerbasierten Benachrichtigungen können Sie auswählen, dass bestimmte Personen auf Grundlage Ihrer Vorgaben benachrichtigt werden.

## Gerät mit Benutzer-ID registrieren
{: #register_device_wh_userid}

Um Push-Benachrichtigungen zu aktivieren, die auf einer Benutzer-ID basieren, müssen Sie sicherstellen, dass Sie das Gerät mit einer Benutzer-ID registrieren.     

Die Benutzer-ID kann eine beliebige Zeichenfolge sein, die die Anwendung gegenüber der API für die Geräteregistrierung bereitstellt. Normalerweise führt eine mobile Anwendung zuerst einen Authentifizierungszyklus aus, in dessen Verlauf der Benutzer mobiler Apps bei einem Authentifizierungsservice wie {{site.data.keyword.amafull}} authentifiziert wird. Nach der erfolgreichen Authentifizierung wird die ID des authentifizierten Benutzers dann an die API für Push-Geräteregistrierungen übergeben. 

Führen Sie die folgenden Schritte aus, um eine Registrierung für die auf Benutzer-IDs basierende Benachrichtigung durchzuführen:

- [Android-Anwendung registrieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [iOS-Anwendung registrieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Cordova-Anwendung registrieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Webanwendung registrieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## Benachrichtigungen, die auf einer Benutzer-ID basieren
{: #using_userid}

Die Benachrichtigungen, die auf einer Benutzer-ID basieren, sind Benachrichtigungsnachrichten, deren Ziel ein bestimmter Benutzer ist. Viele Geräte können mit einem einzigen Benutzer registriert werden. In den folgenden Schritten wird beschrieben, wie Benachrichtigungen auf Benutzer-ID-Basis gesendet werden.

1. Wählen Sie in der **Push Notifications**-Konsole die Option **Benachrichtigung senden** aus.
2. Wählen Sie die **Benutzer-ID** in der Liste der Optionen **Senden an** aus.
3. Suchen Sie im Feld **Benutzer-ID** nach der Benutzer-ID, die Sie verwenden möchten, und klicken Sie anschließend auf **Hinzufügen**.![Anzeige 'Benachrichtigungen'](images/user_notification.jpg "Push Notification-Konsole mit der Schaltfläche 'Hinzufügen' für das Feld 'Benutzer-ID'")
4. Geben Sie im Feld **Nachricht** den Text ein, den Sie in Ihrer Benachrichtigung senden möchten.
5. Klicken Sie auf **Senden**.


## Benutzeranmeldung/-abmeldung synchronisieren 
{: #sync_login_logout}

Sie können festlegen, dass Benachrichtigungen nur gesendet werden, wenn der Benutzer angemeldet ist. 

Beispiel: Ein Gerät wird von mehreren Teammitgliedern bei der Arbeit gemeinsam genutzt und es müssen bestimmte Benutzer angesprochen werden. In einem derartigen Anwendungsfall würde eine entsprechende Benutzeranmelde- und -abmeldesequenz zum Einsatz kommen. Dieser Authentifizierungsmechanismus ermöglicht es der Anwendung, die Identität des aktuellen Benutzer der Anwendung zu ermitteln. So wird sichergestellt, dass Benachrichtigungen, die einen bestimmten Benutzer zum Ziel haben, auch stets nur von diesem Benutzer empfangen werden. Rufen Sie nach einer erfolgreichen Anmeldung die API für die Geräteregistrierung auf, indem Sie die Benutzer-ID des angemeldeten Benutzers übergeben. Ebenso müssen Sie vor dem Abmelden die API für die `Rücknahme der Registrierung` aufrufen. Durch die Reihenfolgeplanung für diese Push-APIs in Verbindung mit der An- und Abmeldung wird sichergestellt, dass Benachrichtigungen für einen bestimmten Benutzer wirklich nur an diesen Benutzer gesendet werden.
