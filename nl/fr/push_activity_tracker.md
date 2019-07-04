---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Evénements Activity Tracker
{: #push_activity_tracker}

Le service {{site.data.keyword.cloudaccesstrailfull}} surveille l'interaction d'un utilisateur avec les services IBM Cloud. Vous pouvez rechercher et analyser comment vos utilisateurs et vos applications interagissent avec des services IBM Cloud.

Les administrateurs, responsables de la sécurité et développeurs de cloud disposent des possibilités suivantes :

<dl>
	<dt>Acquisition des informations sur votre environnement afin de surveiller et d'enquêter sur les failles de sécurité </dt>
	<dd>Capturez les interactions des utilisateurs et applications avec les ressources mises à votre disposition par IBM Cloud. Enquêtez sur les éventuels failles de sécurité ou accès non autorisés.</dd>
	<dt>Réalisation de vos objectifs en matière de règlement, de conformité et de conservation des enregistrements</dt>
	<dd>Stockez les événements capturés aussi longtemps que nécessaire, sauvegardés avec des solutions de stockage économiques sur le cloud. Analysez vos données d'événement collectées via une API ou exportez vos données d'activité de cloud.</dd>
	<dt>Transparence du cloud pour que vos équipes DevOps puissent effectuer le débogage et la planification de la capacité</dt>
	<dd>Les événements d'activité du cloud offrent une transparence de vos opérations informatiques sur IBM Cloud. Spécifiez la date et la méthode d'utilisation des services de votre cloud pour l'isolation et le débogage de vos applications. Une requête a collecté des données au cours d'une certaine durée pour anticiper la croissance de votre cloud et les besoins saisonniers.</dd>
	<dt>Simplification de la collecte et amélioration de la sécurité de votre cloud</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}} capture automatiquement vos événements IBM Cloud.</dd>
</dl>


Les journaux d'activité {{site.data.keyword.cloudaccesstrailshort}} fournissent les informations suivantes :

- Utilisateurs ayant effectué des appels d'API à des services cloud.
- Adresse IP source depuis laquelle les appels d'API ont été effectués.
- Horodatage des appels d'API.
- Statut de l'appel d'API.

## Liste des événements
{: #actions}

Le tableau suivant répertorie les événements {{site.data.keyword.cloudaccesstrailshort}} pour {{site.data.keyword.mobilepushshort}}
<table>
  <caption>Tableau 1. Liste des actions qui génèrent un événement</caption>
  <tr>
    <th>Action </th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>Mise à jour de l'application</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>Suppression de la configuration de l'application</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>Mise à jour de la configuration de l'application</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>Création d'étiquette</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>Suppression d'étiquette</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>Mise à jour d'étiquette</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Création de webhook</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Suppression de webhook</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Mise à jour de webhook</td>
  </tr>   
</table>


Pour plus d'informations sur l'utilisation d'{{site.data.keyword.cloudaccesstrailshort}}, voir la [documentation ici](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}.


Actuellement, les événements Activity Tracker sont disponibles uniquement sur `IBM Cloud - Région Sud des Etats-Unis`.
{: note}
