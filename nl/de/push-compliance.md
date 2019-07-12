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

# Compliance
{: #compliance}

IBM Cloud {{site.data.keyword.mobilepushshort}} Service bietet eine vertrauenswürdige und sichere Möglichkeit zum Senden von Benachrichtigungen an die registrierten mobilen Geräte.
{: shortdesc}

## HIPAA
{: #hipaa}

Der IBM Service {{site.data.keyword.mobilepushshort}} erfüllt die Anforderungen der erforderlichen IBM Kontrollmechanismen, die den Anforderungen der Regeln für Sicherheit und Datenschutz des Health Insurance Portability and Accountability Act von 1996 (HIPAA) entsprechen. Der {{site.data.keyword.mobilepushshort}}-Service speichert die ruhenden Daten in einem verschlüsselten Format und überträgt die Daten verschlüsselt.

Wenn Sie über den IBM Cloud-Service {{site.data.keyword.mobilepushshort}} durch den HIPAA regulierte Informationen senden möchten, sollten Sie keine postMessage-API verwenden, da die über Push-Provider anderer Anbieter gesendeten Nutzdaten möglicherweise nicht den gesetzlichen Bestimmungen entsprechen. Stattdessen können Sie die folgenden Schritte ausführen, bei denen nur die Nachrichten-ID über Push-Provider anderer Anbieter gesendet wird, während die tatsächlichen sensiblen Daten von der Clientanwendung über ein sicheres HTTPS-Transportprotokoll heruntergeladen werden.

1. Stellen Sie eine neue Instanz des erweiterten Plans bereit oder führen Sie ein Upgrade auf einen erweiterten Plan für Ihre vorhandene Instanz durch.
2. Senden Sie eine [Hintergrundbenachrichtigung](/docs/services/mobilepush?topic=mobile-pushnotification-interactive-notifications#send_silent_notifications_for_ios) über den {{site.data.keyword.mobilepushshort}}-Service.
3. Der {{site.data.keyword.mobilepushshort}}-Service sendet die Benachrichtigung mithilfe von Push-Cloud-Providern wie z. B. FCM und APNS. Entsprechend den Merkmalen der Hintergrundbenachrichtigung wird der Alert nicht als Teil der Benachrichtigung gesendet.
4. Nachdem das Gerät eine Benachrichtigung mit der übertragenen ``Nachrichten-ID`` / ``NID`` empfangen hat, ruft die Anwendung den {{site.data.keyword.mobilepushshort}}-Service mithilfe von ``GET /message/{messageId}`` zum Empfangen des Benachrichtigungsalerts auf.

Dadurch wird die Übertragung sensibler Textinhalte über einen geschützten Kanal über den IBM Cloud-Service {{site.data.keyword.mobilepushshort}} erreicht.

IBM hat keine BAA-Beziehung (Business Associate Agreement) mit APNS/FCM.
{: note}
## International Organization for Standardization (ISO)
{: #iso}

Der {{site.data.keyword.mobilepushshort}}-Service wird von einer dritten Sicherheitsfirma geprüft und erfüllt die folgenden ISO- Anforderungen:

* [{{site.data.keyword.cloud_notm}} ISO 27001 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")]](https://www-935.ibm.com/services/multimedia/saas_27k.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27017 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")]](https://www-935.ibm.com/services/us/en/it-services/pdf/ibmcloud_27017.pdf){: new_window}
* [{{site.data.keyword.cloud_notm}} ISO 27018 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")]](https://www-935.ibm.com/services/multimedia/ibmcloud_27018.pdf){: new_window}
* [Alle IBM ISO-Zertifikate durchsuchen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www-935.ibm.com/services/us/en/it-services/iso-management-system-certifications.html){: new_window}.
 
## SOC 2-Zertifizierung von Typ 1
{: #soccert}

{{site.data.keyword.IBM_notm}} stellt einen SOC 2-Bericht von Typ 1 (SOC - Service Organization Controls) für den {{site.data.keyword.mobilepushshort}}-Service bereit. Die Berichte werten die IBM Betriebskontrollen entsprechend den Kriterien aus, die durch die Trust Services Principles des American Institute of Certified Public Accountants (AICPA) festgelegt sind.
Die Trust Services Principles definieren angemessene Kontrollsysteme und legen Branchenstandards für Service-Provider, wie z. B. IBM Cloud, fest, um die Daten und Informationen ihrer Kunden abzusichern.


Sie können einen SOC 2-Bericht von Typ 1 vom Kundenportal anfordern oder sich an Ihren Vertriebsbeauftragten wenden. Alternativ dazu können Sie ein Support-Ticket beim
[IBM Cloud-Support ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/support){: new_window} öffnen.

## Datenschutz-Grundverordnung (DSGVO) 
{: #gdpr}

Mit der DSGVO soll in der gesamten EU ein harmonisierter Rechtsrahmen für den Datenschutz geschaffen werden, in dem Bürger wieder die Kontrolle über ihre personenbezogenen Daten übernehmen, während gleichzeitig denen, die diese Daten an einem beliebigen Standort weltweit hosten und "verarbeiten" strikte Regeln auferlegt werden. Die Verordnung führt zudem Regeln in Bezug auf den freien Datenverkehr innerhalb und außerhalb der EU ein. 

Aufgrund der [Datenschutz-Grundverordnung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.eugdpr.org/){: new_window} können sich Kunden, die den {{site.data.keyword.mobilepushshort}}-Service verwenden, darauf verlassen, dass das {{site.data.keyword.mobilepushshort}}-Service-Team die neuen Datenschutzstandards kennt und einhält und dass {{site.data.keyword.IBM}} eine noch umfassende Suite von Lösungen bereitstellen kann, um Unternehmen jeglicher Größe beim Erfüllen der Anforderungen ihrer internen Datengovernance zu unterstützen.
