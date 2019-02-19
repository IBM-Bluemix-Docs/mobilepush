---

copyright:
  years: 2015, 2017, 2019
lastupdated: "17 February 2019"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Push Notifications REST APIs
{: #push-api-rest}

You can use a REST (Representational State Transfer) API (application program interface) for {{site.data.keyword.mobilepushshort}}. You can also use the SDK and [Push API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://imfpush.ng.bluemix.net/imfpush/){: new_window} to further develop your client applications.

With the Push REST API, backend server applications and clients can access {{site.data.keyword.mobilepushshort}} functions.

- Device registrations
- Registrations
- Messages
- Subscriptions
- Tags
- Webhooks

To obtain the base URL for the REST API, complete the steps:

1. Create a back end application in the Boilerplates section IBM Cloud® catalog by choosing the MobileFirst Services Starter. This binds the {{site.data.keyword.mobilepushshort}} service to the application. You can also create a service instance of Push and leave it unbounded. 
1. In the main page of the IBM Cloud Catalog, go to the **Applications** area and then select your app.
3. Click **MOBILE OPTIONS**. The route and app GUID values are displayed at the start of the details page for your app. The Show Credentials screen shows information about the AppSecret. You can get the application secret from Mobile Options and also client secret for some of the API's.

You can also use the command line to get the service credentials:

```
    cf create-service-key {push_instance_name} {key_name}
    cf service-key {push_instance_name} {key_name}
```
	{: codeblock}

## Accept language header
{: #push-api-rest-accept}

The "Accept-Language" header specifies which language to use for the error messages that are output by [Push REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://imfpush.ng.bluemix.net/imfpush/){: new_window}. The following languages are supported for error messages: Chinese (Simplified), Chinese, (Traditional), English (US), German, French, Italian, Japanese, Korean, Portuguese, and Spanish.


## Push REST API filters
{: #push-api-rest-filters}

Filters define a search criteria that restrict data that is returned from a GET API of {{site.data.keyword.mobilepushshort}}. Apply the filters against the result of the Get operation that you want to filter. The filter restricts the number of entries included in the result. For example, you can use a filter to search for tags that start with "test". 

Filters can be generated using the following syntax:

**name**: The field name on which the filter is being applied.

**operator**: Either == (Exact Match) or =@ (Contains Substring) that describes filter match to use.

**expression**: The values to include in the result.

When a comma and a backslash are displayed in an expression, they must be backslash-escaped.

When you are using multiple filters, they can be combined by using AND and OR logic.

- For AND logic, use multiple filters in the query.
- For OR logic, use a comma(,) inside of the filter expression.
- For both AND and OR logic: A single query can have both AND and OR logic. Each filter is evaluated individually before the filters are combined in an AND expression.

For the device GET API the following combinations are supported:
-The name is the platform field.
- Except for the platform, the operator can be == or =@
- For the platform, the operator must be ==. If operator =@ is used, the value can be a sub string.
- If == is used, the value must be an exact matching string.

For the subscription GET API the following combinations are supported:

- The name can be one of these fields: tagName or deviceId
- Except for the platform, the operator can be == or =@
- For the platform, the operator must be ==
- If the =@ operator is used, the value can be a sub string. If the == operator is used, the value must be an exact matching string.
- For the tag GET API the following combinations are supported:
- The name can be one of these fields: “name” or “description”
- If operator =@ is used, the value can be a sub string.
- If == is used, the value must be an exact matching string.


## Push Notifications service response codes
{: #push-api-response-codes}

Status: 405 Method Not Allowed - Appropriate method expected.
