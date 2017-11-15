---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# API REST Push Notifications
{: #push-api-rest}
Dernière mise à jour : 22 mai 2017
{: .last-updated}

Vous pouvez utiliser une interface de programmation d'application REST (Representational State Transfer) pour {{site.data.keyword.mobilepushshort}}. Vous pouvez également utiliser le SDK et l'[API Push ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobile.{DomainName}/imfpush/){: new_window} pour affiner plus encore le développement de vos applications client.

Avec l'API REST Push, les applications serveur de back end et les clients peuvent accéder à des fonctions {{site.data.keyword.mobilepushshort}}.

- Enregistrements d'appareil
- Enregistrements
- Messages
- Abonnements
- Balises
- Webhooks

Pour obtenir l'URL de base pour l'API REST, procédez comme suit :

1. Créez une application de back end dans la section Conteneurs boilerplate du catalogue Bluemix®, en choisissant MobileFirst Services Starter, ce qui a pour effet de lier le service {{site.data.keyword.mobilepushshort}} à l'application. Vous pouvez aussi créer une instance de service de Push et la laisser non liée. 
1. Dans la page principale du catalogue Bluemix, accédez à la zone **Applications** et sélectionnez votre application.
3. Cliquez sur **OPTIONS POUR APPLICATION MOBILE**. Les valeurs de route et d'identificateur global unique de l'application sont affichées au début de la page des détails de votre application. L'écran Afficher les données d'identification affiche des informations sur la valeur confidentielle AppSecret. Vous pouvez obtenir la valeur confidentielle d'application depuis les options pour application mobile ainsi que la valeur confidentielle de client pour certaines des interfaces API.

Vous pouvez aussi utiliser la ligne de commande pour obtenir les données d'identification pour le service :

```
    cf create-service-key {push_instance_name} {key_name}

 cf service-key {push_instance_name} {key_name}
```
	{: codeblock}

## En-tête Accept-Language
{: #push-api-rest-accept}

L'en-tête "Accept-Language" spécifie la langue à utiliser pour les messages d'erreur générés par  l'[API REST Push ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobile.{DomainName}/imfpush/){: new_window}. Les langues suivantes sont prises en charge pour les messages d'erreur : chinois (simplifié), chinois (traditionnel), anglais (Etats-Unis), allemand, français, italien, japonais, coréen, portugais et espagnol.


## Filtres des API REST Push
{: #push-api-rest-filters}

Les filtres définissent un critère de recherche permettant de restreindre les données qui sont renvoyées depuis une API GET de {{site.data.keyword.mobilepushshort}}. Appliquez les filtres au résultat de l'opération Get à filtrer. Le filtre restreint le nombre d'entrées incluses dans le résultat. Ainsi, vous pouvez utiliser un filtre pour rechercher des balises commençant par "test". 

Les filtres peuvent être générés en utilisant la syntaxe suivante :

**nom** : nom de la zone sur laquelle le filtre est appliqué.

**opérateur** : == (correspondance exacte) ou =@ (contient une sous-chaîne) qui décrit la correspondance de filtre à utiliser.

**expression** : valeurs à inclure dans le résultat.

Dans une expression, les virgules et les barres obliques inversées doivent être précédées d'une barre oblique inversée.

Si vous utilisez plusieurs filtres, vous pouvez les combiner avec la logique AND ou OR.

- Pour la logique AND, utilisez plusieurs filtres dans la requête.
- Pour la logique OR, utilisez une virgule (,) dans l'expression de filtre.
- Pour la logique AND et OR : une requête simple peut comporter les deux logiques, AND et OR. Chaque filtre est évalué individuellement avant que les filtres ne soient combinés dans une expression AND.

Pour l'API GET d'appareil, les combinaisons suivantes sont prises en charge :
-Le nom est la zone de plateforme.
- Sauf pour platform, l'opérateur peut être == ou =@
- Pour platform, l'opérateur doit être ==. Si l'opérateur =@ est utilisé, la valeur peut être une sous-chaîne.
- Si l'opérateur == est utilisé, la valeur doit être une chaîne qui correspond exactement.

Pour l'API GET d'abonnement, les combinaisons suivantes sont prises en charge :

- Le nom peut être l'une des zones suivantes : tagName ou deviceId
- Sauf pour platform, l'opérateur peut être == ou =@
- Pour platform, l'opérateur doit être ==
- Si l'opérateur =@ est utilisé, la valeur peut être une sous-chaîne. Si l'opérateur == est utilisé, la valeur doit être une chaîne qui correspond exactement.
- Pour l'API GET d'étiquette, les combinaisons suivantes sont prises en charge :
- Le nom peut être l'une des zones suivantes : “name” ou “description”
- Si l'opérateur =@ est utilisé, la valeur peut être une sous-chaîne.
- Si l'opérateur == est utilisé, la valeur doit être une chaîne qui correspond exactement.


## Codes de réponse du service Push Notifications
{: #push-api-response-codes}

Status: 405 Method Not Allowed - Appropriate method expected.
