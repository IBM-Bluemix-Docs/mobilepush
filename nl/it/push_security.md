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

# Sicurezza in Push Notifications 
{: #overview-push}
Ultimo aggiornamento: 27 giugno 2017
{: .last-updated}


Le API {{site.data.keyword.mobilepushshort}} sono protette da due tipi di segreti: 

- **appSecret**: l'`appSecret` protegge le API normalmente richiamate dalle applicazioni di backend, come l'API per inviare {{site.data.keyword.mobilepushshort}} e l'API per configurare le impostazioni.
- **clientSecret**:  il `clientSecret` protegge le API normalmente richiamate dalle applicazioni client mobili. C'è solo una API correlata alla registrazione di un dispositivo con un ID utente associato che richiede questo `clientSecret`. Nessuna delle altre API richiamate dai client mobili richiede il `clientSecret`. 

L'`appSecret` e il `clientSecret` vengono assegnati a ogni istanza del servizio al momento del bind di un'applicazione al servizio {{site.data.keyword.mobilepushshort}}. Fai riferimento alla documentazione [API REST ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://mobile.{DomainName}/imfpush/) per informazioni su come i segreti vengono trasmessi e a quale API.

## appSecret 
{: #push-api-rest-secret}

Quando un'applicazione esegue il bind a {{site.data.keyword.mobilepushshort}}, il servizio genera una appSecret (una chiave univoca) e la passa nell'intestazione di risposta. Se stai utilizzando IBM {{site.data.keyword.mobilepushshort}} per la API Rest IBM Cloud, utilizza la guida di riferimento alle API REST per ottenere informazioni su quali API devi proteggere. Per informazioni, vedi [API REST Push ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://mobile.{DomainName}/imfpush/){: new_window}.

L'intestazione di richiesta deve contenere l'appSecret. In caso contrario, il server restituisce un codice di errore
                401 Non autorizzato. Quando {{site.data.keyword.mobilepushshort}} viene aggiunto a un'applicazione, viene creato uno specifico AppID. Come parte della risposta, ottieni un'intestazione denominata appSecret che viene utilizzata per la creazione di tag o l'invio di messaggi. L'operazione viene eseguita tramite i servizi nel catalogo o
                nel contenitore tipo.

Per ottenere il valore appSecret:

1. Fai clic sul * nome-applicazione* associato al servizio push.
2. Fai clic sul link **Visualizza credenziali** per visualizzare
                        l'appSecret (AppID).

La schermata **Visualizza credenziali** mostra le informazioni sull'AppSecret:
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


**Nota**: sono necessarie le precedenti applicazioni per trasmettere il clientSecret solo quando viene seguita la registrazione o l'aggiornamento dei dispositivi con il campo userID. Tutte le altre API richiamate dai client mobili e browser non richiedono il clientSecret. Queste vecchie applicazioni possono continuare ad utilizzare il clientSecret facoltativamente per le registrazioni del dispositivo o per l'aggiornamento delle chiamate. Tuttavia, è fortemente raccomandato che il controllo clientSecret venga applicato a tutte le chiamate API client. Per applicarlo alle applicazioni esistenti, è stata pubblicata una nuova API denominata `verifyClientSecret`.  Per le nuove applicazioni, il controllo clientSecret sarà imposto per tutte le chiamate API client e questo comportamento non può essere modificato con l'API `verifyClientSecret`.

Per impostazione predefinita, la verifica del segreto client viene forzata solo nelle nuove applicazioni. Alle applicazioni nuove e esistenti è consentito abilitare o disabilitare la verifica del segreto client utilizzando l'API REST verifyClientSecret. Ti raccomandiamo di forzare la verifica del segreto client per evitare l'esposizione dei dispositivi agli utenti che possono conoscere il applicationId e il deviceId.

Assicurati che il `clientSecret` sia mantenuto riservato e che non venga mai impostato come hard-coded nell'applicazione mobile. Esistono vari modelli di inizializzazione dell'applicazione che possono essere utilizzati per estrarre dinamicamente il `clientSecret` durante il runtime delle applicazioni. Il diagramma della sequenza illustra il possibile modello.
![Enable_Push](images/init_client_secret.jpg) 



