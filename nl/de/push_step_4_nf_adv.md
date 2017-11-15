---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

#Erweiterte Push-Benachrichtigungen aktivieren
Letzte Aktualisierung: 01. Juni 2017
{: .last-updated}

Konfigurieren Sie ein iOS Badge, zusätzliche JSON-Nutzdaten, umsetzbare Benachrichtigungen und Blockierungsnachrichten.

## Audio, Nutzdaten und iOS Badge konfigurieren
{: #badge-sound-payload}

Konfigurieren Sie ein iOS Badge, eine Audiodatei und zusätzliche JSON-Nutzdaten.

1. Navigieren Sie in der {{site.data.keyword.mobilepushshort}}-Konsole zur Registerkarte **Benachrichtigungen**.
2. Konfigurieren Sie im Abschnitt **Optionale Felder** die folgenden Komponenten für Push-Benachrichtigungen. 
	- **Sound File** (Audiodatei) - Geben Sie eine Zeichenfolge ein, die auf die Audiodatei in Ihrer mobilen App verweist. Geben Sie den Zeichenfolgenamen der zu verwendenden Audiodatei in den Nutzdaten an.
	- **iOS Badge**: Für iOS-Geräte die Nummer, die als Badge für das App-Symbol angezeigt werden soll. Wenn diese Eigenschaft fehlt, wird das Badge nicht geändert. Um das Badge zu entfernen,
legen Sie für diese Eigenschaft den Wert 0 fest.
3. Wählen Sie eine der folgenden Optionen aus:	
	- Unter Android

 	Fügen Sie die Audiodatei zum Verzeichnis `res/raw` der Android-Anwendung hinzu. Fügen Sie beim Senden einer Benachrichtigung den Namen der Audiodatei zum entsprechenden Feld für {{site.data.keyword.mobilepushshort}} hinzu:

	```
	"settings": {
     "gcm" : {
     "sound":"tt.wav",
	  }
		}  
	```	{: codeblock}	
	
	- Unter iOS

	```
	"settings": {
	     "apns" : {
	      "badge": 10,
	      "sound": "tt.wav",
	  }
	}
	``` 
		{: codeblock}
		
**Zusätzliche Nutzdaten** - Diese Nutzdaten können ein beliebiges Schlüssel/Wert-Paar sein; es muss sich jedoch um ein JSON-Objekt handeln, das Sie mit der Push-Benachrichtigung senden möchten.

```
{"key":"value", "key2":"value2"}
```
	{: codeblock}

## Android-Benachrichtigungen blockieren 
{: #hold-notifications-android}

Wenn Ihre Anwendung in den Hintergrund wechselt, ist es möglicherweise wünschenswert, dass {{site.data.keyword.mobilepushshort}} solche Benachrichtigungen vorübergehend blockiert, die an Ihre Anwendung gesendet wurden. Rufen Sie zum Blockieren von Benachrichtigungen die Methode 'hold()' in der Methode 'onPause()' der Aktivität auf, die Push-Benachrichtigungen verarbeitet.

```
@Override
protected void onPause() {
    super.onPause();
    if (push != null) {
        push.hold();
    }
} 
```
	{: codeblock}

    
