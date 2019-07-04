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

# Conformité
{: #compliance}

Le service IBM Cloud {{site.data.keyword.mobilepushshort}} offre une possibilité fiable et sécurisée d'envoi de notifications à des appareils mobiles enregistrés.
{: shortdesc}

## Loi HIPAA
{: #hipaa}

Le service IBM {{site.data.keyword.mobilepushshort}} répond aux exigences en matière de contrôles d'IBM, qui s'appuient sur la loi américaine relative à la portabilité et la responsabilité en assurance santé (HIPAA, Health Insurance Portability and Accountability Act) de 1996 et sur les exigences en matière de sécurité et de confidentialité. Le service {{site.data.keyword.mobilepushshort}} stocke les données sous un format chiffré au repos et transmet les données chiffrées.

Si vous voulez envoyer à l'aide du service IBM Cloud {{site.data.keyword.mobilepushshort}} des informations régies par la loi HIPAA, vous ne devez pas utiliser d'API de message POST, car il est possible que le contenu envoyé par le biais de fournisseurs d'envoi tiers ne respecte pas les directives de réglementation. Sinon, vous pouvez procéder comme suit lorsque seul l'ID message est envoyé par le biais de fournisseurs d'envoi tiers, mais que les données sensibles effectives sont téléchargées par l'application client via un transport sécurisé (https).

1. Mettez à disposition un nouveau plan avancé d'instance ou procédez à une mise à niveau de votre instance existante vers un plan avancé.
2. Envoyez une [notification silencieuse](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios) à l'aide du service {{site.data.keyword.mobilepushshort}}.
3. Le service {{site.data.keyword.mobilepushshort}} envoie la notification en utilisant des fournisseurs d'envoi de cloud tels que FCM et APNS. Compte tenu des caractéristiques de la notification silencieuse, aucune alerte n'est envoyée dans le cadre de la notification.
4. Une fois que l'appareil a reçu la notification avec l'``ID message`` / ``nid`` transmis, l'application lance un appel au service {{site.data.keyword.mobilepushshort}} afin de recevoir l'alerte de notification par le biais de ``GET /message/{ID message}``.

Cette procédure contribue à transmettre du contenu textuel sensible via un canal sécurisé à l'ide du service IBM Cloud {{site.data.keyword.mobilepushshort}}.

IBM n'a pas de relation d'accords Business Associate Agreements (BAA) avec APNS/FCM.
{: note}
## Organisation internationale de normalisation (ISO)
{: #iso}

Le service {{site.data.keyword.mobilepushshort}} fait l'objet d'un audit par une firme indépendante et répond aux exigences
ISO suivantes :

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [Search all IBM ISO certificates ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}.
 
## Certification SOC 2 Type 1
{: #soccert}

{{site.data.keyword.IBM_notm}} fournit des rapports SOC (Service Organization Controls) 2 Type 1 pour le
service {{site.data.keyword.mobilepushshort}}. Ces rapports évaluent les contrôles opérationnels d'IBM selon des critères définis par les principes Trust Services Principles de l'AICPA (American Institute of Certified Public Accountants).
Ces derniers définissent les systèmes de contrôle adéquats et établissent les normes de l'industrie pour les fournisseurs de service, tels qu'IBM Cloud, afin de protéger les données et les informations de leurs clients.

Vous pouvez demander un rapport SOC 2 Type 1 depuis le portail client ou à votre ingénieur commercial. Vous pouvez également ouvrir un ticket de demande de service auprès du [support IBM Cloud![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/support){: new_window}.

## Règlement général sur la protection des données (RGPD) 
{: #gdpr}

Le GDPR a pour but de créer un cadre juridique harmonisé pour la protection des données dans l'Union européenne et vise à redonner aux citoyens un contrôle sur leurs données personnelles, tout en imposant des règles strictes à tous ceux qui hébergent et traitent ces données, partout dans le monde. Ce règlement introduit également des règles en matière de libre circulation des données personnelles au sein et en dehors de l'UE. 

Avec le [règlement général sur la protection des données![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") les clients du service ](https://www.eugdpr.org/){: new_window}, {{site.data.keyword.mobilepushshort}} peuvent compter sur les connaissances et la conformité de l'équipe du service {{site.data.keyword.mobilepushshort}} en matière de législation et de normes de confidentialité des données et sur la capacité accrue d'{{site.data.keyword.IBM}} à fournir une gamme complète de solutions visant à aider les entreprises de toutes tailles concernant leurs exigences internes en matière de gouvernance des données.
