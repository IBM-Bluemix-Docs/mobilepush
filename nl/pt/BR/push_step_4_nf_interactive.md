---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificações interativas e silenciosas  
{: #interactive-notifications}
Última atualização: 22 de maio de 2017
{: .last-updated}

As notificações interativas permitem que os usuários respondam a uma notificação sem abrir o aplicativo. Quando uma notificação interativa chega, o dispositivo mostra os botões de ação junto com a mensagem de notificação. 

**Nota:** as notificações interativas não são suportadas em dispositivos iOS com versões anteriores à 8. 

## Enviando notificações interativas
{: #send_interactive_notifications}

A notificação interativa pode ser enviada usando o console de Notificações push ou usando a [documentação da API de REST](push_restapi.html).

No console de {{site.data.keyword.mobilepushshort}}: 

1. Na guia de notificação, clique em **Enviar notificação**. 
2. Escolha seus destinatários de notificação e clique em **Avançar**. 
3. Na página de composição de notificação, o push interativo pode ser enviado configurando o Tipo como Padrão ou Combinado e especificando o valor de Categoria na guia Opções avançadas. 

## Manipulando notificações interativas 
{: #handle_interactive_notifications}

- Para o iOS, passe por [Ativar e manipular notificações interativas em aplicativos Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications).
- Para o Cordova, passe por [Ativar e manipular notificações interativas em aplicativos Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications).
- Para o Android, passe por [Ativar e manipular notificações interativas em aplicativos Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications).


## Manipulando notificações silenciosas para iOS
{: #send_silent_notifications_for_ios}

As notificações silenciosas não aparecem na tela do dispositivo e são recebidas pelo aplicativo no segundo plano. Para obter mais informações, veja [Notificações silenciosas em dispositivos iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification).
