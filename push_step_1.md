---

copyright:
  years: 2015, 2017, 2019
lastupdated: "18 February 2019"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Step 2: Obtain your notification provider credentials
{: #push_step_1}

To set up {{site.data.keyword.mobilepushshort}} service, you need to obtain the required credentials from your push notification provider. 

## For Android
{: #push_step_1_android}

Firebase Cloud Messaging (FCM) is the gateway used to deliver push notifications to Android devices, Google Chrome browser and Chrome Apps & Extensions. To set up the {{site.data.keyword.mobilepushshort}} service on the console, you need to get your FCM credentials (Sender ID and API key). 

The API key is stored securely and used by the {{site.data.keyword.mobilepushshort}} service to connect to the FCM server and the sender ID (project number) is used by the Android SDK and the JS SDK for  Google Chrome and Mozilla Firefox on the client side. 

To set up FCM and obtain your credentials, complete the steps:

1. Visit the [Firebase Console ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.firebase.google.com/?pli=1){: new_window}. A Google user account is required. 
2. Select **Add project**. 
3. In the Create a project window, provide a project name, choose a country/region and click **Create project**.
3. In the navigation pane, select **Settings** > **Project settings**.
4. Choose the Cloud Messaging tab to obtain your project credentials - Server API Key and a Sender ID. Note that the Server key listed in FCM is the same as Server API Key.
   
	![Obtaining credentials for FCM](images/FCM_settings_2.jpg)

You would also need to generate the `google-services.json` file. Complete the following steps:

1. In the Firebase console, click the **Project Settings** icon.
    
	![Firebase Project Settings](images/FCM_settings_6.jpg)

3. Select **ADD APP** or **Add Firebase to your Android app** icon from the General tab on the Your apps pane.
    
4. In Add Firebase to your Android app window, first add **com.ibm.mobilefirstplatform.clientsdk.android.push** as the Package Name. The App nickname field is optional. Click **REGISTER APP**. 
    
	![Adding Firebase to your Android window](images/FCM_1.jpg)

5. Now, include the package name of your application, by entering the package name in Add Firebase to your Android app window. The App nickname field is optional. Click **REGISTER APP**.  Below is an example -

	![Adding the package name of your application](images/FCM_settings_4.jpg)

6. The `google-services.json` file is generated. 

Once you have obtained your FCM credentials and have generated the `google-services.json` file, the next step is to [Create a service instance](/docs/services/mobilepush/push_step_2.html).

**Note**: Google has deprecated GCM and has integrated Cloud Messaging with Firebase. You will have to migrate your GCM client apps on Android to FCM.

## For iOS
{: #push_step_1_ios}

For iOS devices and applications, Apple Push Notification Service (APNs) allows application developers to send remote notifications from {{site.data.keyword.mobilepushshort}} service instance on IBM Cloud (the provider) to iOS devices and applications. Messages are sent to a target application on the device. 

You need to obtain and configure your APNs credentials. The APNs certificates are securely managed by {{site.data.keyword.mobilepushshort}} service and used to connect to APNs server as a provider.


### Registering an App ID
{: #push_step_1_ios_2}

The App ID (the bundle identifier) is a unique identifier that identifies a specific application. Each application requires an App ID. Services like the {{site.data.keyword.mobilepushshort}} service are configured to the App ID.

Ensure that you have an [Apple Developers ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com/){: new_window} account. This is a mandatory prerequisite.

2. Go to the [Apple Developer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com){: new_window} portal, click **Member Center**, and select **Certificates, Identifiers & Profiles**.
3. Go to **Identifiers** > **App IDs section**.
3. In the **Registering App IDs** page, provide the App name in the App ID Description Name field. For example: ACME Push Notifications.
4. Provide a string for the App ID Prefix.  
4. For the App ID Suffix, choose **Explicit App ID** and provide a Bundle ID value. It is recommended that you provide a reverse domain-name style string. For example: `com.ACME.push`.
5. Select the **Push Notifications** check-box and click **Continue**.
6. Go through your settings and click **Register** > **Done**.

Your App ID is now registered. 

   ![Registered App ID](images/push_ios_register_appid.jpg)
  

### Create a development and distribution APNs SSL certificate
{: #push_step_1_ios_3}

Before you obtain an APNs certificate, you must first generate a certificate signing request (CSR) and submit it to Apple, the certificate authority (CA). The CSR contains information that identifies your company and your public and private key that you use to sign for your Apple push notifications. Then, generate the SSL certificate on the iOS Developer Portal. The certificate, along with its public and private key, is stored in Keychain Access.

You can use APNs in two modes: 

* Sandbox mode for development and testing.
* Production mode when distributing applications through the App Store (or other enterprise distribution mechanisms).

You must obtain separate certificates for your development and distribution environments. The certificates are associated with an App ID for the app that is the recipient of remote notifications. For production, you can create up to two certificates. IBM Cloud uses the certificates to establish an SSL connection with APNs.

<!-- Create a development and distribution SSL certificate. -->

1. Go to the [Apple Developer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com){: new_window} website, click **Member Center**, and select **Certificates, Identifiers & Profiles**.
2. In the **Identifiers** area, click **App IDs**.
3. From your list of App IDs, select your App ID, then select **Edit **.
4. Select the the **Push Notifications** check-box, and then:
	-  On Development SSL certificate pane, click **Create Certificate..**.
	-  On Production SSL certificate pane, click  **Create Certificate..**.

	![Push Notification SSL certificates](images/certificate_createssl.jpg)

5. When the **About Creating a Certificate Signing Request (CSR) screen** displays, start the **Keychain Access** application on your Mac to create a Certificate Signing Request (CSR). Click **Continue**.
6. For the Upload CSR file option, click **Choose File**, and select file  `CertificateSigningRequest.certSigningRequest`. 
7. Click **Continue**.
8. On the Download, Install and Backup pane, click **Download**. The `aps_development.cer` file is downloaded.
	
	![Download certificate](images/push_certificate_download.jpg)	
	
6. From the menu, select **Keychain Access > Certificate Assistant > Request a Certificate From a Certificate Authority…** 
7. In **Certificate Information**, enter the email address that is associated with your App Developer account and a common name. Give a meaningful name that helps you identify whether it is a certificate for development (sandbox) or distribution (production); for example, _sandbox-apns-certificate_ or _production-apns-certificate_.
8. Select **Save to disk** to download the `.certSigningRequest` file to your desktop, then click **Continue**.
9. In the **Save As** menu option, name the `.certSigningRequest` file and click **Save**.
10. Click **Done**. You now have a CSR.
11. Return to the **About Creating a Certificate Siging Request (CSR)** window and click **Continue**. 
12. From the **Generate** screen, click **Choose File ...** and select the CSR file that you saved on your desktop. Then, click **Generate**.

	![Generate certificate](images/generate_certificate.jpg)
13. When your certificate is ready, click **Done**.
14. On the **Push Notifications** screen, click **Download** to download your certificate, then click **Done**. 
	
	![Download certificate](images/certificate_download.jpg)

15. On your Mac, go to **Keychain Access > My Certificates**, and locate your newly installed certificate. Double-click the certificate to install it into the Keychain Access.
16. Select the certificate and private key, and then select **Export** to convert the certificate into the personal information exchange format (`.p12` format).

	![Export certificate and keys](images/keychain_export_key.jpg)
17. In the **Save As** field, provide the certificate a meaningful name. For example, `sandbox_apns.p12_certifcate` or `production_apns.p12`, then click **Save**.
	
	![Export certificate and keys](images/certificate_p12v2.jpg)
18. In the **Enter a password** field, enter a password to protect the exported items, then click **OK**. You can use this password to configure your APNs settings on the Push Notifications service console.
	
	![Export certificate and keys](images/export_p12.jpg)
19. The **Key Access.app** prompts you to export your key from the **Keychain** screen. Enter your administrative password for your Mac to allow your system to export these items, and then select the **Always Allow** option. A `.p12` certificate is generated on your desktop.


### Creating a development provisioning profile
{: #create-push-credentials-dev-profile}

The provisioning profile works with the App ID to determine which devices can install and run your app and which services your app can access. For each App ID, you create two provisioning profiles: one for development and the other for distribution. Xcode uses the development provisioning profile to determine which developers are allowed to build the application and which devices are allowed to be tested on the application.

Ensure that you have registered an App ID, enabled it for {{site.data.keyword.mobilepushshort}} service, and configured it to use a development and production APNs SSL certificate.

Create a development provisioning profile, as follows:

1. Go to the [Apple Developer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com){: new_window} portal, click **Member Center**, and select **Certificates, Identifiers & Profiles**.
2. Go to the [Mac Developer Library ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com/library/mac/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW62site){: new_window}, scroll to the **Creating Development Provisioning Profiles** section, and follow the instructions to create a development profile.
**Note**: When you configure a development provision profile, select the following options:
	* **iOS App Development**
	* **For iOS and watchOS apps**


### Creating a store distribution provisioning profile
{: #create-push-credentials-apns-distribute_profile}

Use the store provisioning profile to submit your app for distribution to the App Store.

1. Go to the [Apple Developer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com){: new_window} portal, click **Member Center**, and select **Certificates, Identifiers & Profiles**.
2. Double-click the downloaded provisioning profile to install it into Xcode.

After obtaining the credentials, the next step is to [Configure a service instance](/docs/services/mobilepush/push_step_2.html).

## For web browsers and Chrome Apps & Extensions
{: #configure-credential-for-browsers}

The IBM {{site.data.keyword.mobilepushshort}} service extends capabilities to send notifications to your browser and also Chrome Apps & Extensions.

The website URL or the domain name of your website is required by the {{site.data.keyword.mobilepushshort}} service to identify the requests that need to be allowed. 

For example: `https://www.acmebanks.com`

A {{site.data.keyword.mobilepushshort}} service instance supports only one domain name at a time. Hence, ensure that the same value is set for Chrome, Firefox and Safari. Chrome and Safari browsers require additional configuration for web push. You would need an FCM API key, as an FCM endpoint is used to deliver messages in Chrome. 

To set up the service for Chrome, Firefox browsers, and Chrome Apps & Extensions, see [Configure a service instance](/docs/services/mobilepush/push_step_2.html).


### Configuring for Safari web push 
{: #configure-safari}

The supported version for {{site.data.keyword.mobilepushshort}} service on Safari is 10.0. You need to generate a certificate through your Apple Developer account, before you can configure your browser to receive notifications.

#### Generating a certificate
{: #certificate-generation}

Ensure that you have an Apple Developer account. You need to register a Website Push ID and generate a certificate to configure your Safari browser to receive notifications. The following steps will help you get started.

1. In the Apple Developer Member center, click **Certificates, ID & Profiles**. 
2. Click **Identifiers** and then **Website Push IDs**.
3. Choose to create a new entry by selecting the plus icon.
  ![Push Notifications console](images/safari_1.jpg)

4. In the Register Website Push ID panel, provide an appropriate Website Push ID description and identifier ID. It is recommended that this is in reverse-domain name format, starting with `web`. For example: `web.com.acmebanks`.
5. Register the Website Push ID. You now have your Website Push ID 
6. Select **Edit** to create a certificate to use for the Website Push ID.
7. In the Certificate Assistant window for Certificate Information, provide your email ID, and a common name. Leave the Certificate Authority email address as blank.
8. Click **Save to disk** and select **Continue**.
9. Choose to save the certificate to an appropriate folder.
10. Choose the `.certSigningRequest` created on the disk when prompted in the wizard for generating the certificate. Ensure that you download the Website push certificate created in the `.cer` format.
11. Open the Certificate in the KeyChain Access tool. Right-click and export as a p12 certificate. Note the password provided during the generation of the p12 certificate.

After generating a certificate, the next step is to [Configure a service instance](/docs/services/mobilepush/push_step_2.html).

