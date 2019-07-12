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

# Activity Tracker-Ereignisse
{: #push_activity_tracker}

Der {{site.data.keyword.cloudaccesstrailfull}}-Service überwacht die Interaktion eines Benutzers mit den IBM Cloud-Services. Sie können Suchen ausführen und analysieren, wie Ihre Benutzer und Anwendungen mit IBM Cloud-Services interagieren.

Cloudadministratoren, Sicherheitspersonal und Entwickler können Folgendes:

<dl>
	<dt>Einblicke in Ihre Umgebung gewinnen, um Sicherheitsverletzungen zu überwachen und zu untersuchen</dt>
	<dd>Benutzer- und Anwendungsinteraktionen mit Ihren bereitgestellten IBM Cloud-Ressourcen erfassen. Mögliche Sicherheitsverletzungen oder unbefugten Zugriff untersuchen.</dd>
	<dt>Ihre Bedürfnisse hinsichtlich der Einhaltung gesetzlicher Bestimmungen, Konformität und Aufbewahrung von Datensätzen erfüllen</dt>
	<dd>Erfasste Ereignisse so lange wie benötigt sicher auf wirtschaftlichen Speicherlösungen der Cloudklasse speichern. Fragen Sie Ihre erfassten Ereignisdaten über eine API ab oder exportieren Sie Ihre Cloudaktivitätsdaten.</dd>
	<dt>Cloudtransparenz für Ihre DevOps-Teams zum Debuggen und zum Ausführen der Kapazitätsplanung</dt>
	<dd>Cloudaktivitätsereignisse bringen Transparenz in Ihren IT-Betrieb in der IBM Cloud. Ermitteln Sie, wann und wie Ihre Cloud-Services verwendet werden, um Ihre Anwendungen zu isolieren und zu debuggen. Fragen Sie die innerhalb eines bestimmten Zeitraums erfassten Daten ab, um Ihren Bedarf an Cloudwachstum und den saisonalen Bedarf einzuschätzen.</dd>
	<dt>Datenerfassung vereinfachen und Cloudsicherheit verbessern</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}} erfasst automatisch Ihre IBM Cloud-Ereignisse.</dd>
</dl>


Die {{site.data.keyword.cloudaccesstrailshort}}-Aktivitätenprotokolle können zum Ermitteln der folgenden Informationen verwendet werden:

- Die Benutzer, die API-Aufrufe an Cloud-Services ausgeführt haben.
- Die Quellen-IP-Adresse, von der die API-Aufrufe ausgeführt wurden.
- Die Zeitmarke, zu der die API-Aufrufe ausgeführt wurden.
- Der Status des API-Aufrufs.

## Ereignisliste
{: #actions}

In der folgenden Tabelle werden die {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse für {{site.data.keyword.mobilepushshort}} aufgelistet.
<table>
  <caption>Tabelle 1. Liste der Aktionen, die ein Ereignis generieren</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>Aktualisierungen der Anwendung</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>Löschen der Anwendungskonfiguration</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>Aktualisierung der Anwendungskonfiguration</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>Erstellen von Tags</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>Löschen von Tags</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>Aktualisierung von Tags</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Erstellen von Webhooks</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Löschen von Webhooks</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Aktualisierung von Webhooks</td>
  </tr>   
</table>


Weitere Informationen zum Arbeiten mit {{site.data.keyword.cloudaccesstrailshort}} finden Sie in der [Dokumentation](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}.


Zurzeit sind die Activity Tracker-Ereignisse nur in `IBM Cloud - US South Region` verfügbar.
{: note}
