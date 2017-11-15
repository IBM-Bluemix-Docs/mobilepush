---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificações com base em plataforma
{: #notification_platform}


Notificações podem ser
destinada a atingir uma plataforma de dispositivo
específica. Por exemplo, uma notificação pode ser enviada a todos os usuários do Android
ou somente a usuários do Google Chrome. Para enviar uma notificação baseada em
plataforma usando a API REST, assegure-se de que as plataformas
destinadas sejam fornecidas ao postar no recurso de mensagem. Especifique as plataformas como uma matriz. As plataformas
suportadas são como a seguir:

* A (Apple)
* G (Google)
* WEB_CHROME (Google Chrome Browser Web Push)
* WEB_FIREFOX (Mozilla Firefox Browser Web Push)
* WEB_SAFARI (Safari Browser Web Push)
* APPEXT_CHROME (Apps Google Chrome e Extensões)
