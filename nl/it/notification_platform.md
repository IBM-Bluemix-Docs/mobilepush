---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifiche basate sulla piattaforma
{: #notification_platform}


Il recapito delle notifiche può essere destinato a una specifica piattaforma di dispositivo. Ad esempio, una notifica può essere inviata solo a tutti gli utenti Android o solo agli utenti Google Chrome. Per inviare una notifica basata sulla
                            piattaforma che utilizza la API REST, assicurati che le piattaforme
                            di destinazione siano fornite all'inserimento in una risorsa messaggi. Specifica
                            le piattaforme come un array. Le piattaforme supportate sono:

* A (Apple)
* G (Google)
* WEB_CHROME (Google Chrome Browser Web Push)
* WEB_FIREFOX (Mozilla Firefox Browser Web Push)
* WEB_SAFARI (Safari Browser Web Push)
* APPEXT_CHROME (Google Chrome Apps & Extensions)
