---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Schritt 5: Benachrichtigung senden
{: #push_step_4}
Letzte Aktualisierung: 27. Juni 2017
{: .last-updated}


Nach dem Entwickeln Ihrer Anwendungen können Sie einfache Push-Benachrichtigungen senden.

Führen Sie die folgenden Schritte aus, um einfache Push-Benachrichtigungen zu senden:

1. Wählen Sie **Benachrichtigungen senden** aus und erstellen Sie eine Nachricht, indem Sie eine Option für **Senden an** auswählen. Die unterstützten Optionen sind **Gerät nach Tag**, **Geräte-ID**, **Benutzer-ID**, **Android-Geräte**, **iOS-Geräte**, **Webbenachrichtigungen** und **Alle Geräte**.
**Hinweis**: Wenn Sie die Option **Alle Geräte** auswählen, erhalten alle Geräte, die Push-Benachrichtigungen subskribiert haben, Benachrichtigungen.
	
	![Anzeige 'Benachrichtigungen'](images/tag_notification.jpg)

2. Erstellen Sie Ihre Nachricht im Feld **Nachricht**. Treffen Sie Ihre Auswahl, um die optionalen Einstellungen wie erforderlich zu konfigurieren.
3. Klicken Sie auf **Senden**.
3. Stellen Sie sicher, dass Ihre Geräte oder Browser die Benachrichtigung empfangen haben.

Der folgende Screenshot zeigt ein Alertfeld bei der Verarbeitung einer Push-Benachrichtigung
im Vordergrund auf einem Android-Gerät.
	![Push-Benachrichtigung im Vordergrund auf Android-Gerät](images/Android_Screenshot.jpg)

Der folgende Screenshot zeigt eine Push-Benachrichtigung im Hintergrund auf einem Android-Gerät.
	![Push-Benachrichtigung im Hintergrund auf Android-Gerät](images/background.jpg)

## Optionale Einstellungen für Android 
{: #push_step_4_Android}

Sie können die {{site.data.keyword.mobilepushshort}}-Einstellungen zum Senden von Benachrichtigung an Android-Geräte anpassen. 

![Angepasste Android-Einstellungen](images/android_custom_settings.jpg)

Die folgenden optionalen Anpassungsoptionen werden unterstützt:

- Collapse Key (Schlüssel ausblenden): Ausgeblendete Schlüssel sind den Benachrichtigungen angehängt. Wenn mehrere Benachrichtigungen nacheinander mit demselben ausgeblendeten Schlüssel eintreffen, während das Gerät offline ist, werden die Benachrichtigungen ausgeblendet. Wenn ein Gerät wieder online ist, empfängt es Benachrichtigungen vom FCM-Server und zeigt nur die aktuellste Benachrichtigung an, die denselben ausgeblendeten Schlüssel aufweist. Falls der ausgeblendete Schlüssel nicht definiert ist, werden sowohl die neuen als auch die alten Nachrichten für die künftige Bereitstellung gespeichert.
- Sound (Audio): Gibt einen Soundclip an, der beim Empfang einer Benachrichtigung abgespielt wird. Unterstützt den Standard oder den Namen einer Soundressource, die in der App gebündelt ist.
- Icon (Symbol): Gibt den Namen des Symbols an, das für die Benachrichtigung angezeigt werden soll. Stellen Sie sicher, dass das Symbol zusammen mit der Clientanwendung im Ordner `res/drawable` gepackt ist.
- Priority (Priorität): Gibt die Optionen für die Zuordnung der Zustellpriorität zu Nachrichten an. 
	- Die Priorität `high` oder `max` bewirkt Heads-up-Benachrichtigungen.
	- Die Priorität `low` oder `default` öffnet keine Netzverbindungen auf Geräten, die sich im Ruhemodus befinden. 
	- Die Priorität `min` weist auf eine Hintergrundbenachrichtigung hin.
- Visibility (Sichtbarkeit): Sie können durch Ihre Auswahl der Option `public` oder `private` die Sichtbarkeit von Benachrichtigungen festlegen. 
	- Die Option `private` beschränkt die öffentliche Anzeige und Sie können die Aktivierung auswählen, wenn Ihr Gerät mit einer Pin oder einem Muster geschützt ist und für die Benachrichtigungseinstellung **Sensiblen Inhalt von Benachrichtigungen ausblenden** festgelegt wurde. Wenn für die Sichtbarkeit `private` festgelegt wurde, muss das Feld `redact` erwähnt werden. Es wird nur der Inhalt, der im Feld `redact` angegeben ist, auf einer sicheren, gesperrten Anzeige dargestellt. 
	- Durch die Auswahl von `public` werden die Benachrichtigungen wiedergegeben, die offen gelesen werden können.
- Time to live (Lebensdauer): Dieser Wert wird in Sekunden angegeben. Falls dieser Parameter nicht angegeben ist, speichert der FCM-Server die Nachricht für vier Wochen und versucht, diese zu übermitteln. Die Gültigkeit läuft nach vier Wochen ab. Der mögliche Wertebereich liegt zwischen 0 und 2.419.200 Sekunden.
- Delay when idle (Verzögerung bei Inaktivität): Diese Option kann auf einen der folgenden Werte gesetzt werden:
	- Bei Angabe von `True` wird der FCM-Server angewiesen, die Benachrichtigung nicht zuzustellen, wenn das Gerät inaktiv ist. 
	- Bei Angabe von `False` erfolgt die Zustellung der Benachrichtigung, auch wenn das Gerät inaktiv ist.
- Sync (Synchronisation): Durch das Festlegen von `true` für diese Option werden Benachrichtigungen über alle registrierten Geräte hinweg synchronisiert. Falls der Benutzer mit einem Benutzernamen über mehrere Geräte mit denselben installierten Anwendungen verfügt, wird die Benachrichtigung durch das Lesen auf einem Gerät auf den anderen Geräten gelöscht. Sie müssen sicherstellen, dass Sie beim {{site.data.keyword.mobilepushshort}}-Service mit der Benutzer-ID registriert sind, damit diese Option funktioniert.
- Additional payload (Zusätzliche Nutzdaten): Gibt die angepassten Werte für Nutzdaten für Ihre Benachrichtigungen an.
- Expandable notification (Erweiterbare Benachrichtigung): Bietet Kunden die Möglichkeit, in einer Benachrichtigung weitere Informationen anzugeben. Dabei wird eine einfache Benachrichtigung angezeigt, während die erweiterte Benachrichtigung ausgeblendet ist. Die folgenden Optionen werden unterstützt:
	- Big Picture-Benachrichtigungen: Die eingeblendete Benachrichtigung kann ein Bild enthalten. Für das Bild muss ein Titeltext und eine URL angegeben werden.
	- Big Text-Benachrichtigungen: Die Benachrichtigung kann zusätzlichen Text mit einem Titel enthalten. Die Big Text-Nachricht und der Titeltext müssen angegeben werden.
	- Posteingangsbenachrichtigungen: Die Benachrichtigung kann als Posteingangsbenachrichtigung gesendet werden. Geben Sie einen Titeltext und die Nachricht in Zeilen an.	 

## Optionale Einstellungen für iOS 
{: #push_step_4_ios}

Sie können die {{site.data.keyword.mobilepushshort}}-Einstellungen zum Senden von Benachrichtigung an iOS-Geräte anpassen. Die folgenden optionalen Anpassungsoptionen werden unterstützt:

- **Badge** (Badge): Gibt die Zahl an, die auf dem Anwendungsbadge angezeigt wird. Der Standardwert lautet Null (0) und führt dazu, dass kein Badge angezeigt wird. 
- **Sound** (Audio): Gibt einen Soundclip an, der beim Empfang einer Benachrichtigung abgespielt wird. Unterstützt den Standard oder den Namen einer Soundressource, die in der App gebündelt ist.
- **Additional payload** (Zusätzliche Nutzdaten): Gibt die angepassten Werte für Nutzdaten für Ihre Benachrichtigungen an.

Sie können auch [interaktive Benachrichtigungen](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications) und [Rich Media-Benachrichtigungen ](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications) aktivieren.

## Überwachung zugestellter Benachrichtigungen 
{: #push_step_4_monitor}

Der {{site.data.keyword.mobilepushshort}}-Service stellt ein Überwachungsdienstprogramm bereit, mit dem Sie den Status gesendeter Nachrichten überprüfen können. Führen Sie zum Konfigurieren des Überwachungsdienstprogramms einen der folgenden Schritte aus:

- [Überwachung für Android-Anwendungen aktivieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
- [Überwachung für iOS-Anwendungen aktivieren](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring)
