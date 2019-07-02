---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, sending a notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Etapa 5: Enviando uma notificação
{: #push_step_4}

Depois de ter desenvolvido seus aplicativos, será possível enviar notificações push básicas.

Para enviar notificações push básicas, conclua as etapas a seguir:

1. Selecione **Mensagens** e componha uma mensagem escolhendo uma opção **Enviar para**. As opções suportadas são **Dispositivo por tag**, **ID do dispositivo**, **ID do usuário**, **Dispositivos Android**, **Dispositivos iOS**, **Notificações da web**, **Apps e extensões do Chrome**, **Navegador Chrome**, **Firefox**, **Safari** e **Todos os dispositivos**.
**Nota**: ao selecionar a opção **Todos os dispositivos**, todos os dispositivos inscritos para {{site.data.keyword.mobilepushshort}} receberão notificações.
	
    ![Tela Notificações](images/tag_notification.jpg "Tela Enviar notificações mostrando os campos Enviar para, Mensagem e Carga útil adicional")

2. No campo **Mensagem**, componha sua mensagem. Escolha a
configurar das definições opcionais conforme necessário.
3. Clique em **Enviar**.
3. Verifique se seus dispositivos ou navegador receberam a notificação.

A captura de tela a seguir mostra uma caixa de alerta que
manipula uma notificação push no primeiro plano em um dispositivo Android.

![Notificação de push de primeiro plano no Android](images/Android_Screenshot.jpg "Caixa de alerta com notificação de teste")

A captura de tela a seguir mostra uma notificação push no plano de fundo para Android.

![Notificação de push de segundo plano no Android](images/background.jpg "Notificação de push em um dispositivo Android")

## Configurações opcionais do Android 
{: #push_step_4_Android}

É possível customizar ainda mais as configurações do {{site.data.keyword.mobilepushshort}} para enviar notificações a dispositivos Android. 

![Configurações customizadas do Android](images/android_custom_settings.jpg "Página de configurações customizadas de notificações de push")

As opções de customização opcionais a seguir são suportadas:

- Chave de redução: as chaves de redução são anexadas às notificações. Se diversas notificações chegarem sequencialmente com a mesma chave de redução quando o dispositivo estiver off-line, elas serão reduzidas. Quando um dispositivo fica on-line, ele recebe notificações do servidor FCM e exibe somente a notificação mais recente que comporta a mesma chave de redução. Se a chave de redução não estiver configurada, as mensagens novas e antigas serão armazenadas para entrega futura.
- Som: indica que um clique de som seja reproduzido no recebimento de uma notificação. Suporta o padrão ou o nome de um recurso de som empacotado no app.
- Ícone: especifique o nome do ícone a ser exibido para a notificação. Assegure-se de ter empacotado o ícone na pasta `res/drawable` com o aplicativo cliente.
- Prioridade: especifica as opções para designar prioridade de entrega às mensagens. 
	- Uma prioridade `high` ou `max` resultará em notificação heads-up.
	- Uma prioridade `low` ou `default` não abrirá conexões de rede em um dispositivo inativo. 
	- Uma prioridade `min` será uma notificação silenciosa.
- Visibilidade: é possível optar por configurar a opção de visibilidade de notificação como `public` ou `private`. 
	- A opção `private` restringe a visualização pública, e é possível optar por ativá-la se seu dispositivo é protegido com pin ou um padrão e a configuração de notificação está configurada como **Ocultar conteúdo de notificação confidencial**. Quando a visibilidade for configurada como `private`, um campo `redact` deverá ser mencionado. Somente o conteúdo especificado no campo `redact` será exibido em uma tela bloqueada segura no dispositivo. 
	- A opção `public` renderiza as notificações para serem lidas livremente.
- Time to live: esse valor é configurado em segundos. Se esse parâmetro não for especificado, o servidor FCM armazenará a mensagem por quatro semanas e tentará entregar. A validade expira após quatro semanas. A faixa de valores possíveis vai de 0 a 2.419.200 segundos.
- Atrasar quando inativo: isso pode ser configurado para um dos valores a seguir:
	- `True` instrui o servidor FCM a não entregar a notificação se o dispositivo estiver inativo. 
	- `False` assegura a entrega de notificação mesmo se o dispositivo estiver inativo.
- Sincronizar: a configuração dessa opção como `true` sincroniza as notificações entre todos os dispositivos registrados. Se o usuário com um nome de usuário tiver diversos dispositivos com o mesmo aplicativo instalado, a leitura da notificação em um dispositivo assegura a exclusão das notificações nos outros dispositivos. É preciso assegurar-se de estar registrado no serviço {{site.data.keyword.mobilepushshort}} com userId para que essa opção funcione.
- Carga útil adicional: especifica os valores de carga útil customizados para suas notificações.
- Notificação expansível: fornece aos clientes uma opção para expandir uma notificação com mais informações, embora uma notificação básica fosse visível com a notificação reduzida. As seguintes opções são suportadas:
	- Notificações de Figura macro: é possível optar por incluir uma figura quando a notificação é expandida. Assegure-se de fornecer um texto do Título e uma URL para a figura.
	- Notificações de Texto grande: é possível optar por incluir texto adicional com um título. Assegure-se de que a mensagem de Texto grande e as informações de texto do Título sejam fornecidas.
	- Notificações de estilo da caixa de entrada: é possível enviar a notificação com o estilo definido como uma notificação de caixa de entrada. Forneça um texto do Título e a mensagem em Linhas.	 

## Configurações Opcionais do iOS 
{: #push_step_4_ios}

É possível customizar as configurações do {{site.data.keyword.mobilepushshort}} para enviar notificações para dispositivos iOS. As opções de customização opcionais a seguir são suportadas.

- **Badge**: indica o número que é exibido no badge do aplicativo. O valor padrão é zero (0) e isso não exibiria um badge. 
- **Som**: indica que um clique de som seja reproduzido no recebimento de uma notificação. Suporta o padrão ou o nome de um recurso de som empacotado no app.
- **Carga útil adicional**: especifica os valores de carga útil customizados para suas notificações.

Também é possível optar por ativar [notificações interativas](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#interactive-notifications) e [notificações de rich media](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enabling-rich-media-notifications).

## Monitoramento para entregar notificações 
{: #push_step_4_monitor}

O serviço {{site.data.keyword.mobilepushshort}} fornece um utilitário de monitoramento para ajudá-lo a verificar o status das mensagens que são enviadas. Para configurar o utilitário de monitoramento, passe por uma das opções a seguir:

- [Ativar monitoramento para aplicativos Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#monitoring).
- [Ativar monitoramento para aplicativos iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-monitoring).
