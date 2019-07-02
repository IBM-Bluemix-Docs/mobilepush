---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Eventos do Activity Tracker
{: #push_activity_tracker}

O serviço do {{site.data.keyword.cloudaccesstrailfull}} monitora a interação de um usuário com os serviços do IBM Cloud. É possível procurar e analisar como os seus usuários e aplicativos interagem com os serviços do IBM Cloud.

Administradores de nuvem, segurança e desenvolvedores podem:

<dl>
	<dt>Obtenha insights em seu ambiente para monitorar e investigar as violações de segurança</dt>
	<dd>Capture interações de usuários e aplicativos com seus recursos provisionados do IBM Cloud. Investigue possíveis violações de segurança ou acesso não autorizado.</dd>
	<dt>Conquiste suas necessidades de regulamentação, conformidade e retenção de registro</dt>
	<dd>Armazene eventos capturados pelo tempo necessário, com proteção nas soluções de armazenamento da classe econômica da nuvem. Consulte os dados do evento coletados por meio da API ou exporte os seus dados de atividade de nuvem.</dd>
	<dt>Transparência do Cloud para as suas equipes do DevOps depurarem e executarem o planejamento da capacidade</dt>
	<dd>Os eventos de atividade na nuvem fornecem transparência em suas operações de TI no IBM Cloud. Identifique quando e como seus serviços de nuvem são usados para isolar e depurar seus aplicativos. Consulte os dados coletados ao longo do tempo para antecipar o crescimento da sua nuvem e as suas necessidades sazonais.</dd>
	<dt>Simplifique a coleta e melhore sua segurança na nuvem</dt>
	<dd>O {{site.data.keyword.cloudaccesstrailshort}} captura automaticamente os seus eventos do IBM Cloud.</dd>
</dl>


Os logs de atividades do {{site.data.keyword.cloudaccesstrailshort}} podem ser usados para identificar as informações a seguir:

- Os usuários que fizeram chamadas API para serviços de nuvem.
- O endereço IP de origem a partir do qual as chamadas API foram feitas.
- O registro de data e hora de quando as chamadas API foram feitas.
- O status da chamada API.

## Lista de Eventos
{: #actions}

A tabela a seguir lista os eventos do {{site.data.keyword.cloudaccesstrailshort}} para o {{site.data.keyword.mobilepushshort}}
<table>
  <caption>Tabela 1. Lista de ações que geram um evento</caption>
  <tr>
    <th>Ação</th>
	  <th>Novas Propriedades do Cliente - %s</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>Atualizações para o aplicativo</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>Exclusão de configuração de aplicativo</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>Atualização de configuração de aplicativo</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>Criação de tag</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>Exclusão de tag</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>Atualização de tag</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>Criação de webhook</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>Exclusão de webhook</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>Atualização de webhook</td>
  </tr>   
</table>


Para obter mais informações sobre como trabalhar com o {{site.data.keyword.cloudaccesstrailshort}}, consulte a [documentação aqui](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}.


Atualmente, os eventos do Activity Tracker estão disponíveis somente no `IBM Cloud - US South Region`.
{: note}
