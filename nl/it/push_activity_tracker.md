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

# Eventi del programma di traccia dell'attività
{: #push_activity_tracker}

Il servizio {{site.data.keyword.cloudaccesstrailfull}} monitora l'interazione di un utente con i servizi IBM Cloud. Puoi cercare e analizzare come gli utenti e le applicazioni interagiscono con i servizi IBM cloud.

Gli sviluppatori, la sicurezza e gli amministratori cloud possono:

<dl>
	<dt>Ottenere approfondimenti sull'ambiente per monitorare e indagare sulle violazioni della sicurezza</dt>
	<dd>Catturare le interazioni di utenti e applicazioni con le risorse IBM Cloud con provisioning. Esaminare eventuali violazioni della sicurezza o accessi non autorizzati.</dd>
	<dt>Raggiungere le esigenze regolamentari, di conformità e di conservazione dei record</dt>
	<dd>Memorizzare gli eventi acquisiti per tutto il tempo necessario, custoditi su soluzioni di storage economiche di classe cloud.  Eseguire query dei tuoi dati di eventi raccolti tramite l'API o esportare i tuoi dati dell'attività cloud.</dd>
	<dt>Trasparenza del cloud per i team DevOps per eseguire il debug e la pianificazione della capacità</dt>
	<dd>Gli eventi di attività cloud offrono trasparenza nelle operazioni IT su IBM Cloud. Identificare quando e come vengono utilizzati i servizi cloud per l'isolamento e il debug delle applicazioni. Eseguire query dei dati raccolti nel tempo per anticipare la crescita del cloud e le esigenze stagionali.</dd>
	<dt>Semplificare la raccolta e migliorare la sicurezza del cloud</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}} cattura automaticamente i tuoi eventi IBM Cloud.</dd>
</dl>


I log di attività {{site.data.keyword.cloudaccesstrailshort}} possono essere utilizzati per identificare le seguenti informazioni:

- Gli utenti che hanno effettuato le chiamate API ai servizi cloud. 
- L'indirizzo IP di origine da dove le chiamate API sono state effettuate.
- La data/ora in cui le chiamate API sono state effettuate.
- Lo stato della chiamata API.

## Elenco degli eventi
{: #actions}

La seguente tabella elenca gli eventi {{site.data.keyword.cloudaccesstrailshort}} per {{site.data.keyword.mobilepushshort}}
<table>
  <caption>Tabella 1. Elenco di azioni che generano un evento</caption>
  <tr>
    <th>Azione </th>
	  <th>Descrizione</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>Aggiorna l'applicazione</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>Eliminazione della configurazione dell'applicazione</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>Aggiornamento della configurazione dell'applicazione</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>Creazione tag</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>Eliminazione tag</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>Aggiornamento tag</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Creazione webhook</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Eliminazione webhook</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Aggiornamento webhook</td>
  </tr>   
</table>


Per ulteriori informazioni sull'utilizzo di {{site.data.keyword.cloudaccesstrailshort}}, fai riferimento alla [documentazione qui](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}.


Al momento, gli eventi del programma di traccia dell'attività sono disponibili solo in `IBM Cloud - US South Region`.
{: note}
