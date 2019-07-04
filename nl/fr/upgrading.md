---

copyright:
  years: 2015, 2017, 2018, 2019
lastupdated: "2019-06-11"

keywords: push notifications, notifications, upgrading plan, lite, basic, advanced

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}


# Mise à niveau de votre plan
{: #upgrade-push}

Le service {{site.data.keyword.mobilepushshort}} offre trois plans qui fournissent différents niveaux de ressources et de fonctions adaptés à vos besoins.
{: shortdesc}

## Plan de tarification
{: #pricing-plan}

**Remarque :**
 - Une notification push envoyée à un point de terminaison/périphérique unique ou un événement de webhook constitue un message numérique. 
 - Un périphérique adressable est un périphérique sur lequel est installée une application qui peut être adressée par le service Cloud.
 - Les services du plan simplifié "Lite" sont supprimés au bout de 30 jours d'inactivité.

|                |Lite                           |Standard                        |Avancé                      |
|----------------|-------------------------------|-----------------------------|------------------------------|
|**Fonction**    |100.000 messages numériques par mois et 50 périphériques adressables |Premier million de messages numériques et premiers 10.000 périphériques adressables gratuits            | Facturé par Instance </br> Inclut 100 millions de messages numériques et 1 million de périphériques adressables<br/> Fonctions avancées<br/> - [Paramétrer les messages](/docs/services/mobilepush?topic=mobile-pushnotification-template_based_notifications)<br/> - [Suivi du cycle de vie des message de bout en bout](/docs/services/mobilepush?topic=mobile-pushnotification-message-delivery-status)<br/>|
|**Tarif**     |Gratuit|- 1$/10 000 périphériques adressables<br/> - 1$/million de messages numériques <br /> |- 100$/instance <br/> - 0.50$/ million de messages numériques <br/> - 0.50$/million de périphériques adressables<br/> |-|
{:caption="Tableau 1. Plans de service" caption-side="top"}


## Mise à niveau d'un service
{: #upgrading-a-service}

Pour mettre votre plan à niveau, procédez comme suit :

1.  Dans le menu {{site.data.keyword.Bluemix_notm}}, sélectionnez **Services** > **Tableau de bord**.
2.  Sélectionnez l'instance de service que vous souhaitez mettre à niveau afin de l'ouvrir.
3.  Cliquez sur **Plan** dans le panneau de navigation.
   Votre plan en cours s'affiche avec d'autres options de plan disponibles, et vous pouvez effectuer des modifications.

Pour plus d'informations sur le calcul des coûts, voir la [calculatrice de tarif {{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/estimator){: new_window}.
