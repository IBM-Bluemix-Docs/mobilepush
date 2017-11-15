---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Tagbasierte Benachrichtigungen
{: #tag_based_notifications}
Letzte Aktualisierung: 30. Juni 2017
{: .last-updated}

Tagbasierte Benachrichtigungen sind Benachrichtigungen, die alle diejenigen Geräte zum Ziel haben, die einen bestimmten Tag subskribiert haben. Tagbasierte Benachrichtigungen ermöglichen die Segmentierung von Benachrichtigungen auf der Basis von Subjektbereichen oder Themen. Benachrichtigungsempfänger können wählen, dass sie Benachrichtigungen nur empfangen, wenn deren Inhalt ein Thema hat, das von Interesse ist. Daher bieten tagbasierte Benachrichtigungen die Möglichkeit, Empfänger zu segmentieren. Diese Funktion ermöglicht es, dass Tags definiert werden und anschließend Nachrichten geordnet nach Tags gesendet und empfangen werden. Eine Nachricht wird zielgruppenspezifisch nur an die Instanzen einer Clientanwendung (in Mobilgeräten, Browsern oder als App oder Erweiterungen) gesendet, die den Tag subskribiert haben. Sie müssen zunächst Tags für die Anwendung erstellen, die Tagsubskriptionen einrichten und anschließend die tagbasierten Benachrichtigungen starten. Zum Senden einer tagbasierten Benachrichtigung mithilfe der REST-API müssen Sie sicherstellen, dass während der Übergabe an die Ressource der Nachricht die Tagnamen ('tagNames') angegeben werden.

Sie können Tags definieren und anschließend mithilfe der Tags Nachrichten senden und empfangen. Sie müssen zuerst die Tags für die Anwendung erstellen, die Subskriptionen erstellen und anschließend die tagbasierten Benachrichtigungen starten. Zum Senden einer tagbasierten Benachrichtigung mithilfe der [REST-API](https://mobile.{DomainName}/imfpush/){: new_window} müssen Sie sicherstellen, dass bei der Übergabe an die Nachrichtenressource die Tagnamen ('tagNames') angegeben werden.


## Tags verwalten
{: #manage_tags}

Verwenden Sie die {{site.data.keyword.mobilepushshort}}-Konsole, um Tags für Ihre Anwendung zu erstellen und zu löschen und anschließend tagbasierte Benachrichtigungen zu initiieren. Die tagbasierte Benachrichtigung wird auf Geräten empfangen, von denen Tags subskribiert wurden.


### Tags erstellen
{: #create_tags}

Tagbasierte Benachrichtigungen sind Benachrichtigungen, die all diejenigen Geräte als Ziel haben, die einen bestimmten Tag subskribiert haben. Jedes Gerät kann beliebig viele Tags subskribieren. 

1. Wählen Sie in der {{site.data.keyword.mobilepushshort}}-Konsole die Registerkarte **Tags** aus.
1. Klicken Sie auf die Schaltfläche **Tag erstellen**.   
   1. Geben Sie in das Feld **Name** den Namen für den Tag ein. Beispiel: "Coupons".
   1. Geben Sie in das Feld **Beschreibung** eine Beschreibung für den Tag ein.
   1. Klicken Sie auf **Speichern**.

1. Wählen Sie im Bereich **Code-Snippets** die Plattform für Ihre mobile Anwendung aus.
1. Ändern Sie die Code-Snippets so, dass Fehler verarbeitet werden, und kopieren Sie anschließend die Code-Snippets für jeden Tag in Ihre mobile Anwendung.

### Tags löschen
{: #delete_tags}

1. Wählen Sie auf der Registerkarte **Tag** den Tag aus, den Sie löschen möchten, und klicken Sie auf das Symbol **Löschen**.
1. Klicken Sie auf **OK**.

Wenn ein Tag gelöscht wird, werden die Informationen diesem Tag zugeordneten Informationen (einschließlich Subskribenten und Geräte) gelöscht. Es ist erforderlich, die automatische Subskription aufzuheben, wenn der Tag nicht mehr vorhanden ist. Es ist keine weitere Aktion von der Clientseite erforderlich.

### Tagbeschreibung bearbeiten
{: #edit_tags}

1. Wählen Sie in der Registerkarte **Tag** den Tag aus, den Sie bearbeiten möchten.
1. Klicken Sie auf das Symbol **Bearbeiten**.
1. Bearbeiten Sie die Tagbeschreibung und klicken Sie anschließend auf die Schaltfläche **Speichern**.

## Tabs abrufen
{: #get_tags}

Mit Tags können im Gegensatz zu allgemeinen Rundsendungen, die an alle Anwendungen gesendet werden, Benachrichtigungen auf der Grundlage eines Interessenbereichs zielgruppenspezifisch an Benutzer gesendet werden. Sie können Tags erstellen und verwalten, indem Sie die Registerkarte 'Tags' in der {{site.data.keyword.mobilepushshort}}-Konsole oder REST-APIs verwenden. Sie können Code-Snippets verwenden, um Ihre Tag-Subskriptionen für Ihre mobile Anwendung zu verwalten und abzufragen. Sie können die Code-Snippets verwenden, um Subskriptionen abzurufen, eine Subskription für einen Tag einzurichten, eine Subskription für einen Tag aufzuheben oder eine Liste der verfügbaren Tags abzurufen. Kopieren Sie diese Code-Snippets in Ihre mobile Anwendung.


- Android: Siehe Abschnitte zur API `getTags` und zur API `getSubscriptions` in [Push Notifications: Tags abrufen (Android)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#ios-app).

- Cordova: Siehe Abschnitte zur API `retrieveAvailableTags()` und zur API `retrieveSubscriptions()` in [Push Notifications: Tags abrufen (Cordova)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- iOS: Siehe Abschnitt zur API `retrieveAvailableTagsWithCompletionHandler` in [Push Notifications: Tags abrufen (Swift)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#retrieve-tags).

- Web-Browser: Siehe Abschnitt zur API `retrieveAvailableTags()` in [Push Notifications: Tags abrufen (Web-Browser)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).


## Tags subskribieren
{: #Subscribe_tags}

Verwenden Sie die folgende API, um Ihren Geräten das Abrufen von Tags, das Subskribieren von Tags, das Abrufen von Subskriptionenund das Aufheben der Subskription von Tags zu ermöglichen.

- Verwenden Sie für Android die APIs `getTags`, `subscribe`, `getSubscriptions` und `unsubscribeFromTags`. Siehe [Push Notifications: Tags subskribieren (Android)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#push-notification-service-tags).

- Verwenden Sie für Cordova die APIs `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` und `unsubscribe()`. Siehe [Push Notifications: Tags subskribieren (Cordova)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#push-notification-service-tags).

- Verwenden Sie für iOS die APIs `retrieveAvailableTagsWithCompletionHandler`, `subscribeToTags`, `retrieveSubscriptionsWithCompletionHandler` und `unsubscribeFromTags`. Siehe [Push Notifications: Tags subskribieren (Swift)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#push-notification-service-tags).

- Verwenden Sie für Web-Browser die APIs `retrieveAvailableTags()`, `subscribe()`, `retrieveSubscriptions()` und `unSubscribe()`. Siehe [Push Notifications: Tags subskribieren (Web-Browser)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-javascript-webpush/blob/Doc/README.md#push-notification-service-tags).

## Tagbasierte Benachrichtigungen verwenden
{: #using_tags}

Tagbasierte Benachrichtigungen sind Benachrichtigungen, die alle diejenigen Geräte zum Ziel haben, die einen bestimmten Tag subskribiert haben. Jedes Gerät kann beliebig viele Tags subskribieren. Dieses Thema beschreibt, wie tagbasierte Benachrichtigungen gesendet werden. Subskriptionen werden von der Bluemix-Instanz des {{site.data.keyword.mobilepushshort}}-Service verwaltet. Wenn ein Tag gelöscht wird, werden alle diesem Tag zugeordneten Informationen (einschließlich Subskribenten und Geräte) gelöscht. Für diesen Tag ist keine automatische Aufhebung der Subskription erforderlich, da er nicht mehr vorhanden ist und daher clientseitig keine weiteren Aktionen nötig sind.

Erstellen Sie Tags in der Anzeige **Tag**. Informationen zum Erstellen von Tags finden Sie in [Tags erstellen](t_manage_tags.html).

1. Klicken Sie in der **Push Notifications**-Konsole auf **Benachrichtigungen senden**.
1. Wählen Sie in der Dropdown-Liste **Senden an** die Option **Gerät nach Tag** aus.
1. Suchen Sie nach den Tags, die Sie verwenden möchten, und wählen Sie sie aus. ![Anzeige 'Benachrichtigungen'](images/tag_notification.jpg)
1. Geben Sie im Feld **Nachrichtentext** den Text ein, der als Benachrichtigung an die subskribierte Benutzergruppe gesendet werden soll.
1. Klicken Sie auf **Senden**.
