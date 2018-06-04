---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Parametrisierte Benachrichtigungen
{: #template_based_notifications}
Letzte Aktualisierung: 21. August 2017
{: .last-updated}

Sie können Benachrichtigungen parametrisieren und angepasste Benachrichtigungen senden, indem Sie Variablen erstellen und diese in den Benachrichtigungsvorlagen aufrufen.

Mit der Benachrichtigungsvorlage ist Folgendes möglich:

 - Kombinieren von statischen und dynamischen Elementen in den Benachrichtigungen
 - Personalisieren von Benachrichtigungen für die jeweiligen Empfänger durch Hinzufügen von Variablen
 - Verwenden mehrerer Variablen in der Benachrichtigung 

Übergeben Sie Variablen als JSON-Objekte im Anwendungscode während der Initialisierung:

    
   ```
    MFPPushNotificationOptions options = new MFPPushNotificationOptions();

    JSONObject tempValue = new JSONObject();
        try {
        
		tempValue.put("username",userName);
        
        tempValue.put("amountSpent",amount);
		
        tempValue.put("currency",currency);
		
        tempValue.put("avilableBalance",balance);
        
		} catch (JSONException e) {
            e.printStackTrace();
        }
        options.setPushVariables(tempValue); 
	   
	   push = MFPPush.getInstance();

       push.initialize(getApplicationContext(),appGuid,clientSecret,options);
   ```
{: codeblock}


Nach der Definition der Variablen können diese in der Nachrichtenvorlage aufgerufen werden.

1. Wählen Sie in der {{site.data.keyword.mobilepushshort}}-Konsole die Registerkarte **Nachrichten** aus.

2. Erstellen Sie eine Nachricht, indem Sie eine der Optionen für **Senden an** auswählen.

2. Erstellen Sie Ihre Nachricht im Feld **Nachricht**.  Rufen Sie die definierten Variablen in der Nachrichtenvorlage auf. Klicken Sie auf **Senden**.

![Nachrichtenvorlage](images/message_template.png)

Die angepasste Benachrichtigung wird gesendet, indem die Variablendaten abgerufen werden.

![Nachrichtenbeispiel](images/message_template_example.jpg)

Hinweis: Das Feature ist nur für Benutzer aktiviert, die den `Erweiterten Plan` ausgewählt haben. Wählen Sie **Plan** in der {{site.data.keyword.mobilepushshort}}-Servicekonsole aus, um ein [Upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing) durchzuführen.

**Einschränkungen:**

 - Dieses Feature wird zum gegenwärtigen Zeitpunkt nicht für Safari unterstützt.
 - Variablen in der Benachrichtigungsvorlage können möglicherweise nicht korrekt verwendet werden, wenn unter iOS die Beendigung einer App erzwungen wird. Diese Einschränkung stammt aus iOS und kann vom SDK nicht beeinflusst werden.








