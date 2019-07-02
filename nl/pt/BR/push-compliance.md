---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-24"

keywords: push notifications, notifications, compliance, hipaa, iso, soc 2 type 1 certification, gdpr

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Conformidade
{: #compliance}

O IBM Cloud {{site.data.keyword.mobilepushshort}} Service fornece uma maneira confiável e segura de enviar notificações para os dispositivos móveis registrados.
{: shortdesc}

## HIPAA
{: #hipaa}

O IBM {{site.data.keyword.mobilepushshort}} Service atende aos IBM Controls necessários que são proporcionais aos requisitos do Health Insurance Portability and Accountability Act de 1996 (HIPAA) Security and Privacy Rule. O Serviço do {{site.data.keyword.mobilepushshort}} armazena os dados em formato criptografado em repouso e transmite os dados criptografados.

Se você desejar enviar informações reguladas de HIPAA usando o IBM Cloud {{site.data.keyword.mobilepushshort}} Service, você não deverá estar usando a API de Pós-mensagem, uma vez que a carga útil enviada em provedores Push de terceiro pode não atender às diretrizes regulamentares. Em vez disso, é possível usar as etapas a seguir no local em que apenas messageId é enviado nos provedores Push de terceiro, mas os dados sensíveis reais são transferidos por download pelo aplicativo cliente em um transporte seguro (https).

1. Provisione um Plano avançado de nova instância ou atualize a sua instância existente para um Plano avançado.
2. Envie uma [notificação silenciosa](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios) usando o {{site.data.keyword.mobilepushshort}} Service.
3. O {{site.data.keyword.mobilepushshort}} Service envia a notificação usando os provedores de nuvem push como FCM, APNS. Pelas características da notificação silenciosa o alerta não é enviado como parte da notificação.
4. Assim que o dispositivo recebe notificação com o ``message id`` / ``nid`` transmitido, o aplicativo faz uma chamada para o {{site.data.keyword.mobilepushshort}} Service para receber o alerta de notificação usando o ``GET /message/{messageId}``.

Isso ajuda a alcançar a transmissão de conteúdo de texto sensível em um canal seguro usando o IBM Cloud {{site.data.keyword.mobilepushshort}} Service.

A IBM não tem uma relação de Acordos de associação de negócios (BAA) com o APNS/FCM.
{: note}
## International Organization for Standardization (ISO)
{: #iso}

O {{site.data.keyword.mobilepushshort}} Service é auditado por uma empresa de segurança de terceiro
e atende aos requisitos ISO a seguir:

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [Procure todos os certificados ISO da IBM![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}.
 
## Certificação Tipo 1 do SOC 2
{: #soccert}

O {{site.data.keyword.IBM_notm}} fornece um relatório de Tipo 1 do Service Organization Controls (SOC) 2
para o {{site.data.keyword.mobilepushshort}} Service. Os relatórios avaliam os controles operacionais da IBM de acordo com os critérios configurados
pelos Princípios de Serviços de Confiança do American Institute of Certified Public Accountants (AICPA). 
Os Princípios de Serviços de Confiança definem sistemas de controle adequados e estabelecem padrões de mercado
para provedores de serviços, como o IBM Cloud, para proteger os dados de seus clientes e as informações.

É possível solicitar um relatório de Tipo 1 do SOC 2 por meio do portal do cliente ou entrar em contato com o seu representante de vendas. Alternativamente, é possível abrir um chamado de suporte com
o suporte do [IBM Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/support){: new_window}.

## Regulamento Geral sobre a Proteção de Dados (GDPR) 
{: #gdpr}

O GDPR busca criar uma estrutura de lei de proteção de dados harmonizada em toda a UE e visa retornar aos cidadãos o controle de seus dados pessoais, enquanto impõe regras rígidas sobre aqueles que hospedam e 'processam' esses dados, em qualquer lugar do mundo. O regulamento também introduz regras relativas à livre circulação de dados pessoais dentro e fora da UE. 

Com o [Regulamento geral de proteção de dados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.eugdpr.org/){: new_window}, os clientes do {{site.data.keyword.mobilepushshort}} Service podem contar com
o entendimento e a conformidade da equipe do {{site.data.keyword.mobilepushshort}} Service com padrões de privacidade de dados emergentes e a legislação e também com a capacidade mais ampla da {{site.data.keyword.IBM}} em fornecer um conjunto abrangente de soluções para ajudar as empresas de todos os tamanhos com os seus próprios requisitos internos de governança de dados.
