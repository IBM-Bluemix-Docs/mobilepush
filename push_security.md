---

copyright:
  years: 2015, 2017, 2019
lastupdated: "28 May 2019"

keywords: push notifications, notification, security, appsecret, api keys

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:tip: .tip}

# Security in Push Notifications 
{: #security-in-push-notifications}

The {{site.data.keyword.mobilepushshort}} APIs are secured by -

- **appSecret**: The `appSecret` protects APIs that are typically invoked by back end applications - such as the API to send {{site.data.keyword.mobilepushshort}} and the API to configure settings.
- **clientSecret**:  The `clientSecret` protects APIs that are typically invoked by mobile client applications. There is only one API related to registration of a device with an associated UserId that requires this `clientSecret`. None of the other APIs invoked from mobile clients require the `clientSecret`. 
- **API Keys**: Application programming interface keys (API keys) are available through Cloud IAM for you to use to authenticate by using API or CLI as a user or service ID. These API keys are provided through Cloud IAM and therefore cannot be used generally to authenticate with IBMid outside of IBM Cloud. 

The `appSecret` and `clientSecret` are allocated to every service instance at the time of binding an application with {{site.data.keyword.mobilepushshort}} service. Refer to the [REST APIs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://eu-gb.imfpush.cloud.ibm.com/imfpush/) documentation for information on how the secrets are to be passed and for what APIs.

## appSecret 
{: #push-api-rest-secret}

When an application binds to the {{site.data.keyword.mobilepushshort}}, the service generates an appSecret (a unique key) and passes it in the response header. If you are using the IBM {{site.data.keyword.mobilepushshort}} for IBM Cloud Rest API, use the REST API reference to obtain information on which APIs you need to secure. For information, see the [Push REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://eu-gb.imfpush.cloud.ibm.com/imfpush/){: new_window}.

The request header must contain the appSecret. If not, the server returns a 401 Unauthorized Error code. When the {{site.data.keyword.mobilepushshort}} is added to an application, a specific AppID is created. As part of the response, you get a header called appSecret that is used for creating tags or sending messages. The operation happens through services in the catalog or the boilerplate.

To get the appSecret value:

1. Click the *app-name* that is bound to the push service.
2. Click the **Show Credentials** link to display the appSecret (AppID).

The **Show Credentials** screen shows information about the AppSecret:
```
	{
    "imfpush_Dev": [
    {
     "name": "testapp1",
     "label": "imfpush_Dev",
     "plan": "Basic",
     "credentials": {
       "url": "http://https://eu-gb.imfpush.cloud.ibm.com/imfpush/v1/apps/b615b280-b37e-4042-8815-38a758f234e2",
       "admin_url": "//mobile.cloud.ibm.com/imfpushdashboard/?appGuid=b615b280-b37e-4042-8815-38a758f234e2",
       "appSecret": "8dac71a5-2219-42b3-a9f3-dbb828ba1f04",
       }
     }
    ]
    }
```
	{: codeblock} 


**Note**: Earlier applications were required to pass the clientSecret only when registering or updating devices with userId field. All other APIs invoked by mobile and browser clients did not require clientSecret. These old applications can continue to use the clientSecret optionally for device registrations or updating calls. However, it is strongly recommended that clientSecret check is enforced for all client API calls. To enforce this in existing applications, there is a new `verifyClientSecret` API that is published.  For new applications, clientSecret check will be enforced on all client API calls and this behavior cannot be changed with the `verifyClientSecret` API.

By default, client secret verification is enforced only in new apps. Both existing and new apps are allowed to enable or disable the client secret verification using the verifyClientSecret REST API. It is recommended that you enforce client secret verification to avoid exposing devices to users who might know the applicationId and deviceId.

Ensure that the `clientSecret` is kept confidential and never hard-coded into the mobile app. There are various application initialization patterns that can be used to pull in the `clientSecret` dynamically during the applications runtime. The sequence diagram outlines on such possible pattern.
![Enable_Push](images/init_client_secret.jpg) 

## API keys for user authentication
{: #push-api-key}

An API key is a unique code that is passed in to an API to identify the calling application or user. API keys are used to track and control how the API is being used, for example to prevent malicious use or abuse of the API. The API key often acts as both a unique identifier and a secret token for authentication, and generally has a set of access rights specific to the identity associated with it.

Refer [here](https://cloud.ibm.com/docs/iam?topic=iam-manapikey) for more details on managing and working with API keys.

