---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, setup client sdk, android application, cordova application, iOS application, web browser

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Schritt 4: Service-Client-SDKs einrichten
{: #push_step_3}

Stellen Sie zunächst sicher, dass Sie [die Berechtigungsnachweise für Benachrichtigungen abgerufen](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) und [eine Push-Serviceinstanz konfiguriert](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2) haben. Anschließend müssen Sie die Anwendung einrichten, um den Push Notifications-Service zum Registrieren, Subskribieren und Empfangen von Push-Benachrichtigungen verwenden zu können. 

Führen Sie zum Einrichten des Service-Client-SDK je nach Anwendungstyp die folgenden Schritte aus.

## In Android-Anwendungen
{: #push_step_3_Android}

Sie können Android-Anwendungen für den Empfang von Push-Benachrichtigungen auf Ihren Geräten aktivieren. Android Studio ist dafür Voraussetzung und auch die empfohlene Methode für die Erstellung von Android-Projekten. Grundlegende Kenntnisse von Android Studio sind erforderlich.

Stellen Sie sicher, dass die Anweisungen im Abschnitt [Berechtigungsnachweise des Benachrichtigungsproviders abrufen](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) ausgeführt wurden, um das FCM-Projekt einzurichten und die Berechtigungsnachweise abzurufen.

Führen Sie die Schritte für [Push Notifications: Android-SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc) aus, damit Android-Apps vom Service gesendete Push-Benachrichtigungen empfangen können. 

1. Öffnen Sie die App in Android Studio. Kopieren Sie die Datei `google-services.json`, die Sie in [Schritt 2: Berechtigungsnachweise abrufen](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) erstellt haben, in das Stammverzeichnis des Android-Anwendungsmoduls. Beachten Sie, dass die Datei `google-service.json` die hinzugefügten Paketnamen enthält.

    ![JSON-Datei zum Stammverzeichnis Ihrer Anwendung hinzufügen](images/FCM_7.jpg "JSON-Datei zum Stammverzeichnis Ihrer Anwendung hinzufügen")

2. Klicken Sie im Fenster 'Add Firebase to your Android app' auf **Continue** und dann auf **Finish**. 
3. Bauen Sie Ihre Anwendung auf und führen Sie sie aus. Nach der erfolgreichen Erstellung wird die Nachricht angezeigt, dass die Gradle-Erstellung abgeschlossen ist``.
4. Fügen Sie das Client-Push-SDK in Gradle ein.
	1. Konfigurieren Sie Ihre [Gradle](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-gradle)-Datei. 
	2. Konfigurieren Sie Ihre [AndroidManifest](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#configure-androidmanifest)-Datei.
	3. Fügen Sie die Datei `google-services.json` in das Stammverzeichnis Ihres Android-Anwendungsmoduls ein.
5. Initialisieren Sie die SDKs. Siehe [ Core-SDK und Push-SDK initialisieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#initializing-the-core-sdk-and-the-push-sdk).
6. Erstellen Sie die Anwendung.
7. Sie können sich beim Push Notifications-Service registrieren, indem Sie in der Anwendung auf die Schaltfläche 'Gerät registrieren' klicken oder die Schritte in [Mit Push-Android-SDK beim Service registrieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-to-push-notifications-ervice) ausführen.

Als Nächstes müssen Sie [eine Benachrichtigung senden](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## In Cordova-Anwendungen
{: #push_step_3_Cordova}

Cordova ist eine Plattform zum Erstellen von Hybridanwendungen mit JavaScript, CSS und HTML. Der Push Notifications-Service unterstützt die Entwicklung von iOS- und Android-Anwendungen, die auf Cordova basieren.

Sie können Cordova-Anwendungen für den Empfang von Push-Benachrichtigungen auf Ihren Geräten aktivieren. Dazu muss das [Push-SDK für Cordova-Plug-in](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app) konfiguriert werden.

Nachdem Sie das Push-SDK für Cordova-Plug-in eingerichtet haben, müssen Sie eine [Benachrichtigung senden](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## In iOS-Anwendungen
{: #push_step_3_iOS}

Sie können iOS-Anwendungen für den Empfang von {{site.data.keyword.mobilepushshort}} auf Ihren Geräten aktivieren. Dazu muss das [iOS-SDK für Push Notifications-Service](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#setup-client-application) konfiguriert werden. 

Nachdem Sie das iOS-SDK eingerichtet haben, müssen Sie eine [Benachrichtigung senden](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).


## In Web-Browsern
{: #push_step_3_web}

Sie können Ihre Browseranwendungen für den Empfang von Push-Benachrichtigungen auf Ihren Geräten aktivieren. Dazu muss das [Web-SDK für Push Notifications-Service ](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md) konfiguriert werden.

Nachdem Sie das Web-SDK eingerichtet haben, müssen Sie eine [Benachrichtigung senden](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_4).

