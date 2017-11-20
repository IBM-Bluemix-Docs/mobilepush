---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Notifiche broadcast 
{: #broadcast_notifications}

Le notifiche broadcast sono messaggi destinati a tutte le istanze di un'applicazione installate nei dispositivi mobili, nei browser o implementate come applicazioni Chrome o istanze dell'estensione e configurate per il servizio {{site.data.keyword.mobilepushshort}}. Le notifiche broadcast sono abilitate per impostazione predefinita con qualsiasi applicazione abilitata per {{site.data.keyword.mobilepushshort}}.

Quando un'applicazione client si registra al servizio {{site.data.keyword.mobilepushshort}}, può iniziare a ricevere i broadcast. Le applicazioni abilitate per il servizio {{site.data.keyword.mobilepushshort}} hanno una sottoscrizione predefinita alla tag Push.ALL, che viene utilizzata dal server per eseguire il broadcast dei messaggi di notifica a tutti i dispositivi. Per inviare una notifica broadcast che utilizza la API Push
                        REST, assicurati che la destinazione ("target") sia un JSON vuoto all'inserimento nella
                        risorsa messaggi.
