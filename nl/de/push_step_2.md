---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, service instance, cordova application

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Schritt 3: Serviceinstanz konfigurieren 
{: #push_step_2}

Stellen Sie sicher, dass die im Abschnitt [Berechtigungsnachweise für Benachrichtigung abrufen](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) durchgeführt wurden.

## Für Android- und Chrome-Apps & -Erweiterungen
{: #push_step_2_Android}

Stellen Sie sicher, dass die Anweisungen im Abschnitt [Berechtigungsnachweise des Benachrichtigungsproviders abrufen](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) ausgeführt wurden, um das FCM-Projekt einzurichten und die Berechtigungsnachweise abzurufen.

Führen Sie die folgenden Schritte aus, um FCM-Berechtigungsnachweise für Android-Anwendungen und Google Chrome Apps & Erweiterungen zu konfigurieren:

1. Öffnen Sie den IBM Cloud-Katalog und klicken Sie anschließend auf die von Ihnen erstellte Serviceinstanz von {{site.data.keyword.mobilepushfull}}. 
2. Klicken Sie auf **Verwalten** > **Konfigurieren**. 
3. Wählen Sie eine der folgenden Optionen aus: 
	- Android: Wählen Sie **Mobile** aus und aktualisieren Sie die Registerkarte für FCM-Push-Berechtigungsnachweise mit Absender-ID/Projektnummer und API-Schlüssel. 
	- Google Chrome Apps & Erweiterungen: Wählen Sie **Web** aus und aktualisieren Sie die Registerkarte für Chrome-Apps und Erweiterungen mit Absender-ID/Projektnummer und API-Schlüssel. 
4. Klicken Sie auf **Speichern**. Der Push Notifications-Service ist nun konfiguriert.

Als Nächstes müssen Sie die [Client-SDKs für Push-Service einrichten](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3).


## Für Cordova-Anwendungen 
{: #push_step_2_b}


Cordova ist eine Plattform zum Erstellen von Hybridanwendungen mit JavaScript, CSS und HTML. Der {{site.data.keyword.mobilepushshort}}-Service unterstützt die Entwicklung von iOS- und Android-Anwendungen, die auf Cordova basieren.

Sie können Cordova-Anwendungen für den Empfang von Push-Benachrichtigungen auf Ihren Geräten aktivieren. Lesen Sie dazu die Informationen in [Push Notifications: Push-SDK für Cordova-Plug-in](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).



## Für iOS-Anwendungen und Safari-Browser 
{: #enable-push-ios-notifications}


Um den {{site.data.keyword.mobilepushshort}}-Service zum Senden von Benachrichtigungen verwenden zu können, laden Sie die `.p12`-Zertifikate hoch, die Sie in Schritt 1: [Berechtigungsnachweise des Benachrichtigungsproviders abrufen](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_1) erstellt haben. Dieses Zertifikat enthält den privaten Schlüssel und die SSL-Zertifikate, die zum Erstellen und Veröffentlichen Ihrer Anwendung erforderlich sind. Sie können auch die REST-API verwenden, um ein APNs-Zertifikat hochzuladen.

**Hinweis**: Nachdem sich die `.cer`-Datei in Ihrem Key Chain-Zugriff befindet, exportieren Sie sie auf Ihrem Computer, um ein `.p12`-Zertifikat zu erstellen.

Weitere Informationen zur Verwendung der APNs finden Sie in der Veröffentlichung [iOS Developer Library: Local and Push Notification Programming Guide ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1){: new_window}.

Führen Sie die folgenden Schritte aus, um APNs in der Push Notifications-Services-Konsole einzurichten:

1. Wählen Sie in der Push Notifications-Services-Konsole die Option **Konfigurieren** aus.
2. Wählen Sie die Option **Mobile** aus, um die Informationen im Formular mit den APNs-Push-Berechtigungsnachweisen zu aktualisieren.
3. Wählen Sie eine der folgenden Optionen aus:
	- Für die Option **Mobile**
		1. Wählen Sie je nach Bedarf **Sandbox** (Entwicklung) oder **Produktion** (Verteilung) aus und laden Sie dann das `p.12`-Zertifikat hoch, das Sie erstellt haben.
		  ![Push Notifications-Konsole einrichten](images/wizard.jpg "Push Notifications-Konsole mit ausgewählter Navigationsoption 'Konfigurieren' und angezeigter Seite 'Mobile' und den APN-Push-Berechtigungsnachweisen")

		1. Geben Sie in das Feld **Kennwort** das zugehörige Kennwort für die `.p12`-Zertifikatsdatei ein und klicken Sie anschließend auf **Speichern**.
	- Für die Option **Web**
		- Aktualisieren Sie im Abschnitt 'Safari Push' das Formular mit den erforderlichen Informationen. 
		- **Website Name**: Dies ist der Name, den Sie im Benachrichtigungscenter angegeben haben.
		- **Website Push ID**: Aktualisieren Sie den Wert durch die umgekehrte Zeichenfolge der Domäne für Ihre Website Push ID. Beispiel: web.com.acmebanks.www.
		- **Website URL**: Geben Sie die URL der Website für die Subskription von Push-Benachrichtigungen an. Beispiel: https://www.acmebanks.com.
		- **Allowed Domains**: Dies ist ein optionaler Parameter. Dies ist die Liste der Websites, die eine Berechtigung vom Benutzer anfordern. Stellen Sie sicher, dass es sich bei den URLs um durch Kommas getrennte Werte handelt. Beachten Sie, dass der Wert für die Website-URL verwendet wird, wenn an dieser Stelle nichts angegeben wird. 
		- **URL Format String**: Die URL für die Auflösung, wenn die Benachrichtigung angeklickt wird. Beispiel: ["https://www.acmebanks.com"]. Stellen Sie sicher, dass die URL das HTTP- oder HTTPS-Schema verwendet.
		- **Safari web push certificate**: Laden Sie das .p12-Zertifikat hoch und geben Sie ein Kennwort an.
4. Klicken Sie auf **Speichern**.	
![Push Notifications-Konsole](images/push_configure_safari.jpg "Felder der Seite für Weboptionen")	

Nachdem Sie den Service für iOS-Anwendungen eingerichtet haben, müssen Sie die [Client-SDKs für Push- Service einrichten](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3).


## Für Chrome- und Firefox-Browser 
{: #push_step2_chromefirefox}

1. Wählen Sie in der Push Notifications-Konsole **Konfigurieren** aus.
2. Wählen Sie die Webregisterkarte aus.
	![Web-Push-Konfigurationen](images/webpush_configure.jpg "Web-Push-Konfigurationsfenster zum Definieren des FCM-API-Schlüssels und der URL Ihrer Webseite")
3. Konfigurieren Sie den FCM-API-Schlüssel und die URL Ihrer Webseite, die für den Empfang von Push-Benachrichtigungen registriert wird.
4. Klicken Sie auf **Speichern**.
5. Nachdem Sie den Service eingerichtet haben, müssen Sie die [Client-SDKs für Push-Service einrichten](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_3).


