---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Paramétrer les notifications
{: #template_based_notifications}
Dernière mise à jour : 21 août 2017
{: .last-updated}

Vous pouvez paramétrer et envoyer des notifications personnalisées en créant des variables et en les appelant dans vos modèles de notifications.

Votre modèle de notification peut :

 - combiner les éléments statiques et dynamiques dans vos notifications
 - personnaliser les notifications pour chaque destinataire en ajoutant des variables
 - inclure plusieurs variables dans votre notification 

Transmettez les variables en tant qu'objets JSON dans votre code d'application lors de l'initialisation -

    
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


Une fois que les variables sont définies, elles peuvent être appelées dans votre modèle de message.

1. Sur la console {{site.data.keyword.mobilepushshort}}, sélectionnez l'onglet **Messages**.

2. Composez un message en sélectionnant une option **Envoyer à**.

2. Dans la zone **Message**, composez votre message. Appelez les variables définies dans le modèle de message. Cliquez sur **Envoyer**.

![modèle de message](images/message_template.png)

Votre message de notification personnalisé sera envoyé en extrayant les données des variables -

![exemple de message](images/message_template_example.jpg)

Remarque : la fonction est uniquement activée pour les utilisateurs ayant opté pour le `plan avancé`. Sélectionnez **Plan** dans la console du service {{site.data.keyword.mobilepushshort}} pour effectuer une [mise à niveau](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing).

**Limitations :**

 - A l'heure actuelle, cette fonction n'est pas prise en charge sur Safari
 - Les variables contenues dans le modèle de notification peuvent ne pas fonctionner en cas de fermeture forcée d'une application sur iOS. Cette limitation vient d'iOS et se trouve hors du contrôle du SDK.








