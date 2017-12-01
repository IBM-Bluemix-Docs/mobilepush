---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Lernprogramm zur Einführung
{: #getting-started-with-push}

In diesem Lernprogramm zur Einführung von {{site.data.keyword.mobilepushfull}} wird der Prozess der Aktivierung einer Android-App für den Empfang von Push-Benachrichtigungen und das Senden einer einfachen Push-Benachrichtigung an ein Gerät erläutert.
{:shortdesc}

<div id="prerequisites"></div>

## Vorbemerkungen
{: #prereqs}

Sie benötigen ein [IBM Cloud-Konto](https://console.bluemix.net/registration/), eine Instanz des
{{site.data.keyword.mobilepushshort}}-Service und die folgenden Tools und Voraussetzungen:

  * Android API 15+
  * Android 4.0.3+
  * Android Studio
  * Gradle
  * [Android-Beispielanwendung 'helloPush'](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush){: new_window}
  * [BMSCore](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window}- und
  [BMSPush](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-push){: new_window}-SDKs, die mit Android Studio oder Gradle installiert wurden

## Schritt 1: {{site.data.keyword.mobilepushshort}}-Instanz für Android-Geräte konfigurieren

1. Kopieren Sie den Paketnamen aus der Beispieldatei `AndroidManifest.xml`.

2. Erstellen Sie eine FCM-App und fügen Sie den Paketnamen Ihrer Android-App hinzu:
  1. Klicken Sie in der [Firebase-Konsole](https://console.firebase.google.com){: new_window} auf **Add Project**, geben Sie einen Projektnamen an, und klicken Sie auf **Create Project**.
  2. Klicken Sie auf **Add Firebase to your Android app**, geben Sie den Paketnamen der App ein, und klicken Sie auf **Register App**. Sie können die beiden nächsten Eingabeaufforderungen überspringen, indem Sie auf **Continue > Finish** klicken. 

3. Fügen Sie die FCM-Berechtigungsnachweise Ihrer {{site.data.keyword.mobilepushshort}}-Instanz hinzu:
  1. Rufen Sie in der Firebase-Konsole **Settings > Project Settings > Cloud Messaging** auf und kopieren Sie den Serverschlüssel und die Absender-ID.
  2. Öffnen Sie in der {{site.data.keyword.Bluemix_notm}}-Konsole das Dashboard für Ihre Serviceinstanz.
  3. Klicken Sie auf **Verwalten > Konfigurieren**.
  4. Geben Sie die Absender-ID und den Serverschlüssel in das Feld für die **GCM/FCM-Push-Berechtigungsnachweise** ein.

## Schritt 2: Android-App für das Senden von Push-Benachrichtigungen aktivieren

1. Konfigurieren Sie die Projektebenendatei `build.gradle` und die Modulebenendatei `build.gradle`:

  * Fügen Sie die SDK-Abhängigkeit zur Projektebenendatei `build.gradle` hinzu:
  
  ```
  dependencies {
  ........
  compile group: 'com.ibm.mobilefirstplatform.clientsdk.android',
      name: 'push',
      version: '3.+',
      ext: 'aar',
      transitive: true
  .......
	      }
  ```
  {: codeblock}

  * Fügen Sie die folgenden Abhängigkeiten zur Modulebenendatei `build.gradle` hinzu:
  
  ```
  dependencies {
    classpath 'com.android.tools.build:gradle:2.2.3'
    classpath 'com.google.gms:google-services:3.0.0'
  }
  ```
  {: codeblock}
  
  * Fügen Sie die Google Play Services-Abhängigkeit am Ende der Modulebenendatei `build.gradle`  nach den Abhängigkeiten hinzu:
  
  ```
  apply plugin: 'com.google.gms.google-services'
  ```
  {: codeblock}
  
  * Fügen Sie die folgenden Berechtigungen zur Datei `AndroidManifest.xml` Ihrer App hinzu:
  
  ```
  <uses-permission android:name="android.permission.INTERNET"/>
  <uses-permission android:name="android.permission.GET_ACCOUNTS" />
  <uses-permission android:name="android.permission.USE_CREDENTIALS" />
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  ```
  {: codeblock}
  
  * Fügen Sie die Einstellungen für die Benachrichtigungsabsicht für die Aktivität hinzu. 
  
  Mit dieser Einstellung wird die App gestartet, wenn der Benutzer im Benachrichtigungsbereich auf die empfangene Benachrichtigung klickt. Ersetzen Sie `<yourAndroidPackageName>` durch den Paketnamen der App, der in Ihrer App verwendet wird.
  
  ```
  <intent-filter>
		<action android:name="Your_Android_Package_Name.IBMPushNotification"/>
		<category  android:name="android.intent.category.DEFAULT"/>
	</intent-filter>
  ```
  {: codeblock}
  
  * Aktualisieren Sie den Absichtsservice und die Absichtsfilter von FCM für die Ereignisbenachrichtigungen des Typs `RECEIVE` und `REGISTRATION`:
  
  ```
  <service android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushIntentService"
    android:exported="true" >
  <intent-filter>
    	    <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
	</service>
	<service
    android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPush"
    android:exported="true" >
  <intent-filter>
        <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
    </intent-filter>
	</service>
  ```
  {: codeblock}
  
2. Öffnen Sie die App in Android Studio und fügen Sie die Datei `google-services.json` in das Stammverzeichnis des App-Moduls ein.

3. Initialisieren Sie das Core-SDK und das Push-SDK. 

Die Methode 'onCreate()' der Hauptaktivität in Ihrer Android-App ist eine übliche Position für den Initialisierungscode:

```
// SDK initialisieren
BMSClient.getInstance().initialize(this, "bluemixRegionSuffix");

//Initialize client Push SDK
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "appGUID", "clientSecret");
```
{: codeblock}
Dabei gilt Folgendes: `<bluemixRegionSuffix>` gibt den Standort an, an dem die App gehostet wird. Sie können einen der folgenden Werte verwenden:

  * BMSClient.REGION_US_SOUTH
  * BMSClient.REGION_UK
  * BMSClient.REGION_SYDNEY

'appGUID' ist der GUID-Wert der Push-App und 'clientSecret' ist der geheime Schlüssel des Push-Clients. 

## Schritt 3: Android-Gerät bei der {{site.data.keyword.mobilepushshort}}-Instanz registrieren

1. Führen Sie die App aus.

2. Verwenden Sie die API 'MFPPush.register()', um das Gerät für die Aktivierung benutzerbasierter Benachrichtigungen zu registrieren.

```
//Gerät für die Push Notifications-Serviceinstanz registrieren
 push.registerDeviceWithUserId("userId",new MFPPushResponseListener<String>() {
 @Override
		public void onSuccess(String response) {
 //Erfolgreiche Geräteregistrierung hier verarbeiten
 }
 @Override
    public void onFailure(MFPPushException ex) {
 //Nicht erfolgreiche Geräteregistrierung hier verarbeiten
 }
 });
 ```
 {: codeblock}
 
 
 'userId' wird verwendet, um die eindeutige Benutzer-ID für die Registrierung von Push-Benachrichtigungen zu übergeben. Stellen Sie sicher, dass auch der geheime Schlüssel 'clientSecret' angegeben wird.
 {: tip}
 
 ## Schritt 4: Einfache Push-Benachrichtigung senden
 
 1. Navigieren Sie in der {{site.data.keyword.Bluemix_notm}}-Konsole zum Dashboard für Ihre Serviceinstanz.
 2. Klicken Sie auf **Verwalten > Benachrichtigungen senden**.
 3. Wählen Sie Android-Geräte aus dem Menü **Senden an** aus.
 4. Geben Sie Ihre Nachricht ein und klicken Sie auf **Senden**. 
 
