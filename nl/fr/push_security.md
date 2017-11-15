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

# Sécurité des notifications push 
{: #overview-push}
Dernière mise à jour : 27 juin 2017
{: .last-updated}


Les API {{site.data.keyword.mobilepushshort}} sont sécurisées par deux types de valeur confidentielle :

- **appSecret** : `appSecret` protège les API qui sont généralement appelées par des applications de back end (telles que l'API d'envoi de {{site.data.keyword.mobilepushshort}}  et l'API de configuration des paramètres).
- **clientSecret** : `clientSecret` protège les API généralement appelées par des applications de client mobile. Il n'y a qu'une seule API relative à l'enregistrement d'un appareil avec un ID utilisateur associé qui nécessite cette valeur confidentielle `clientSecret`. Aucune des autres API invoquées depuis les clients mobiles n'ont besoin de `clientSecret`. 

Les valeurs `appSecret` et `clientSecret` sont allouées à chaque instance de service au moment de la liaison d'une application au service {{site.data.keyword.mobilepushshort}}. Reportez-vous à la documentation des [API REST ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobile.{DomainName}/imfpush/) pour plus d'informations sur la transmission des valeurs confidentielles et pour quelles API.

## Valeur confidentielle d'application 
{: #push-api-rest-secret}

Quand une application est liée à {{site.data.keyword.mobilepushshort}}, le service génère une valeur confidentielle appSecret (clé unique) et la transmet dans l'en-tête de réponse. Si vous utilisez l'API REST IBM {{site.data.keyword.mobilepushshort}} for Bluemix, servez-vous de la référence de l'API REST pour savoir quelles sont les API que vous devez sécuriser. Pour plus d'informations, reportez-vous à la rubrique [Push REST API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobile.{DomainName}/imfpush/){: new_window}.

L'en-tête de demande doit contenir la valeur appSecret. Si tel n'est pas le cas, le serveur renvoie le code d'erreur 401 Unauthorized. Quand {{site.data.keyword.mobilepushshort}} est ajouté à une application, un ID d'application spécifique est créé. Dans le cadre de la réponse, vous obtenez un en-tête intitulé appSecret (valeur confidentielle d'application) qui est utilisé pour créer des balises ou envoyer des messages. L'opération est effectuée via des services dans le catalogue ou le conteneur boilerplate.

Pour obtenir la valeur appSecret :

1. Cliquez sur le *nom d'application* qui est lié au service Push.
2. Cliquez sur le lien **Afficher les données d'identification** pour afficher la valeur confidentielle d'application (ID d'application).

L'écran **Afficher les données d'identification** affiche des informations sur la valeur confidentielle d'application :
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


**Remarque** : Les applications plus anciennes ne devaient transmettre le clientSecret que lors de l'enregistrement ou de la mise à jour
d'appareils avec la zone userId. Toutes les autres interfaces API invoquées par des clients mobiles et de navigateur n'avaient pas besoin de clientSecret. Toutes ces anciennes applications peuvent continuer à se servir facultativement de clientSecret pour les enregistrements d'appareil ou la mise à jour des appels. Il est toutefois vivement conseillé d'appliquer une vérification clientSecret pour tous les appels d'API client. Pour mettre en oeuvre ce processus dans les applications existantes, une nouvelle API, `verifyClientSecret`, a été publiée.  Pour les nouvelles applications, la vérification clientSecret sera mise en oeuvre sur tous les appels d'API client et ce comportement ne peut être modifié avec l'API `verifyClientSecret`.

Par défaut, la vérification de la valeur confidentielle n'est appliquée que dans les nouvelles applications, mais aussi bien les applications existantes que les applications nouvelles sont autorisées à activer ou désactiver cette vérification en utilisant l'API REST verifyClientSecret. Il est conseillé d'imposer la vérification de la valeur confidentielle pour éviter d'exposer des appareils à des utilisateurs qui pourraient avoir connaissance des valeurs applicationId et deviceId.

Prenez soin de préserver la confidentialité de clientSecret `clientSecret` et ne procédez jamais à un codage en dur dans l'application mobile. Il existe différents modèles d'initialisation d'application qui peuvent être utilisés pour extraire dynamiquement la valeur confidentielle `clientSecret` durant l'exécution de l'application. Le diagramme de séquence illustre un tel scénario possible.
![Enable_Push](images/init_client_secret.jpg) 



