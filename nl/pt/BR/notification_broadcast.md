---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# As notificações de transmissão 
{: #broadcast_notifications}

Notificações de
transmissão são mensagens destinadas a todas as instâncias de um aplicativo instalado em dispositivos móveis, navegadores ou implementadas como apps Chrome ou
instâncias de extensão e configuradas para o serviço {{site.data.keyword.mobilepushshort}}. As notificações de transmissão são ativadas por padrão para qualquer aplicativo ativado para {{site.data.keyword.mobilepushshort}}.

Quando um aplicativo cliente se registra no serviço {{site.data.keyword.mobilepushshort}}, ele pode começar a receber transmissões. Aplicativos ativados para o serviço {{site.data.keyword.mobilepushshort}} possuem uma assinatura predefinida para a tag Push.ALL, que é usada pelo servidor para transmitir mensagens de notificação para todos os dispositivos. Para enviar uma
notificação de transmissão usando a API Push REST, assegure-se de que
o "destino" seja um JSON vazio ao postar no recurso de mensagens.
