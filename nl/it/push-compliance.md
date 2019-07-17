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

# Conformità
{: #compliance}

Il servizio IBM Cloud {{site.data.keyword.mobilepushshort}} fornisce un modo affidabile e sicuro per inviare le notifiche ai dispositivi mobili registrati.
{: shortdesc}

## HIPAA
{: #hipaa}

Il servizio IBM {{site.data.keyword.mobilepushshort}} soddisfa i controlli IBM richiesti che sono commisurati ai requisiti di sicurezza e regole sulla privacy di HIPAA (Health Insurance Portability and Accountability Act) del 1996. Il servizio {{site.data.keyword.mobilepushshort}} archivia i dati in formato crittografico quando sono inattivi e trasmette dati crittografati.

Se vuoi inviare informazioni regolamentate HIPAA utilizzando il servizio IBM Cloud {{site.data.keyword.mobilepushshort}} non dovresti utilizzare l'API Post/message, poiché il payload inviato attraverso provider Push di terze parti potrebbe non soddisfare le linee guida normative. Invece, puoi utilizzare la seguente procedura in cui viene inviato solo il messageId attraverso provider Push di terze parti, ma i dati sensibili reali vengono scaricati dall'applicazione client tramite un trasporto protetto (https).

1. Esegui il provisioning di una nuova istanza del piano Avanzato o esegui l'upgrade della tua istanza esistente a un piano Avanzato.
2. Invia una [notifica silenziosa](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios) utilizzando il servizio {{site.data.keyword.mobilepushshort}}.
3. Il servizio {{site.data.keyword.mobilepushshort}} invia la notifica utilizzando dei provider cloud Push come FCM, APNS. In base alle proprie caratteristiche, l'avviso di notifica silenzioso non viene inviato come parte della notifica.
4. Dopo che il dispositivo riceve una notifica con ``message id`` / ``nid`` trasmessi, l'applicazione effettua una chiamata al servizio {{site.data.keyword.mobilepushshort}} per ricevere l'avviso di notifica tramite ``GET /message/{messageId}``.

Questo è utile per realizzare la trasmissione di contenuto di testo sensibile attraverso un canale sicuro utilizzando il servizio IBM Cloud {{site.data.keyword.mobilepushshort}}.

IBM non ha una relazione BAA (Business Associate Agreements) con APNS/FCM.
{: note}
## ISO (International Organization for Standardization)
{: #iso}

Il servizio {{site.data.keyword.mobilepushshort}} è controllato da una società di sicurezza di terze parti e rispetta
i seguenti requisiti ISO:

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [Ricerca su tutti i certificati IBM ISO ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}.
 
## Certificazione SOC 2 Type 1
{: #soccert}

{{site.data.keyword.IBM_notm}} fornisce un report SOC (Service Organization Controls) 2 Type 1
per il servizio {{site.data.keyword.mobilepushshort}}. I report valutano i controlli operativi di IBM in base ai criteri
stabiliti dai Trust Services Principles dell'AICPA (American Institute of Certified Public Accountants).
I Trust Services Principles definiscono i sistemi di controllo adeguati e stabiliscono gli standard di settore
per i provider di servizi come IBM Cloud per salvaguardare le informazioni e i dati dei propri clienti.

Puoi richiedere un report SOC 2 Type 1 dal portale clienti o contattare il tuo rappresentante delle vendite. In alternativa, puoi aprire un ticket di supporto con
[IBM Cloud support ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/support){: new_window}.

## Regolamento generale sulla protezione dei dati (GDPR, General Data Protection Regulation) 
{: #gdpr}

Il GDPR cerca di creare un quadro normativo armonizzato in materia di protezione dei dati in tutta l'Unione Europea e mira a restituire ai cittadini il controllo dei propri dati personali, imponendo nel contempo regole rigide a coloro che ospitano ed ‘elaborano’ questi dati, in qualsiasi parte del mondo. Il Regolamento introduce anche regole inerenti la libera circolazione di dati personali all'interno e all'esterno dell'UE. 

Con il [General Data Protection Regulation ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.eugdpr.org/){: new_window}, i clienti del servizio {{site.data.keyword.mobilepushshort}} possono fare affidamento
sulla conoscenza e sulla conformità del team del servizio {{site.data.keyword.mobilepushshort}} con normative e standard di privacy dei dati emergenti ma anche nella più ampia capacità di {{site.data.keyword.IBM}} di fornire una suite completa di soluzioni per assistere le aziende di ogni dimensione con i propri requisiti di governance dei dati interni.
