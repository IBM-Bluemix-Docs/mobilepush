---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Notifiche interattive e automatiche  
{: #interactive-notifications}
Ultimo aggiornamento: 22 maggio 2017
{: .last-updated}

Le notifiche interattive consentono agli utenti di rispondere a una notifica senza aprire l'applicazione. Quando viene ricevuta una notifica, il dispositivo visualizza i pulsanti di azione insieme al messaggio di notifica. 

**Nota:** le notifiche interattive non sono supportate sui dispositivi iOS con versioni precedenti alla 8. 

## Invio di notifiche interattive
{: #send_interactive_notifications}

La notifica interattiva può essere inviata utilizzando la console Push Notifications o utilizzando la [Documentazione API REST](push_restapi.html).


Dalla console {{site.data.keyword.mobilepushshort}}: 

1. Nella scheda delle notifiche, fai clic su **Send Notification**. 
2. Scegli i tuoi destinatari per la notifica e fai clic su **Next**. 
3. Nella pagina di composizione della notifica, può essere inviato un push interattivo impostando il tipo su predefinito o misto e specificando il valore della categoria nella scheda del delle opzioni avanzate. 

## Gestione di notifiche interattive 
{: #handle_interactive_notifications}

- Per iOS, utilizza [Enable and handle interactive notifications on Swift applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#enable-interactive-push-notifications).
- Per Cordova, utilizza [Enable and handle interactive notifications on Cordova applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-push/tree/Doc#enable-interactive-push-notifications).
- Per Android, utilizza [Enable and handle interactive notifications on Android applications](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push/tree/Doc#enable-interactive-push-notifications).


## Gestione di notifiche automatiche per iOS
{: #send_silent_notifications_for_ios}

Le notifiche automatiche non vengono visualizzate sulla schermata del dispositivo e sono ricevute dall'applicazione in background. Per ulteriori informazioni, vedi [Silent Notifications on iOS devices](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/Doc#silent-notification).
