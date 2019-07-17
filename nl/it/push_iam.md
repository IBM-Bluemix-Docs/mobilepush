---

copyright:
  years:  2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, service access, manage, user roles

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Gestione dell'accesso al servizio
{: #service-access-management}

Con l'account {{site.data.keyword.mobilepushshort}} e {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM), i proprietari possono gestire l'accesso degli utenti nel tuo account.
{: shortdesc}

Come proprietario dell'account, puoi impostare delle politiche all'interno del tuo account per creare diversi livelli di accesso per i vari utenti. Ad esempio, alcuni utenti possono avere accesso in **Sola lettura** a un'istanza, ma l'accesso in **Scrittura** a un'altra. Puoi decidere chi è autorizzato a creare, aggiornare ed eliminare le istanze di {{site.data.keyword.mobilepushshort}}.

**Nota:** poiché il servizio {{site.data.keyword.mobilepushshort}} ha iniziato ad utilizzare IAM, il segreto applicazione non sarà generato per le nuove istanze. Devi invece utilizzare le [chiavi API](https://cloud.ibm.com/docs/iam?topic=iam-manapikey).

## Ruoli utente
{: #roles}

L'ambito di una politica di accesso si basa sul ruolo assegnato di un utente.
{: shortdesc}

Le politiche consentono di concedere l'accesso a diversi livelli. Alcune delle opzioni includono:
<ul><ul>
  <li>Accesso a tutte le istanze del servizio nel tuo account</li>
  <li>Accesso alle istanze di un singolo servizio nel tuo account</li>
  <li>Accesso a una specifica risorsa all'interno di un'istanza</li>
  <li>Accesso a tutti i servizi abilitati IAM nel tuo account</li>
</ul></ul>

I ruoli di gestione della piattaforma consentono agli utenti di eseguire attività sulle risorse del servizio a livello di piattaforma. Ad esempio, è possibile assegnare ruoli per determinare chi può creare o eliminare ID, creare istanze e associare le istanze alle applicazioni. La seguente tabella descrive le azioni correlate ai ruoli di gestione della piattaforma.

<table>
  <tr>
    <th>Ruolo piattaforma</th>
    <th>Autorizzazioni </th>
    <th>Azioni di esempio</th>
  </tr>
  <tr>
    <td><i>Visualizzatore</i></td>
    <td>Visualizza le istanze {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puoi vedere i dati di un utente Cloud Directory o la configurazione del provider di identità.</td>
  </tr>
  <tr>
    <td><i>Editor</i></td>
    <td>Visualizza e associa le istanze {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puoi associare le applicazioni a un'istanza di {{site.data.keyword.mobilepushshort}}.</td>
  </tr>
  <tr>
    <td><i>Operatore</i></td>
    <td>Crea, elimina, modifica, sospendi, riprendi, visualizza o associa le istanze {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puoi creare o eliminare un'istanza {{site.data.keyword.mobilepushshort}} dal catalogo.</td>
  </tr>
  <tr>
    <td><i>Amministratore</i></td>
    <td>Tutte le azioni di gestione per ogni servizio nell'account.</td>
    <td>Puoi eseguire tutte le azioni dell'operatore e hai la possibilità di assegnare politiche ad altri utenti.</td>
  </tr>
</table>

</br>
</br>
La seguente tabella illustra le azioni che sono associate ai ruoli di accesso al servizio. I ruoli di accesso al servizio consentono agli utenti di accedere a {{site.data.keyword.mobilepushshort}} nonché la possibilità di richiamare l'API {{site.data.keyword.mobilepushshort}}.


<table>
  <tr>
    <th>Ruolo servizio</th>
    <th>Autorizzazioni </th>
    <th>Azioni di esempio</th>
  </tr>
  <tr>
    <td><i>Lettore</i></td>
    <td>Visualizza i dati dell'istanza {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puoi visualizzare i dettagli dell'istanza del servizio come dati utente o informazioni sul provider di identità.</td>
  </tr>
  <tr>
    <td> <i>Scrittore o Gestore</i></td>
    <td>Visualizza e modifica un'istanza {{site.data.keyword.mobilepushshort}}.</td>
    <td>Puoi eseguire tutte le azioni del Lettore e modificare l'istanza del servizio, ad esempio modificare la configurazione del provider di identità. </li></ul></td>
  </tr>
</table>

Per ulteriori informazioni sull'assegnazione dei ruoli utente nell'IU, vedi [Gestione dell'accesso IAM](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser).


## Politiche di accesso {{site.data.keyword.mobilepushshort}}
{: #access}

Ad ogni utente che accede al servizio {{site.data.keyword.mobilepushshort}} nel tuo account deve essere assegnata una politica di accesso con un ruolo utente IAM definito. Tale politica determina quali azioni l'utente può eseguire nel contesto del servizio o dell'istanza che selezioni.
{: shortdesc}

Le azioni sono personalizzate e definite dal servizio {{site.data.keyword.Bluemix_notm}} come operazioni consentite nel servizio. Le azioni vengono quindi associate ai ruoli utente IAM. Alcune delle azioni intraprese possono tracciare il servizio {{site.data.keyword.cloudaccesstrailshort}}. Nella seguente tabella, le azioni e le autorizzazioni richieste per {{site.data.keyword.mobilepushshort}} sono associate.

|Azione |Spiegazione |Ruolo richiesto |
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |Ottieni impostazioni applicazione |Gestore, scrittore, lettore |
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |Elimina impostazioni applicazione |Gestore|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |Aggiorna impostazioni applicazione |Gestore|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |Ottieni dispositivi |Gestore, scrittore, lettore |
|`POST /imfpush/v1/apps/{applicationId}/devices` |Registra dispositivo|Gestore, scrittore |
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Aggiorna dispositivo |Gestore, scrittore |
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Elimina dispositivo|Gestore|
|`POST /imfpush/v1/apps/{applicationId}/messages` |Invia messaggi|Gestore, scrittore |
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |Invia messaggi in blocco |Gestore, scrittore |
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |Elimina messaggio|Gestore|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |Ottieni messaggi|Gestore, lettore, scrittore|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |Aggiorna stato di consegna del messaggio|Gestore, scrittore |
|`POST /imfpush/v1/apps/{applicationId}/tags` |Crea tag|Gestore, scrittore |
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Aggiorna tag   |Gestore, scrittore |
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Elimina tag |Gestore|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |Ottieni le tag |Gestore, lettore, scrittore|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |Crea sottoscrizioni|Gestore, scrittore |
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |Elimina sottoscrizioni|Gestore|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |Ottieni sottoscrizioni|Gestore, lettore, scrittore|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |Crea webhook |Gestore, scrittore |
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Aggiorna webhook|Gestore, scrittore |
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Elimina webhook |Gestore|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |Ottieni webhook |Gestore, lettore, scrittore|-|

## Gestione delle chiavi API
{: #apikeys}

Al momento della creazione delle credenziali del servizio, puoi notare che viene visualizzata un'apiKey invece dell'appSecret.

Per utilizzare tutte le API REST, devi generare il token di accesso tramite il seguente comando curl:

### Parametri 

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### Risposta

```
{
    "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```

Nel momento in cui generi il token di accesso tramite il precedente comando curl, puoi utilizzare le API REST passando ‘Bearer <value of access_token>’ nell'intestazione dell'autorizzazione

Ad esempio:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

Per ulteriori informazioni su IAM, vedi [Accesso IAM](https://cloud.ibm.com/docs/iam?topic=iam-userroles).
