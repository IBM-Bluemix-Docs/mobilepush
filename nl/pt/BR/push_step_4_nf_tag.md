---

copyright:
years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notificações baseadas em tag
{: #tag_based_notifications}
Última atualização: 30 de junho de 2017
{: .last-updated}

Notificações baseadas em tag são mensagens que se destinam a todos os dispositivos inscritos em uma tag específica. As notificações baseadas em identificação
permitem a segmentação de notificações com base em áreas ou tópicos de assunto. Os destinatários da notificação podem optar por receber notificações somente se for
sobre um assunto ou um tópico de interesse. Portanto, a notificação baseada em
identificação fornece um meio de segmentar destinatários. Esse recurso ativa
a capacidade de definir identificações e, em seguida, de enviar e receber mensagens por identificações. Uma mensagem é destinada somente para instâncias do aplicativo
cliente (no dispositivo móvel, navegador ou como um app ou extensões) que estão inscritas para a identificação. Deve-se primeiramente criar tags para o aplicativo, configurar as assinaturas da tag e, em seguida, iniciar as notificações baseadas em tag. Para enviar uma notificação baseada em tag que usa a API REST, assegure-se de que os "tagNames" sejam fornecidos ao postar no recurso de mensagem.

É possível definir tags e depois enviar e receber mensagens usando tags. Crie primeiro as tags para o aplicativo, crie assinaturas e, em seguida, inicie as notificações baseadas em tag. Para enviar uma
notificação baseada em tag usando a
[API
REST](https://mobile.{DomainName}/imfpush/){: new_window}, assegure-se de que os "tagNames" sejam fornecidos ao
postar no recurso de mensagem.


## Gerenciando Identificações
{: #manage_tags}

Use o console do {{site.data.keyword.mobilepushshort}} para criar e excluir tags de seu aplicativo e, em seguida, iniciar as notificações baseadas em tag. A notificação
baseada em tag é recebida nos dispositivos inscritos nas tags.


### Criando marcações
{: #create_tags}

Notificações baseadas em tag são mensagens que se destinam a todos os dispositivos inscritos em uma tag específica. Cada dispositivo pode se inscrever em
qualquer número de tags. 

1. No console do {{site.data.keyword.mobilepushshort}}, selecione a guia **Tags**.
1. Clique no botão + **Criar tag**.   
   1. No campo **Nome**, insira o nome da tag. Por exemplo, "coupons".
   1. No campo **Descrição**, insira uma descrição de tag.
   1. Clique em **Salvar**.

1. Na área **Fragmentos de códigos**,
selecione a plataforma para seu aplicativo móvel.
1. Modifique os fragmentos de códigos para manipular erros e
depois copie os fragmentos de códigos para cada tag em seu
aplicativo móvel.

### Excluindo marcações
{: #delete_tags}

1. Na guia **Tag**, selecione a tag que você deseja excluir e
clique no ícone **Excluir**.
1. Clique em **OK**.

Quando uma tag é excluída, as informações associadas a ela, incluindo seus assinantes e dispositivos, são excluídas. O
cancelamento de assinatura automático não é necessário, uma vez que a tag não
existe mais. Nenhuma ação posterior é necessária no lado do cliente.

### Editando uma descrição de tag
{: #edit_tags}

1. Na guia **Tag**, selecione a tag que deseja
editar.
1. Clique no ícone **Editar**.
1. Edite a descrição d tag e clique no botão
**Salvar**.

## Obter tags
{: #get_tags}

As tags fornecem uma maneira de enviar notificações destinadas a usuários com base
em seus interesses, ao contrário das transmissões em geral que são enviadas a todos os
aplicativos. É possível criar e gerenciar tags usando a guia Tags no console do {{site.data.keyword.mobilepushshort}} ou usar APIs de REST. É possível usar fragmentos de código para gerenciar e consultar as assinaturas de identificação de seu aplicativo
móvel. É possível usar os fragmentos de código para obter assinaturas, assinar uma tag, cancelar a assinatura de uma tag ou obter uma lista de tags disponíveis. Copie esses
fragmentos de código para seu aplicativo móvel.


- Para o Android, veja a API `getTags` e a API `getSubscriptions` em [Obter tags de Notificação push no Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

- Para o Cordova, veja a API `retrieveAvailableTags()` e a API `retrieveSubscriptions()` em [Obter tags de Notificações push no Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Para o iOS, veja a API `retrieveAvailableTagsWithCompletionHandler` em [Obter tags de Notificações push no Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags).

- Para navegadores da web, veja a API `retrieveAvailableTags()` em [Obter tags de Notificações push nos navegadores da web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).


## Assinar tags
{: #Subscribe_tags}

Use a API a seguir para permitir que seus dispositivos recuperem tags, assinem uma tag, recuperem assinaturas e cancelem a assinatura de uma tag.

- Para o Android, use as APIs `getTags`, `subscribe`, `getSubscriptions` e `unsubscribeFromTags`. Veja [Assinar tags de Notificações push para o Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags).

- Para o Cordova, use as APIS `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` e `unsubscribe()`. Veja [Assinar tags de Notificações push para o Cordova](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Para o iOS, use as APIs `retrieveAvailableTagsWithCompletionHandler`, `subscribeToTags`, `retrieveSubscriptionsWithCompletionHandler` e `unsubscribeFromTags`. Veja [Assinar tags de Notificações push para o Swift](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags).

- Para navegadores da web, use as APIs `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` e `unSubscribe()`. Veja [Assinar tags de Notificações push para navegadores da web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).

## Usando
notificações baseada em tag
{: #using_tags}

Notificações baseadas em tag são mensagens que se destinam a todos os dispositivos inscritos em uma tag específica. Cada dispositivo pode ser inscrito em qualquer número de tags. Este
tópico descreve como enviar notificações baseadas em tag. As assinaturas são mantidas pela instância do Bluemix do serviço {{site.data.keyword.mobilepushshort}}. Quando uma tag é excluída, todas as informações associadas a essa tag, incluindo seus assinantes e dispositivos, são excluídas. Nenhum cancelamento de
assinatura automático é necessário para essa tag, uma vez que ela não existe mais e
nenhuma ação adicional é necessária no lado do cliente.

Crie tags na tela **Tag**. Para obter informações sobre como
criar tags, consulte
[Criando tags](t_manage_tags.html).

1. No console de **Notificação push**, clique em **Enviar notificações**.
1. Selecione a opção **Dispositivo por identificação** na lista suspensa **Enviar para**.
1. Procure as tags que deseja usar e selecione-as.
![Tela de notificações](images/tag_notification.jpg)
1. No campo **Texto da mensagem**, insira o texto que seria enviado como uma notificação ao público inscrito.
1. Clique em **Enviar**.
