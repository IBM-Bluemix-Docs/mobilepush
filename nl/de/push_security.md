----

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Sicherheit bei Push Notifications 
{: #overview-push}
Letzte Aktualisierung: 27. Juni 2017
{: .last-updated}


Die {{site.data.keyword.mobilepushshort}}-APIs sind durch zwei geheime Schlüssel geschützt:

- **appSecret**: Der geheime Schlüssel `appSecret` schützt APIs, die normalerweise von Back-End-Anwendungen wie der API zum Senden von Push-Benachrichtigungen oder der API zum Konfigurieren von Einstellungen aufgerufen werden.
- **clientSecret**: Der geheime Schlüssel `clientSecret` schützt APIs, die normalerweise von mobilen Clientanwendungen aufgerufen werden. Es gibt im Zusammenhang mit der Registrierung von Geräten nur eine API mit zugeordneter Benutzer-ID, die diesen geheimen Clientschlüssel (`clientSecret`) erfordert. Keine der anderen APIs, die von mobilen Clients aufgerufen werden, erfordert den geheimen Clientschlüssel (`clientSecret`). 

Die geheimen Schlüssel `appSecret` und `clientSecret` werden jeder Serviceinstanz beim Binden einer Anwendung mit dem {{site.data.keyword.mobilepushshort}}-Service zugeordnet. Weitere Informationen dazu, auf welche Weise und für welche APIs die geheimen Schlüssel übergeben werden sollen, finden Sie in der Dokumentation für [REST-APIs ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://mobile.{DomainName}/imfpush/).

## appSecret 
{: #push-api-rest-secret}

Beim Binden einer Anwendung an {{site.data.keyword.mobilepushshort}} generiert der Service den eindeutigen Schlüssel 'appSecret' und übergibt diesen mit dem Antwortheader. Wenn Sie die REST-API von IBM {{site.data.keyword.mobilepushshort}} for IBM Cloud verwenden, finden Sie in der Referenz für die REST-API Informationen dazu, welche APIs geschützt werden müssen. Weitere Informationen finden Sie in der [Push-REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://mobile.{DomainName}/imfpush/){: new_window}.

Der Anforderungsheader muss 'appSecret' enthalten. Andernfalls gibt der Server den Fehlercode 401 ('Unauthorized Error') zurück. Beim Hinzufügen von {{site.data.keyword.mobilepushshort}} zu einer Anwendung wird eine spezifische App-ID erstellt. Sie erhalten als Teil der Antwort einen Header mit dem Namen 'appSecret', der für die Erstellung von Tags oder das Senden von Nachrichten verwendet wird. Diese Operation erfolgt über Services im Katalog oder in der Boilerplate.

Gehen Sie wie folgt vor, um den Wert 'appSecret' abzurufen:

1. Klicken Sie auf den *App-Namen*, der an den Push-Service gebunden ist.
2. Klicken Sie auf den Link **Berechtigungsnachweise anzeigen**, um 'appSecret' (App-ID) anzuzeigen.

In der Anzeige **Berechtigungsnachweise anzeigen** werden Informationen zu 'appSecret' angezeigt:
```
	{
    "imfpush_Dev": [
   {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://imfpush.ng.bluemix.net/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.ng.bluemix.net/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**Hinweis**: Frühere Anwendungen mussten den geheimen Clientschlüssel (clientSecret) nur bei der Registrierung oder Aktualisierung von Geräten mit dem Feld für die Benutzer-ID (userId) übergeben. Alle anderen APIs, die von mobilen oder Browserclients aufgerufen wurden, benötigten den geheimen Clientschlüssel nicht. Diese früheren Anwendungen können den geheimen Clientschlüssel auch weiterhin optional für Geräteregistrierungen oder Aktualisierungsaufrufe verwenden. Es wird jedoch dringend empfohlen, dass die Prüfung des geheimen Clientschlüssels für alle Aufrufe der Client-API zwingend durchgeführt wird. Um dies in vorhandenen Anwendungen durchzusetzen, wurde eine neue API mit dem Namen `verifyClientSecret` veröffentlicht.  Für neue Anwendungen wird die Überprüfung des geheimen Clientschlüssels bei allen Aufrufen der Client-API erzwungen. Dieses Verhalten kann auch durch die API `verifyClientSecret` nicht verändert werden.

Standardmäßig wird die Verifizierung des geheimen Clientschlüssels nur bei neuen Apps erzwungen. Sowohl vorhandene als auch neue Apps können die Verifizierung des geheimen Clientschlüssels mithilfe der REST-API 'verifyClientSecret' aktivieren oder inaktivieren. Es wird empfohlen, die Verifizierung des geheimen Clientschlüssels zu erzwingen, um zu verhindern, dass Benutzer mit Kenntnis der Anwendungs-ID und der Geräte-ID Zugang zu Geräten erhalten.

Stellen Sie sicher, dass der geheime Clientschlüsel (`clientSecret`) vertraulich behandelt wird und zu keinem Zeitpunkt in der mobilen App fest codiert ist. Es gibt verschiedene Muster für die Anwendungsinitialisierung, mit denen der geheime Clientschlüssel (`clientSecret`) zur Anwendungslaufzeit dynamisch extrahiert werden kann. Das Ablaufdiagramm stellt solche möglichen Muster dar.
![Enable_Push](images/init_client_secret.jpg) 



