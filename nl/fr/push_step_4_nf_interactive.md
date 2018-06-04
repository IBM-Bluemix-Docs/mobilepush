---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifications interactives et silencieuses  
{: #interactive-notifications}
Dernière mise à jour : 22 mai 2017
{: .last-updated}

Les notifications interactives permettent aux utilisateurs de répondre à une notification sans ouvrir l'application. Lorsqu'une notification interactive est reçue, l'appareil affiche
les boutons d'action avec le message de notification. 

**Remarque :** les notifications interactives ne sont pas prises en charge sur les appareils iOS dont la version est antérieure à la version 8. 

## Envoi de notifications interactives
{: #send_interactive_notifications}

Une notification interactive peut être envoyée via la console Push Notifications ou en vous reportant à la documentation d'[API REST](push_restapi.html).


Depuis la console {{site.data.keyword.mobilepushshort}} : 

1. Sous l'onglet Notification, cliquez sur **Envoyer une notification**. 
2. Choisissez les destinataires de votre notification et cliquez sur **Suivant**. 
3. Dans la page de rédaction de la notification, une notification push interactive peut être envoyée en définissant Défaut ou Mixte comme type et en spécifiant la valeur Catégorie sous l'onglet Options avancées. 

## Traitement des notifications interactives 
{: #handle_interactive_notifications}

- Pour iOS, voir [Enable and handle interactive notifications on Swift applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications).
- Pour Cordova, voir [Enable and handle interactive notifications on Cordova applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications).
- Pour Android, voir [Enable and handle interactive notifications on Android applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications).


## Traitement des notifications silencieuses pour iOS
{: #send_silent_notifications_for_ios}

Les notifications silencieuses n'apparaissent pas sur l'écran de l'appareil et sont reçues par l'application en arrière-plan. Pour plus d'informations, voir [Silent Notifications on iOS devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification).
