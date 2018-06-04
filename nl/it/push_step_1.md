
---

copyright:
 years: 2015, 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Passo 2: ottieni le tue credenziali del provider della notifica
{: #push_step_1}
Ultimo aggiornamento: 27 giugno 2017
{: .last-updated}

Per configurare il servizio {{site.data.keyword.mobilepushshort}}, devi ottenere le credenziali dal provider di notifica di push. 

## Per Android
{: #push_step_1_android}

FCM (Firebase Cloud Messaging) è il gateway utilizzato per consegnare le notifiche di push ai dispositivi Android e al browser Google Chrome e alle estensioni e applicazioni Chrome. Per configurare il servizio {{site.data.keyword.mobilepushshort}} sulla console, devi ottenere le tue credenziali FCM (ID mittente e chiave API). 

La chiave API è archiviata in modo protetto e utilizzata dal servizio {{site.data.keyword.mobilepushshort}} per stabilire una connessione al server FCM e l'ID mittente (numero progetto) viene utilizzato dall'SDK Android e dall'SDK JS per Google Chrome e Mozilla Firefox sul lato client. 

Per configurare FCM e ottenere le tue credenziali, completa le seguenti istruzioni:

1. Visita il sito [Console Firebase ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.firebase.google.com/?pli=1){: new_window}. È obbligatorio un account utente Google. 
2. Seleziona **Aggiungi progetto**. 
3. Nella finestra Crea un progetto, fornisci un nome progetto, scegli una regione/paese e fai clic su **Crea progetto**.
3. Nel pannello di navigazione, seleziona **Impostazioni** > **Impostazioni progetto**.
4. Scegli la scheda Cloud Messaging per ottenere le tue credenziali del progetto - la chiave API server e un ID mittente. Tieni presente che la chiave server elencata in FCM è uguale alla chiave API server.
   
	![Ottenimento delle credenziali per FCM](images/FCM_settings_2.jpg)

Potresti anche aver bisogno di generare il file `google-services.json`. Completa la seguente procedura:

1. Nella console Firebase, fai clic sull'icona **Impostazioni progetto**.
    
	![Impostazioni progetto Firebase](images/FCM_settings_6.jpg)

3. Seleziona **AGGIUNGI APPLICAZIONE** o l'icona **Aggiungi Firebase alla tua applicazione Android** dalla scheda Generale nel pannello Tue applicazioni.
    
4. Nella finestra Aggiungi Firebase alla tua applicazione Android, aggiungi prima **com.ibm.mobilefirstplatform.clientsdk.android.push** come nome pacchetto. Il campo Nome alternativo applicazione è facoltativo. Fai clic su **REGISTRA APPLICAZIONE**. 
    
	![Aggiunta di Firebase alla tua finestra Android](images/FCM_1.jpg)

5. Ora, includi il nome pacchetto della tua applicazione immettendolo nella finestra Aggiungi Firebase alla tua applicazione Android. Il campo Nome alternativo applicazione è facoltativo. Fai clic su **REGISTRA APPLICAZIONE**.  Il seguente è un esempio -

	![Aggiunta del nome del pacchetto alla tua applicazione](images/FCM_settings_4.jpg)

6. Viene generato il file `google-services.json`. 


Una volta che hai ottenuto le tue credenziali FCM e generato il file `google-services.json`, il passo successivo è [Crea un'istanza del servizio](push_step_2.html).

**Nota**: Google ha dichiarato obsoleto GCM e ha integrato Cloud Messaging con Firebase. Dovrai migrare le tue applicazioni client GCM su Android a FCM.

## Per iOS
{: #push_step_1_ios}

Per le applicazioni e i dispositivi iOS, il servizio APNS (Apple Push Notification Service) consente agli sviluppatori dell'applicazione di inviare notifiche remote dall'istanza del servizio {{site.data.keyword.mobilepushshort}} su IBM Cloud (il provider) alle applicazioni e ai dispositivi iOS. I messaggi sono inviati a un'applicazione di destinazione sul dispositivo. 

Devi ottenere e configurare le tue credenziali APNS. I certificati APNS sono gestiti in modo sicuro dal servizio {{site.data.keyword.mobilepushshort}} e utilizzati per stabilire una connessione al server APNs come un provider.


### Registrazione di un ID applicazione
{: #push_step_1_ios_2}

L'ID applicazione (l'identificativo del bundle) è un identificativo univoco che identifica una specifica
             applicazione. Ogni applicazione richiede un ID applicazione. I servizi come {{site.data.keyword.mobilepushshort}} sono configurati sull'ID applicazione.

Assicurati di disporre di un account [Apple Developers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com/){: new_window}. Questo è un prerequisito obbligatorio.

2. Vai al portale [Apple Developer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com){: new_window}, fai clic su **Member Center** e seleziona **Certificates, Identifiers & Profiles**.
3. Vai a **Identifiers** > **App IDs section**.
3. Nella pagina **Registering App IDs**, fornisci il nome dell'applicazione nel campo del nome di descrizione dell'ID dell'applicazione. Ad esempio: ACME Push Notifications.
4. Fornisci una stringa per il prefisso dell'ID applicazione.  
4. Per un suffisso dell'ID applicazione, scegli **Explicit App ID** e fornisci un valore ID bundle. Ti raccomandiamo di fornire una stringa di stile nome dominio inversa. Ad esempio: `com.ACME.push`.
5. Seleziona la casella di spunta **Push Notifications** e fai clic su **Continue**.
6. Completa le impostazioni e fai clic su **Register** > **Done**.

Il tuo ID applicazione è ora registrato. 

   ![ID applicazione registrato](images/push_ios_register_appid.jpg)
  

### Crea un certificato SSL di APNS di sviluppo e distribuzione
{: #push_step_1_ios_3}

Prima di ottenere un certificato APNs, devi generare una CSR (certificate signing request) e inoltrarla ad Apple, l'autorità di certificazione (CA). La CSR contiene informazioni che identificano la tua società e la tua chiave pubblica e privata che usi per firmare le tue notifiche di push Apple. Genera quindi il certificato SSL
            nel portale per sviluppatori iOS. Il certificato, insieme alla sua chiave pubblica e a quella privata,
             viene archiviato in Keychain Access.

Puoi utilizzare le APNs in due modi: 

* Modalità sandbox per lo sviluppo e il test.
* Modalità produzione quando si distribuiscono le applicazioni tramite l'App Store (o altri meccanismi di distribuzione aziendali).

Devi ottenere dei certificati separati per gli ambienti di sviluppo e
                    distribuzione. I certificati sono associati a un ID applicazione per l'applicazione
                    destinataria delle notifiche remote. per la produzione, è possibile creare fino a
                    due certificati. IBM Cloud utilizza i certificati per stabilire una connessione SSL con APNS.

<!-- Create a development and distribution SSL certificate. -->

1. Vai al sito web [Apple Developer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com){: new_window}, fai clic su **Member Center** e seleziona **Certificates, Identifiers & Profiles**.
2. Nell'area **Identifiers**, fai clic su **App
                            IDs**.
3. Dall'elenco di ID applicazione, seleziona il tuo ID applicazione e **Edit **.
4. Seleziona la casella di spunta **Push Notifications** e quindi:
	-  Nel pannello del certificato SSL di sviluppo, fai clic su **Create Certificate..**.
	-  Nel pannello del certificato SSL di produzione, fai clic su **Create Certificate..**.

	![Certificati SSL Push Notification](images/certificate_createssl.jpg)

5. Quando viene visualizzata la **schermata About Creating a Certificate Signing Request (CSR)**, avvia l'applicazione **Keychain Access** nel tuo Mac per creare una CSR (Certificate Signing Request). Fai clic su **Continue**.
6. Per l'opzione file carica CSR, fai clic su **Choose File** e seleziona il file  `CertificateSigningRequest.certSigningRequest`. 
7. Fai clic su **Continue**.
8. Nel pannello Download, Install and Backup, fai clic su **Download**. Il file `aps_development.cer` è stato scaricato.
	
	![Scarica certificato](images/push_certificate_download.jpg)	
	
6. Dal menu, seleziona **Keychain Access > Certificate Assistant > Request a Certificate From a Certificate Authority…** 
7. In **Certificate Information**, immetti l'indirizzo email che è associato al tuo account di sviluppatore di applicazioni e un nome comune. Fornisci un nome significativo che ti aiuta a identificare se si tratta di un certificato per lo sviluppo (sandbox) o la distribuzione (produzione); ad esempio, _sandbox-apns-certificate_ o _production-apns-certificate_.
8. Seleziona **Save to disk** per scaricare il file `.certSigningRequest` sul tuo desktop e fai quindi clic su **Continue**.
9. Nell'opzione del menu **Save As**, denomina il file `.certSigningRequest` e fai clic su **Save**.
10. Fai clic su **Done**. Ora hai una CSR.
11. Ritorna nella finestra **About Creating a Certificate Siging Request (CSR)** e fai clic su **Continue**. 
12. Dalla schermata **Generate**, fai clic su **Choose
                            File ... **e seleziona il file CSR che avevi salvato sul tuo
                        desktop. Fai quindi clic su **Generate**.

	![Genera certificato](images/generate_certificate.jpg)
13. Quando il tuo certificato è pronto, fai clic su **Done**.
14. Sulla schermata **Push Notifications**, fai clic su **Download** per scaricare il tuo certificato e fai quindi clic su **Done**. 
	
	![Scarica certificato](images/certificate_download.jpg)

15. Sul tuo Mac, vai a **Keychain Access > My Certificates**, e individua il certificato appena installato. Fai doppio clic sul certificato per installarlo in Keychain Access.
16. Seleziona il certificato (certificate) e la chiave privata (private key) e seleziona quindi **Export** per convertire il certificato nel formato Personal Information Exchange (formato `.p12`).

	![Esporta certificato e chiavi](images/keychain_export_key.jpg)
17. Nel campo **Save As**, dai al certificato un nome significativo. Ad esempio, `sandbox_apns.p12_certifcate` o `production_apns.p12` e fai quindi clic su **Save**.
	
	![Esporta certificato e chiavi](images/certificate_p12v2.jpg)
18. Nel campo **Enter a password**, immetti una password per proteggere gli elementi esportati e fai quindi clic su **OK**. Puoi utilizzare questa password per configurare le tue impostazioni APNS sulla console del servizio Push Notifications.
	
	![Esporta certificato e chiavi](images/export_p12.jpg)
19. **Key Access.app** ti chiede di esportare la tua chiave dalla schermata **Keychain**. Immetti la tua password amministrativa per il tuo Mac per consentire al tuo sistema di esportare questi elementi e seleziona quindi l'opzione **Always Allow**. Sul tuo desktop viene generato un certificato `.p12`.


### Creazione di profilo di provisioning di sviluppo
{: #create-push-credentials-dev-profile}

Il profilo di provisioning utilizza l'ID applicazione per determinare quali sono
            i dispositivi su cui può essere installata ed eseguita la tua applicazione e quali sono
            i servizi a cui la tua applicazione può accedere. Per ogni ID applicazione, crei
            due profili di provisioning: uno per lo sviluppo e l'altro per la distribuzione. Xcode utilizza il profilo di provisioning di sviluppo per determinare quali sono
            gli sviluppatori a cui è consentito creare l'applicazione e quali sono i dispositivi
            di cui è consentita l'esecuzione di test sull'applicazione.

Assicurati di aver registrato un ID applicazione, di averlo abilitato per il servizio {{site.data.keyword.mobilepushshort}} e di averlo configurato per utilizzare un certificato SSL APNs di sviluppo e produzione.

Crea un profilo di provisioning di sviluppo nel seguente modo:

1. Vai al portale [Apple Developer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com){: new_window}, fai clic su **Member Center** e seleziona **Certificates, Identifiers & Profiles**.
2. Vai alla [Mac Developer Library ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com/library/mac/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW62site){: new_window} , scorri fino alla sezione **Creating Development Provisioning Profiles** e segui le istruzioni per creare un profilo di sviluppo.
**Nota**: quando configuri un profilo di provisioning di sviluppo, seleziona le seguenti opzioni:
	* **iOS App Development**
	* **For iOS and watchOS apps **


### Creazione di un profilo di provisioning di distribuzione di archivio
{: #create-push-credentials-apns-distribute_profile}

Utilizza il profilo di provisioning di archivio per inoltrare la tua applicazione per la distribuzione all'App Store.

1. Vai al portale [Apple Developer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com){: new_window}, fai clic su **Member Center** e seleziona **Certificates, Identifiers & Profiles**.
2. Fai doppio clic sul file di provisioning scaricato per installarlo in Xcode.

Dopo aver ottenuto le credenziali FCM, il passo successivo è [Configura un'istanza del servizio](push_step_2.html).

## Per i browser web e le estensioni e applicazioni Chrome
{: #configure-credential-for-browsers}

Il servizio IBM {{site.data.keyword.mobilepushshort}} estende le funzionalità per inviare le notifiche al tuo browser e anche alle estensioni e applicazioni Chrome.

L'URL o il nome dominio del tuo sito Web è richiesto dal servizio {{site.data.keyword.mobilepushshort}} per identificare le richieste che devono essere consentite. 

Ad esempio: `https://www.acmebanks.com`

Un'istanza del servizio {{site.data.keyword.mobilepushshort}} supporta un solo nome dominio alla volta. Pertanto, assicurati che sia impostato lo stesso valore per Chrome, Firefox e Safari. I browser Chrome e Safari richiedono una configurazione aggiuntiva per il push web. Avrai bisogno di una chiave API FCM in quanto viene utilizzato un endpoint FCM per consegnare i messaggi in Chrome. 

Per configurare il servizio per i browser Chrome, Firefox e per le estensioni e applicazioni Chrome, consulta [Configura un'istanza del servizio](push_step_2.html).


### Configurazione del push web per Safari 
{: #configure-safari}

La versione supportata per il servizio {{site.data.keyword.mobilepushshort}} su Safari è la 10.0. Prima di poter configurare il tuo browser per la ricezione delle notifiche, devi generare un certificato tramite il tuo account Apple Developer.

#### Generazione di un certificato
{: #certificate-generation}

Assicurati di disporre in un account Apple Developer. Hai bisogno di registrare un ID push sito web e generare un certificato per configurare il tuo browser Safari per ricevere le notifiche. La seguente procedura ti aiuterà ad iniziare.

1. Nel Apple Developer Member center, fai clic su **Certificates, ID & Profiles**. 
2. Fai clic su **Identifiers** e quindi su **Website Push IDs**.
3. Scegli di creare una nuova voce selezionando l'icona più.
  ![Console Push Notifications](images/safari_1.jpg)

4. Nel pannello Register Website Push ID, fornisci un ID identificativo e una descrizione Website Push ID appropriati. Ti raccomandiamo che sia nel formato del nome a dominio inverso e che inizi con `web`. Ad esempio: `web.com.acmebanks`.
5. Registra l'ID push sito web. Ora hai un ID push sito web. 
6. Seleziona **Edit** per creare un certificato da utilizzare per l'ID push sito web.
7. Nella finestra Certificate Assistant per Certificate Information, fornisci il tuo indirizzo email e un nome comune. Lascia l'indirizzo email Certificate Authority vuoto.
8. Fai clic su **Save to disk** e seleziona **Continue**.
9. Scegli di salvare il certificato in una cartella appropriata.
10. Scegli il `.certSigningRequest` creato sul disco quando ti viene richiesto nella procedura guidata di creazione del certificato. Assicurati di scaricare il certificato di push sito web creato nel formato `.cer`.
11. Apri il certificato nello strumento KeyChain Access. Fai clic con il tasto destro del mouse ed esportalo come certificato p12. Annota la password fornita durante la generazione del certificato p12.

Dopo aver generato un certificato, il prossimo passo è di [Configurare un'istanza del servizio](push_step_2.html).

