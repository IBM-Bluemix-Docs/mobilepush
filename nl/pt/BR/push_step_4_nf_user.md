---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# As notificações baseadas no usuário
{: #user_based_notifications}
Última atualização: 22 de maio de 2017
{: .last-updated}

{{site.data.keyword.mobilepushshort}} baseado no ID do usuário destina-se a usuários do app móvel com mensagens customizadas. Com
notificações baseadas no usuário, é possível escolher notificar indivíduos
específicos com base em suas preferências.

## Registrar dispositivo com ID do usuário
{: #register_device_wh_userid}

Para ativar notificações push destinadas por ID do usuário, assegure-se de registrar
o dispositivo com um campo ID do usuário configurado.     

O ID do usuário pode ser qualquer sequência que o aplicativo forneça para o API de registro de dispositivo. Normalmente, um aplicativo móvel primeiro executará um ciclo de autenticação no qual o usuário do app móvel é autenticado junto a um serviço de autenticação, tal como o [{{site.data.keyword.amafull}} ![Ícone de link externo](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/docs/services/mobileaccess/index.html){: new_window}. Na autenticação bem-sucedida, o ID de usuário autenticado então é passado para a API de
registro de dispositivo push. 

Para se registrar para notificação baseada em userId, passe por:

- [Registrando um aplicativo Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#register-for-notifications)
- [Registrando um aplicativo iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#register-for-notifications)
- [Registrando um aplicativo Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#register-for-notifications)
- [Registrando um aplicativo da web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#register-for-notifications)


## Usando notificações baseadas em userId
{: #using_userid}

As notificações baseadas em userId são mensagens de notificação destinadas a
um usuário específico. Muitos dispositivos podem ser
registrados com um usuário. As etapas a seguir descrevem como enviar notificações baseadas em ID do usuário.

1. No console de **Notificação push**, selecione a opção **Enviar notificações**.
1. Selecione **UserId** na lista de opções **Enviar para**.
1. No campo **ID do usuário**, procure o ID do usuário que deseja usar e, em seguida, clique em
**+Incluir**.![Tela de notificações](images/user_notification.jpg)
1. No campo **Mensagem**, insira o texto que você deseja enviar em sua notificação.
1. Clique em **Enviar**.


## Sincronizando o login e o logout do usuário 
{: #sync_login_logout}

É possível optar por enviar notificações somente se o usuário está conectado. 

Por exemplo, considere um dispositivo compartilhado por membros de uma equipe no trabalho e há a necessidade de abordar usuários específicos. Em
um caso de uso desse tipo, haveria uma sequência de login e logout do usuário. Esse
mecanismo de autenticação permite que o aplicativo rastreie a identidade do usuário
presente do aplicativo. Isso assegura que notificações destinadas a um usuário
específico sempre sejam recebidas por esse usuário somente. Após um login bem-sucedido,
chame a API de registro de dispositivo passando o ID do usuário conectado. Da mesma forma, antes de efetuar logout, chame a API `unregistration` do dispositivo. O
sequenciamento dessas APIs de Push com login e logout irá assegurar que as notificações destinadas a um usuário específico sejam enviadas somente para esse usuário.
