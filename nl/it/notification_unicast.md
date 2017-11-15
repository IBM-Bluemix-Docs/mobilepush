---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifiche Unicast
{: #notification_unicast}


Le notifiche Unicast sono messaggi destinati a un dispositivo o un utente particolare. Le notifiche Unicast destinate ai dispositivi non richiedono alcuna impostazione aggiuntiva e sono abilitate per impostazione predefinita quando l'applicazione è abilitata per {{site.data.keyword.mobilepushshort}}.

Tuttavia, le notifiche Unicast indirizzate agli utenti richiedono l'associazione di un ID utente a un dispositivo al momento della registrazione del dispositivo mobile client o del browser web o delle estensioni e delle applicazioni Chrome per {{site.data.keyword.mobilepushshort}}.   

Normalmente, un'applicazione client prima eseguirà un ciclo di autenticazione in cui l'utente dell'applicazione mobile viene autenticato in un servizio di autenticazione come [Mobile Client Access](docs/services/mobileaccess/index.html). Dopo la corretta autenticazione, l'ID dell'utente autenticato viene trasmesso all'API Push Device Registration. 

Per inviare notifiche Unicast tramite l'API REST, assicurati che gli ID del dispositivo o dell'utente siano forniti durante l'inserimento in una risorsa messaggi.
