---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificações unicast
{: #notification_unicast}


Notificações unicast são mensagens destinadas a um dispositivo ou usuário específico. As notificações unicast destinadas a dispositivos não requerem configuração adicional e são ativadas por padrão quando o aplicativo está ativado para o {{site.data.keyword.mobilepushshort}}.

No entanto, as notificações Unicast destinadas para usuários requerem a associação de um ID do usuário com um dispositivo no momento do registro do dispositivo
móvel, do navegador da web ou de Apps Chrome e Extensões do cliente para {{site.data.keyword.mobilepushshort}}.   

Geralmente, um aplicativo cliente executará, primeiramente, um ciclo de autenticação no qual o usuário do app móvel é autenticado em um serviço como
[Mobile Client Access](docs/services/mobileaccess/index.html). Na autenticação bem-sucedida, o ID de usuário autenticado então é passado para a API de
registro de dispositivo push. 

Para enviar notificações Unicast por meio da API REST, assegure-se de que os deviceIds ou userIds sejam fornecidos ao postar em um recurso de mensagem.
