---

copyright:
  years:  2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, service access, manage, user roles

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Gerenciando o acesso de serviço
{: #service-access-management}

Com o {{site.data.keyword.mobilepushshort}} e o {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) os proprietários da conta podem gerenciar o acesso de usuário em sua conta.
{: shortdesc}

Como um proprietário da conta, é possível configurar políticas dentro de sua conta para criar diferentes níveis de acesso para diferentes usuários. Por exemplo, alguns usuários podem ter acesso **Somente leitura** para uma instância, mas acesso de **Gravação** para outra. É possível decidir quem tem permissão para criar, atualizar e excluir instâncias do {{site.data.keyword.mobilepushshort}}.

**Nota:** como o serviço do {{site.data.keyword.mobilepushshort}} adotou o IAM, o segredo do App não será gerado para as novas instâncias. Em vez disso, deve-se usar as [chaves de API](https://cloud.ibm.com/docs/iam?topic=iam-manapikey).

## Funções dos usuários
{: #roles}

O escopo de uma política de acesso é baseado na função designada a um usuário.
{: shortdesc}

As políticas permitem que o acesso seja concedido em diferentes níveis. Algumas das opções incluem:
<ul><ul>
  <li>Acesso em todas as instâncias do serviço em sua conta</li>
  <li>Acesso a uma instância de serviço individual em sua conta</li>
  <li>Acesso a um recurso específico dentro de uma instância</li>
  <li>Acesso a todos os serviços ativados pelo IAM em sua conta</li>
</ul></ul>

As funções de gerenciamento de plataforma permitem que os usuários executem tarefas em recursos de serviço no nível de plataforma. Por exemplo, as funções podem ser designadas para determinar quem pode criar ou excluir IDs, criar instâncias e ligar instâncias a apps. A tabela a seguir detalha as ações da forma que se correlacionem às funções de gerenciamento de plataforma.

<table>
  <tr>
    <th>Função da plataforma</th>
    <th>Permissões</th>
    <th>Ações de exemplo</th>
  </tr>
  <tr>
    <td><i>Visualizador</i></td>
    <td>Visualize instâncias do {{site.data.keyword.mobilepushshort}}.</td>
    <td>É possível ver os dados de um usuário do Diretório da nuvem ou a configuração do provedor de identidade.</td>
  </tr>
  <tr>
    <td><i>Editor
</i></td>
    <td>Visualize e ligue instâncias do {{site.data.keyword.mobilepushshort}}.</td>
    <td>É possível ligar aplicativos a uma instância do {{site.data.keyword.mobilepushshort}}.</td>
  </tr>
  <tr>
    <td><i>Operador</i></td>
    <td>Crie, exclua, edite, suspenda, continue, visualize ou ligue instâncias do {{site.data.keyword.mobilepushshort}}.</td>
    <td>É possível criar ou excluir uma instância do {{site.data.keyword.mobilepushshort}} por meio do catálogo.</td>
  </tr>
  <tr>
    <td><i>Administrador</i></td>
    <td>Todas as ações de gerenciamento para todos os serviços na conta.</td>
    <td>É possível executar todas as ações do operador e a capacidade de designar políticas para outros usuários.</td>
  </tr>
</table>

</br>
</br>
A tabela a seguir detalha as ações que são mapeadas para as funções de acesso de serviço. As funções de acesso de serviço permitem que os usuários acessem o {{site.data.keyword.mobilepushshort}} bem como a capacidade de chamar a API do {{site.data.keyword.mobilepushshort}}.


<table>
  <tr>
    <th>Função de serviço</th>
    <th>Permissões</th>
    <th>Ações de exemplo</th>
  </tr>
  <tr>
    <td><i>Leitor</i></td>
    <td>Visualize dados de instância do {{site.data.keyword.mobilepushshort}}.</td>
    <td>Pode visualizar os detalhes da instância de serviço, como dados do usuário ou informações do provedor de identidade.</td>
  </tr>
  <tr>
    <td> <i>Gravador ou gerenciador</i></td>
    <td>Visualize e mude uma instância do {{site.data.keyword.mobilepushshort}}.</td>
    <td>Pode executar todas as ações do Leitor e editar a instância de serviço, como editar a configuração do provedor de identidade. </li></ul></td>
  </tr>
</table>

Para obter mais informações sobre como designar funções de usuário na IU, veja [Gerenciando o acesso ao IAM](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser).


## Políticas de acesso do {{site.data.keyword.mobilepushshort}}
{: #access}

Cada usuário que acessa o serviço do {{site.data.keyword.mobilepushshort}} em sua conta deve ter uma política de acesso designada com uma função de usuário do IAM definida. Essa política determina quais ações o usuário pode executar dentro do contexto do serviço ou instância que você seleciona.
{: shortdesc}

As ações são customizadas e definidas pelo serviço {{site.data.keyword.Bluemix_notm}} como operações que podem ser executadas no serviço. As ações são, então, mapeadas para funções de usuário do IAM. É possível controlar algumas das ações tomadas com o serviço {{site.data.keyword.cloudaccesstrailshort}}. Na tabela a seguir, as ações e as permissões necessárias para o {{site.data.keyword.mobilepushshort}} são mapeadas.

|Ação |Explicação |Função necessária |
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |Obter configurações do app |Gerenciador, gravador, leitor|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |Excluir configurações do app |de Domínio|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |Atualizar configurações do app |de Domínio|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |Obter dispositivos |Gerenciador, gravador, leitor|
|`POST /imfpush/v1/apps/{applicationId}/devices` |Registrar dispositivo |Gerenciador, gravador|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Atualizar dispositivo |Gerenciador, gravador|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Excluir dispositivo |de Domínio|
|`POST /imfpush/v1/apps/{applicationId}/messages` |Enviar mensagens |Gerenciador, gravador|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |Enviar mensagens em massa |Gerenciador, gravador|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |Exclui uma mensagem |de Domínio|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |Receber mensagens |Gerenciador, Leitor, Gravador|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |Atualizar status de entrega de mensagem|Gerenciador, gravador|
|`POST /imfpush/v1/apps/{applicationId}/tags` |Criar tags |Gerenciador, gravador|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Atualizar tag   |Gerenciador, gravador|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Excluir marcação   |de Domínio|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |Obter tags |Gerenciador, Leitor, Gravador|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |Criar Assinaturas |Gerenciador, gravador|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |Excluir assinaturas |de Domínio|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |Obter Assinaturas |Gerenciador, Leitor, Gravador|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |Criar webhook |Gerenciador, gravador|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Atualizar webhook |Gerenciador, gravador|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Excluir webhook |de Domínio|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |Obter webhook |Gerenciador, Leitor, Gravador|-|

## Trabalhando com chaves API
{: #apikeys}

Ao criar credenciais de serviço, é possível notar que uma apiKey é exibida em vez do appSecret.

Para usar quaisquer APIs de REST, deve-se gerar o token de acesso usando o comando curl a seguir:

### Paramêtros

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### Response

```
{
    "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```

Ao gerar o token de acesso usando o comando curl anterior, agora é possível operar as APIs de REST passando o ‘valor do Bearer do access_token>’ no cabeçalho de Autorização

Por exemplo:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

Para obter mais informações sobre o IAM, veja [Acesso IAM](https://cloud.ibm.com/docs/iam?topic=iam-userroles).
