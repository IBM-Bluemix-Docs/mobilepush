---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificações do rich media
{: #interactive-notifications}
Última atualização: 13 de julho de 2017
{: .last-updated}


É possível ativar o Rich Media {{site.data.keyword.mobilepushshort}} no iOS 10 e mais recente. As notificações push podem ser enviadas com Áudio, Vídeo, GIFs e imagens. 

Para configurar o aplicativo para receber rich push no iOS 10, conclua as etapas:  

1. Em Xcode, selecione **Arquivo** > **Novo** > **Destino** > **Extensão de serviço de notificação**.
2. No método `didReceive()` no `UNNotificationServiceExtension`, inclua o código.
```
BMSPushRichPushNotificationOptions.didReceive(request, withContentHandler: contentHandler)
```
	{: codeblock}	

Para enviar um Rich Media {{site.data.keyword.mobilepushshort}} do console de Push, assegure-se de especificar os campos de mensagem, título, subtítulo e attachmentURL.
