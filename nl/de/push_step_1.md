
---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Schritt 2: Berechtigungsnachweise des Benachrichtigungsproviders abrufen
{: #push_step_1}
Letzte Aktualisierung: 27. Juni 2017
{: .last-updated}

Zum Einrichten des {{site.data.keyword.mobilepushshort}}-Service müssen Sie die erforderlichen Berechtigungsnachweise bei Ihrem Push-Benachrichtigungsprovider abrufen. 

## Für Android
{: #push_step_1_android}

Firebase Cloud Messaging (FCM) ist das Gateway, das für die Übermittlung von Push-Benachrichtigungen an Android-Geräte sowie an Google Chrome-Browser und Chrome Apps & Erweiterungen verwendet wird. Sie müssen Ihre FCM-Berechtigungsnachweise (Sender-ID und API-Schlüssel) abrufen, um den {{site.data.keyword.mobilepushshort}}-Service auf der Konsole einzurichten. 

Der API-Schlüssel wird geschützt gespeichert und vom {{site.data.keyword.mobilepushshort}}-Service für die Verbindungsherstellung zum FCM-Server verwendet. Die Absender-ID (Projektnummer) wird vom Android-SDK und dem JS-SDK für Google Chrome und Mozilla Firefox auf der Clientseite verwendet. 

Führen Sie zum Einrichten von FCM und Abrufen Ihrer Berechtigungsnachweise die folgenden Schritte aus:

1. Rufen Sie die [Firebase-Konsole ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.firebase.google.com/?pli=1){: new_window} auf. Eine Google-Benutzerkonto ist erforderlich. 
2. Wählen Sie **Projekt hinzufügen** aus. 
3. Geben Sie im Fenster 'Projekt erstellen' einen Projektnamen ein, wählen Sie ein Land/eine Region aus und klicken Sie auf **Projekt erstellen**.
3. Wählen Sie im Navigationsfenster **Einstellungen** > **Projekteinstellungen** aus.
4. Wählen Sie die Registerkarte 'Cloud Messaging' aus, um Ihre Berechtigungsnachweise (Server-API-Schlüssel und Absender-ID) abzurufen. Beachten Sie, dass der in FCM aufgeführte Serverschlüssel mit dem Server-API-Schlüssel identisch ist.
   
	![Berechtigungsnachweise für FCM abrufen](images/FCM_settings_2.jpg)

Darüber hinaus müssen Sie die Datei `google-services.json` generieren. Führen Sie die folgenden Schritte aus:

1. Klicken Sie in der Firebase-Konsole auf das Symbol für die **Projekteinstellungen**.
    
	![Firebase-Projekteinstellungen](images/FCM_settings_6.jpg)

3. Wählen Sie auf der Registerkarte 'Allgemein' im Fenster mit Ihren Apps das Symbol **ADD APP** oder **Add Firebase to your Android app** aus.
    
4. Fügen Sie im Fenster 'Add Firebase to your Android app' **com.ibm.mobilefirstplatform.clientsdk.android.push** als Paketnamen hinzu. Das Feld 'App nickname' ist optional. Klicken Sie auf **ADD APP**. 
    
	![Fenster 'Add Firebase to your Android app'](images/FCM_1.jpg)

5. Geben Sie den Paketnamen Ihrer Anwendung an, indem Sie ihn im Fenster 'Add Firebase to your Android app' eingeben. Das Feld 'App nickname' ist optional. Klicken Sie auf **REGISTER APP**. 

	![Paketnamen Ihrer Anwendung hinzufügen](images/FCM_settings_4.jpg)

6. Die Datei `google-services.json` wird generiert. 


Nachdem Sie die FCM-Berechtigungsnachweise abgerufen und die Datei `google-services.json` generiert haben, müssen Sie als nächsten Schritt eine [Serviceinstanz erstellen](push_step_2.html).

**Hinweis**: FCM ist die neue Version von Google Cloud Messaging (GCM). Achten Sie darauf, für neue Apps FCM-Berechtigungsnachweise zu verwenden. Vorhandene Apps können mit GCM-Konfigurationen weiterhin betrieben werden.

## Für iOS
{: #push_step_1_ios}

Apple Push Notification Service (APNs) ermöglicht Anwendungsentwicklern das Senden ferner Benachrichtigungen aus der IBM CLoud-Instanz des {{site.data.keyword.mobilepushshort}}-Service (d. h. dem Provider) an iOS-Geräte und -Anwendungen. Die Nachrichten werden an eine Zielanwendung auf dem Gerät gesendet. 

Sie müssen die APNs-Berechtigungsnachweisee abrufen und konfigurieren. Die APNs-Zertifikate werden vom {{site.data.keyword.mobilepushshort}}-Service sicher verwaltet und zum Herstellen einer Verbindung zum APNs-Server als Provider verwendet.


### App-IDs registrieren
{: #push_step_1_ios_2}

Die App-ID (Bundle-ID) ist eine eindeutige Kennung für eine bestimmte Anwendung. Für jede Anwendung ist eine App-ID erforderlich. Services wie der {{site.data.keyword.mobilepushshort}}-Service werden für die App-ID konfiguriert.

Stellen Sie sicher, dass Sie über ein [Apple Developers-Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com/){: new_window} verfügen. Dieses Konto ist absolut erforderlich.

2. Rufen Sie das [Apple Developer-Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com){: new_window} auf, klicken Sie auf **Member Center** und wählen Sie **Certificates, Identifiers & Profiles** aus.
3. Rufen Sie **IDs** > Abschnitt **App-IDs** auf.
3. Geben Sie auf der Seite **Registering App IDs** den App-Namen im Namensfeld für die App-ID-Beschreibung an. Beispiel: ACME-Push-Benachrichtigungen.
4. Geben Sie eine Zeichenfolge für das App-ID-Präfix an.  
4. Wählen Sie für das App-ID-Suffix **Explicit App ID** aus und geben Sie einen Bundle-ID-Wert an. Es wird empfohlen, die umgekehrte Zeichenfolge eines Domänennamens zu verwenden. Beispiel: `com.ACME.push`.
5. Wählen Sie das Kontrollkästchen **Push Notifications** aus und klicken Sie auf **Continue**.
6. Nehmen Sie Ihre Einstellungen vor und klicken Sie auf **Register** > **Done**.

Ihre App-ID ist nun registriert. 

   ![Registierte App-ID](images/push_ios_register_appid.jpg)
  

### SSL-Zertifikat zum Entwickeln und Verteilen von APNs erstellen
{: #push_step_1_ios_3}

Bevor Sie ein APNs-Zertifikat anfordern, müssen Sie zunächst eine Zertifikatssignieranforderung (Certificate Signing Request, CSR) generieren und an die Zertifizierungsstelle (Certificate Authority, CA) von Apple schicken. Die CSR enthält Informationen zum Identifizieren Ihres Unternehmens und beinhaltet Ihren öffentlichen sowie Ihren privaten Schlüssel, den Sie zum Signieren Ihrer Apple-Push-Benachrichtigungen verwenden. Generieren Sie anschließend das SSL-Zertifikat in iOS Developer Portal. Das Zertifikat mit dem zugehörigen öffentlichen und privaten Schlüssel wird in Keychain Access gespeichert.

Sie können APNs auf zwei Weisen verwenden: 

* Sandboxmodus zum Entwickeln und Testen.
* Produktionsmodus zum Verteilen von Anwendungen über den App
Store (oder über die Verteilungsmechanismen anderer Unternehmen.

Sie müssen separate Zertifikate für Ihre Entwicklungs- und Verteilungsumgebungen anfordern. Die Zertifikate werden einer App-ID für die App zugeordnet, die der Empfänger für ferne Benachrichtigungen ist. Für die Produktion können Sie bis zu zwei Zertifikate erstellen. IBM Cloud verwendet diese Zertifikate, um eine SSL-Verbindung mit APNs herzustellen.

<!-- Create a development and distribution SSL certificate. -->

1. Rufen Sie die [Apple Developer-Website ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com){: new_window} auf, klicken Sie auf **Member Center** und wählen Sie **Certificates, Identifiers & Profiles** aus.
2. Klicken Sie im Bereich **Identifiers** auf **App IDs**.
3. Wählen Sie in der Liste Ihrer App-IDs zunächst die App-ID und anschließend **Edit** aus.
4. Wählen Sie das Kontrollkästchen **Push Notifications** aus und gehen Sie dann wie folgt vor:
	-  Klicken Sie im Bereich für das SSL-Zertifikat für Entwicklung auf **Create Certificate**.
	-  Klicken Sie im Bereich für das SSL-Zertifikat für Produktion auf **Create Certificate**.

	![SSL-Zertifikate für Push Notifications](images/certificate_createssl.jpg)

5. Wenn die Anzeige zur Erstellung einer Zertifikatssignieranforderung (CSR) **About Creating a Certificate Siging Request (CSR)** angezeigt wird, starten Sie auf Ihrem Mac-Computer die Anwendung **Keychain Access**, um eine Zertifikatssignieranforderung (Certificate Signing Request, CSR) zu erstellen. Klicken Sie auf **Weiter**.
6. Klicken Sie für die Option zum Hochladen der CSR-Datei auf **Choose File** und wählen Sie die Datei `CertificateSigningRequest.certSigningRequest` aus. 
7. Klicken Sie auf **Weiter**.
8. Klicken Sie im Bereich für Download, Installation und Backup auf **Download**. Die Datei `aps_development.cer` wird heruntergeladen.
	
	![Download certificate](images/push_certificate_download.jpg)	
	
6. Wählen Sie im Menü **Keychain Access > Certificate Assistant > Request a Certificate From a Certificate Authority…** aus. 
7. Geben Sie unter **Certificate Information** die E-Mail-Adresse ein, die Ihrem App Developer-Konto zugeordnet ist, sowie einen allgemeinen Namen. Verwenden Sie einen aussagefähigen Namen, der erkennen lässt, ob es sich um ein Zertifikat für die Entwicklung (Sandbox) oder für die Verteilung (Produktion) handelt (z. B. _sandbox-apns-certificate_ oder _production-apns-certificate_).
8. Wählen Sie die Option **Save to disk** aus, um die Datei `.certSigningRequest` auf Ihren Desktop herunterzuladen, und klicken Sie anschließend auf **Continue**.
9. Geben Sie in der Menüoption **Save As** einen Namen für die Datei `.certSigningRequest` an und klicken Sie anschließend auf **Save**.
10. Klicken Sie auf **Done**. Sie haben eine CSR erstellt.
11. Kehren Sie zum Fenster **About Creating a Certificate Siging Request (CSR)** zurück und klicken Sie auf **Continue**. 
12. Klicken Sie in der Anzeige **Generate** auf die Option **Choose File ... ** und wählen Sie die CSR-Datei aus, die Sie auf Ihrem Desktop gespeichert haben. Klicken Sie anschließend auf **Generate**.

	![Zertifikat generieren](images/generate_certificate.jpg)
13. Nachdem das Zertifikat erstellt wurde, klicken Sie auf **Done**.
14. Klicken Sie in der Anzeige **Push Notifications** auf **Download**, um Ihr Zertifikat herunterzuladen, und klicken Sie anschließend auf **Done**. 
	
	![Download certificate](images/certificate_download.jpg)

15. Navigieren Sie auf Ihrem Mac-Computer zu **Keychain Access > My Certificates** und suchen Sie nach dem neu installierten Zertifikat. Doppelklicken Sie auf das Zertifikat, damit es in Keychain Access installiert wird.
16. Wählen Sie das Zertifikat und den privaten Schlüssel aus und klicken Sie anschließend auf **Export**, um das Zertifikat in das Format zum Austauschen personenbezogener Daten (`.p12`) umzuwandeln.

	![Zertifikat und Schlüssel exportieren](images/keychain_export_key.jpg)
17. Geben Sie im Feld **Save As** einen aussagefähigen Namen für das Zertifikat an. Zum Beispiel `sandbox_apns.p12_certifcate` oder `production_apns.p12` und klicken Sie anschließend auf **Save**.
	
	![Zertifikat und Schlüssel exportieren](images/certificate_p12v2.jpg)
18. Geben Sie im Feld **Enter a password** ein Kennwort zum Schützen der exportierten Elemente ein und klicken Sie anschließend auf **OK**. Dieses Kennwort können Sie verwenden, um Ihre APNs-Einstellungen in der Push Notifications-Services-Konsole zu konfigurieren.
	
	![Zertifikat und Schlüssel exportieren](images/export_p12.jpg)
19. **Key Access.app** fordert Sie zum Exportieren Ihres Schlüssels aus der Anzeige **Keychain** auf. Geben Sie Ihr Administratorkennwort für Ihren Mac-Computer ein, um den Export dieser Elemente zuzulassen, und wählen Sie anschließend die Option **Always Allow** aus. Auf Ihrem Desktop wird ein `.p12`-Zertifikat erstellt.


### Entwicklungsbereitstellungsprofil erstellen
{: #create-push-credentials-dev-profile}

Das Bereitstellungsprofil ermittelt anhand der App-ID, auf welchen Geräten Ihre App installiert und ausgeführt werden kann und auf welche Services die App zugreifen kann. Sie erstellen für jede App-ID zwei Bereitstellungsprofile, eines für die Entwicklung und das zweite für die Verteilung. Xcode ermittelt anhand des Entwicklungsbereitstellungsprofils, welche Entwickler den Build für die App durchführen dürfen und welche Geräte in der Anwendung
getestet werden dürfen.

Stellen Sie sicher, dass die App-ID registriert, für den {{site.data.keyword.mobilepushshort}}-Service aktiviert und für die Verwendung eines SSL-Zertifikats für APNs im Entwicklungs- sowie im Produktionsmodus konfiguriert wurde.

Erstellen Sie ein Entwicklungsbereitstellungsprofil wie folgt:

1. Rufen Sie das [Apple Developer-Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com){: new_window} auf, klicken Sie auf **Member Center** und wählen Sie **Certificates, Identifiers & Profiles** aus.
2. Rufen Sie die [Mac Developer Library ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com/library/mac/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW62site){: new_window}  auf, navigieren Sie zum Abschnitt **Creating Development Provisioning Profiles** und befolgen Sie die Anweisungen zum Erstellen eines Entwicklungsprofils.
**Hinweis**: Wählen Sie beim Konfigurieren eines Entwicklungsbereitstellungsprofils die folgenden Optionen aus:
	* **iOS App Development**
	* **For iOS and watchOS apps **


### Bereitstellungsprofil für Store-Verteilung erstellen
{: #create-push-credentials-apns-distribute_profile}

Mithilfe des Store-Bereitstellungsprofils können Sie Ihre App für die Verteilung
an den App-Store übergeben.

1. Rufen Sie das [Apple Developer-Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com){: new_window} auf, klicken Sie auf **Member Center** und wählen Sie **Certificates, Identifiers & Profiles** aus.
2. Doppelklicken Sie auf das heruntergeladene Bereitstellungsprofil, um das Profil in Xcode zu installieren.

Nach dem Abrufen der Berechtigungsnachweise müssen Sie als nächsten Schritt eine [Serviceinstanz konfigurieren](push_step_2.html).

## Für Web-Browser und Chrome-Apps & Erweiterungen
{: #configure-credential-for-browsers}

Der IBM Service {{site.data.keyword.mobilepushshort}} verfügt über erweiterte Funktionen zum Senden von Benachrichtigungen an Ihren Browser und zudem an Chrome Apps & Erweiterungen.

Die Website-URL oder der Domänenname Ihrer Website wird vom {{site.data.keyword.mobilepushshort}}-Service benötigt, um die Anforderungen zu identifizieren, die zugelassen werden müssen. 

Beispiel: `https://www.acmebanks.com`

Jede Instanz des {{site.data.keyword.mobilepushshort}}-Service unterstützt nur einen Domänennamen. Stellen Sie daher sicher, dass für Chrome, Firefox und Safari der gleiche Wert festgelegt ist. In Chrome- und Safari-Browsern sind zusätzliche Konfigurationsschritte für Web-Push erforderlich. Sie benötigen einen FCM-API-Schlüssel, da Nachrichten in Chrome über einen FCM-Endpunkt gesendet werden. 

Informationen zum Einrichten des Service für Chrome, Firefox-Browser und Chrome Apps & Erweiterungen finden Sie in [Serviceinstanz konfigurieren](push_step_2.html).


### Web-Push für Safari konfigurieren 
{: #configure-safari}

Für den {{site.data.keyword.mobilepushshort}}-Service wird die Version Safari 10.0 unterstützt. Sie müssen zunächst über Ihr Apple Developer-Konto ein Zertifikat generieren, bevor Sie Ihren Browser für den Empfang von Benachrichtigungen konfigurieren.

#### Zertifikat generieren
{: #certificate-generation}

Stellen Sie sicher, dass Sie über ein Apple Developer-Konto verfügen. Sie müssen eine 'Website Push ID' registrieren und ein Zertifikat generieren, um Ihren Safari-Browser für den Empfang von Benachrichtigungen zu konfigurieren. Führen Sie zur Einführung die folgenden Schritte aus.

1. Klicken Sie im Apple Developer Member Center auf **Certificates, ID & Profiles**. 
2. Klicken Sie auf **Identifiers** und anschließend auf **Website Push IDs**.
3. Erstellen Sie durch Auswahl des Plussymbols einen neuen Eintrag.
  ![Push Notifications-Konsole](images/safari_1.jpg)

4. Geben Sie in der Anzeige 'Register Website Push ID' eine entsprechende Beschreibung der Website Push ID sowie eine ID an. Es wird empfohlen, das rDNS-Format (Reverse DNS Lookup) zu verwenden, das mit `web` beginnt. Beispiel:  `web.com.acmebanks`.
5. Registrieren Sie die 'Website Push ID'. Sie haben jetzt Ihre Website Push ID 
6. Wählen Sie **Edit** aus, um ein Zertifikat für die Verwendung für die Website Push ID zu erstellen.
7. Geben Sie im Fenster 'Certificate Assistant' als Zertifikatsinformationen Ihre E-Mail-ID und einen allgemeinen Namen an. Lassen Sie das Feld für die E-Mail-Adresse der Zertifizierungsstelle leer.
8. Klicken Sie auf **Save to disk** und wählen Sie **Continue** aus.
9. Wählen Sie für die Speicherung des Zertifikats einen entsprechenden Ordner aus.
10. Wählen Sie die auf der Platte erstellte Datei `.certSigningRequest` aus, wenn Sie vom Assistenten zum Generieren des Zertifikats aufgefordert werden. Stellen Sie sicher, dass Sie das im `.cer`-Format erstellte Website-Push-Zertifikat herunterladen.
11. Öffnen Sie das Zertifikat im Tool KeyChain Access. Klicken Sie mit der rechten Maustaste und exportieren Sie es als p12-Zertifikat. Beachten Sie das während der Generierung des p12-Zertifikats bereitgestellte Kennwort.

Nach der Generierung des Zertifikats müssen Sie eine [Serviceinstanz konfigurieren](push_step_2.html).

