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

# Servicezugriff verwalten
{: #service-access-management}

Mit {{site.data.keyword.mobilepushshort}} und {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) können Kontoeigner den Benutzerzugriff in ihrem Konto verwalten.
{: shortdesc}

Als Kontoeigner können Sie Richtlinien innerhalb Ihres Kontos festlegen, um für verschiedene Benutzer verschiedene Zugriffsebenen zu erstellen. Beispiel: Bestimmte Benutzer können **Lesezugriff** auf eine Instanz und **Schreibzugriff** auf eine andere Instanz haben. Sie können entscheiden, wer Instanzen von {{site.data.keyword.mobilepushshort}} erstellen, aktualisieren und löschen darf.

**Hinweis:** Da der {{site.data.keyword.mobilepushshort}}-Service IAM angenommen hat, wird der geheime Anwendungsschlüssel nicht für die neuen Instanzen generiert. Sie müssen stattdessen die [API-Schlüssel](https://cloud.ibm.com/docs/iam?topic=iam-manapikey) verwenden.

## Benutzerrollen
{: #roles}

Der Bereich einer Zugriffsrichtlinie basiert auf der zugewiesenen Rolle eines Benutzers.
{: shortdesc}

Richtlinien ermöglichen, dass Zugriff auf verschiedenen Ebenen gewährt wird. Zu den Optionen gehören folgende:
<ul><ul>
  <li>Zugriff über alle Instanzen des Service in Ihrem Konto hinweg</li>
  <li>Zugriff auf eine einzelne Serviceinstanz in Ihrem Konto</li>
  <li>Zugriff auf eine bestimmte Ressource innerhalb einer Instanz</li>
  <li>Zugriff auf alle IAM-fähigen Services in Ihrem Konto</li>
</ul></ul>

Plattformmanagementrollen ermöglichen Benutzern das Ausführen von Tasks für Serviceressourcen auf Plattformebene. Beispiel: Rollen können zugewiesen werden, um festzulegen, wer IDs erstellen oder löschen, Instanzen erstellen und Instanzen an Apps binden kann. Die folgende Tabelle enthält Details zu den Aktionen, die mit den Plattformmanagementrollen korrelieren:

<table>
  <tr>
    <th>Plattformrolle</th>
    <th>Berechtigungen</th>
    <th>Beispielaktionen</th>
  </tr>
  <tr>
    <td><i>Anzeigeberechtigter</i></td>
    <td>{{site.data.keyword.mobilepushshort}}-Instanzen anzeigen.</td>
    <td>Sie können die Daten des Cloudverzeichnisbenutzers oder die Identitätsproviderkonfiguration anzeigen.</td>
  </tr>
  <tr>
    <td><i>Bearbeiter</i></td>
    <td>{{site.data.keyword.mobilepushshort}}-Instanzen anzeigen und binden.</td>
    <td>Sie können Anwendungen an eine Instanz von {{site.data.keyword.mobilepushshort}} binden.</td>
  </tr>
  <tr>
    <td><i>Operator</i></td>
    <td>{{site.data.keyword.mobilepushshort}}-Instanzen erstellen, löschen, bearbeiten, aussetzen, wiederaufnehmen, anzeigen oder binden.</td>
    <td>Sie können eine {{site.data.keyword.mobilepushshort}}-Instanz erstellen oder aus dem Katalog löschen.</td>
  </tr>
  <tr>
    <td><i>Administrator</i></td>
    <td>Alle Managementaktionen für alle Services im Konto.</td>
    <td>Sie können alle Bedieneraktionen ausführen und anderen Benutzern Richtlinien zuweisen.</td>
  </tr>
</table>

</br>
</br>
Die folgende Tabelle enthält Details zu den Aktionen, die Servicezugriffsrollen zugeordnet sind. Servicezugriffsrollen ermöglichen Benutzern den Zugriff auf {{site.data.keyword.mobilepushshort}} sowie die Fähigkeit, die {{site.data.keyword.mobilepushshort}}-API aufzurufen.


<table>
  <tr>
    <th>Servicerolle</th>
    <th>Berechtigungen</th>
    <th>Beispielaktionen</th>
  </tr>
  <tr>
    <td><i>Leseberechtigter</i></td>
    <td>{{site.data.keyword.mobilepushshort}}-Instanzdaten anzeigen.</td>
    <td>Sie können die Details der Serviceinstanz anzeigen, wie z. B. Benutzerdaten oder Identitätsproviderinformationen.</td>
  </tr>
  <tr>
    <td> <i>Schreibberechtigter oder Manager</i></td>
    <td>{{site.data.keyword.mobilepushshort}}-Instanz anzeigen und ändern.</td>
    <td>Sie können alle Aktionen eines Leseberechtigten ausführen und die Serviceinstanz bearbeiten, wie z. B. die Identitätsproviderkonfiguration bearbeiten. </li></ul></td>
  </tr>
</table>

Weitere Informationen zum Zuweisen von Benutzerrollen in der Benutzerschnittstelle finden Sie in [IAM-Zugriff verwalten](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser).


## {{site.data.keyword.mobilepushshort}}-Zugriffsrichtlinien
{: #access}

Jedem Benutzer, der auf den {{site.data.keyword.mobilepushshort}}-Service in Ihrem Konto zugreift, muss eine Zugriffsrichtlinie mit einer definierten IAM-Benutzerrolle zugewiesen sein. Diese Richtlinie bestimmt, welche Aktionen der Benutzer im Kontext des Service oder der Instanz ausführen kann, den bzw. die Sie ausgewählt haben.
{: shortdesc}

Die Aktionen werden vom {{site.data.keyword.Bluemix_notm}}-Service als Operationen angepasst und definiert, die im Service ausgeführt werden dürfen. Die Aktionen werden dann IAM-Benutzerrollen zugeordnet. Einige der ausgeführten Aktionen können Sie mit dem {{site.data.keyword.cloudaccesstrailshort}}-Service verfolgen. In der folgenden Tabelle sind die Aktionen und die erforderlichen Berechtigungen für {{site.data.keyword.mobilepushshort}} zugeordnet.

|Aktion |Erläuterung |Erforderliche Rolle |
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |App-Einstellungen abrufen |Manager, Schreibberechtigter, Leseberechtigter|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |App-Einstellungen löschen |Manager|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |App-Einstellungen aktualisieren |Manager|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |Geräte abrufen |Manager, Schreibberechtigter, Leseberechtigter|
|`POST /imfpush/v1/apps/{applicationId}/devices` |Gerät registrieren |Manager, Schreibberechtigter|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Gerät aktualisieren |Manager, Schreibberechtigter|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Gerät löschen |Manager|
|`POST /imfpush/v1/apps/{applicationId}/messages` |Nachrichten senden |Manager, Schreibberechtigter|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |Massennachrichten senden |Manager, Schreibberechtigter|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |Nachricht löschen |Manager|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |Nachrichten abrufen |Manager, Leseberechtigter, Schreibberechtigter|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |Nachrichtenübermittlungsstatus aktualisieren |Manager, Schreibberechtigter|
|`POST /imfpush/v1/apps/{applicationId}/tags` |Tags erstellen |Manager, Schreibberechtigter|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Tag aktualisieren |Manager, Schreibberechtigter|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Tag löschen |Manager|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |Tags abrufen|Manager, Leseberechtigter, Schreibberechtigter|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |Subskriptionen erstellen |Manager, Schreibberechtigter|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |Subskriptionen löschen |Manager|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |Subskriptionen abrufen |Manager, Leseberechtigter, Schreibberechtigter|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |Webhook erstellen |Manager, Schreibberechtigter|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Webhook aktualisieren |Manager, Schreibberechtigter|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Webhook löschen |Manager|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |Webhook abrufen |Manager, Leseberechtigter, Schreibberechtigter|-|

## Mit API-Schlüsseln arbeiten
{: #apikeys}

Nach dem Erstellen von Serviceberechtigungsnachweisen wird möglicherweise ein API-Schlüssel (apiKey) anstelle des geheimen App-Schlüssels (appSecret) angezeigt.

Damit Sie REST-APIs verwenden können, müssen Sie das Zugriffstoken mit dem folgenden curl-Befehl generieren:

### Parameter

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### Antwort

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

Nach dem Generieren des Zugriffstokens mit dem oben genannten curl-Befehl können Sie die REST-API betreiben, indem Sie ‘Bearer <Wert von access_token>’ im Berechtigungsheader übergeben.

Beispiel:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

Weitere Informationen zu IAM finden Sie in [IAM-Zugriff](https://cloud.ibm.com/docs/iam?topic=iam-userroles).
