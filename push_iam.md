---

copyright:
  years:  2017, 2019
lastupdated: "2019-06-13"

keywords: push notifications, notifications, service access, manage, user roles

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Managing service access
{: #service-access-management}

With {{site.data.keyword.mobilepushshort}} and {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) account owners can manage user access in your account.
{: shortdesc}

As an account owner, you can set policies within your account to create different levels of access for different users. For example, certain users can have **Read only** access to one instance, but **Write** access to another. You can decide who is allowed to create, update, and delete instances of {{site.data.keyword.mobilepushshort}}.

**Note:** As the {{site.data.keyword.mobilepushshort}} service has adopted IAM, the App secret will not be generated for the new instances. You must use the [API keys instead](https://cloud.ibm.com/docs/iam?topic=iam-manapikey).

## User roles
{: #roles}

The scope of an access policy is based on a user's assigned role.
{: shortdesc}

Policies enable access to be granted at different levels. Some of the options include:
<ul>
  <li>Access across all instances of the service in your account</li>
  <li>Access to an individual service instances in your account</li>
  <li>Access to a specific resource within an instance</li>
  <li>Access to all IAM-enabled services in your account</li>
</ul>

Platform management roles enable users to perform tasks on service resources at the platform level. For example, roles can be assigned to determine who can create or delete IDs, create instances, and bind instances to apps. The following table details the actions as they correlate to platform management roles.

<table>
  <tr>
    <th>Platform role</th>
    <th>Permissions</th>
    <th>Example actions</th>
  </tr>
  <tr>
    <td><i>Viewer</i></td>
    <td>View {{site.data.keyword.mobilepushshort}} instances.</td>
    <td>You can see a Cloud Directory user's data or the identity provider configuration.</td>
  </tr>
  <tr>
    <td><i>Editor</i></td>
    <td>View and bind {{site.data.keyword.mobilepushshort}} instances.</td>
    <td>You can bind applications to an instance of {{site.data.keyword.mobilepushshort}}.</td>
  </tr>
  <tr>
    <td><i>Operator</i></td>
    <td>Create, delete, edit, suspend, resume, view, or bind {{site.data.keyword.mobilepushshort}} instances.</td>
    <td>You can create or delete an {{site.data.keyword.mobilepushshort}} instance from the catalog.</td>
  </tr>
  <tr>
    <td><i>Administrator</i></td>
    <td>All management actions for all services in the account.</td>
    <td>You can perform all operator actions and the ability to assign policies to other users.</td>
  </tr>
</table>

</br>
</br>
The following table details actions that are mapped to service access roles. Service access roles enable users to access {{site.data.keyword.mobilepushshort}} as well as the ability to call the {{site.data.keyword.mobilepushshort}} API.


<table>
  <tr>
    <th>Service role</th>
    <th>Permissions</th>
    <th>Example actions</th>
  </tr>
  <tr>
    <td><i>Reader</i></td>
    <td>View {{site.data.keyword.mobilepushshort}} instance data.</td>
    <td>Can view the details of the service instance such as user data or identity provider information.</td>
  </tr>
  <tr>
    <td> <i>Writer or Manager</i></td>
    <td>View and change an {{site.data.keyword.mobilepushshort}} instance.</td>
    <td>Can perform all Reader actions and edit the service instance, such as editing the identity provider configuration. </li></ul></td>
  </tr>
</table>

For more information about assigning user roles in the UI, see [Managing IAM access](https://cloud.ibm.com/docs/iam?topic=iam-iammanidaccser#iammanidaccser).


## {{site.data.keyword.mobilepushshort}} access policies
{: #access}

Every user who accesses the {{site.data.keyword.mobilepushshort}} service in your account must be assigned an access policy with an IAM user role defined. That policy determines what actions the user can perform within the context of the service or instance you select.
{: shortdesc}

The actions are customized and defined by the {{site.data.keyword.Bluemix_notm}} service as operations that are allowed to be performed in the service. The actions are then mapped to IAM user roles. Some of the actions taken you can track with the {{site.data.keyword.cloudaccesstrailshort}} service. In the following table, the actions and required permissions for {{site.data.keyword.mobilepushshort}} are mapped.

|Action |Explanation |Required role |
|----------------------------------------------------|------------------|------------------------------|
|`GET /imfpush/v1/apps/{applicationId}/settings/*` |Get app settings |Manager, Writer, Reader|
|`DELETE /imfpush/v1/apps/{applicationId}/settings/* |Delete app settings |Manager|
|`PUT /imfpush/v1/apps/{applicationId}/settings/*` |Update app settings |Manager|
|`GET /imfpush/v1/apps/{applicationId}/devices/* ` |Get devices |Manager, Writer, Reader|
|`POST /imfpush/v1/apps/{applicationId}/devices` |Register device |Manager, Writer|
|`PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Update device |Manager, Writer|
|`DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId}` |Delete device |Manager|
|`POST /imfpush/v1/apps/{applicationId}/messages` |Send messages |Manager, Writer|
|`POST /imfpush/v1/apps/{applicationId}/messages/bulk` |Send bulk messages |Manager, Writer|
|`DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId}` |Delete a message |Manager|
|`GET /imfpush/v1/apps/{applicationId}/messages/*` |Get messages |Manager, Reader, Writer|
|`PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus` |Update message delivery status|Manager, Writer|
|`POST /imfpush/v1/apps/{applicationId}/tags` |Create tags |Manager, Writer|
|`PUT /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Update tag   |Manager, Writer|
|`DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName}` |Delete tag   |Manager|
|`GET /imfpush/v1/apps/{applicationId}/tags/*` |Get tags |Manager, Reader, Writer|
|`POST /imfpush/v1/apps/{applicationId}/subscriptions` |Create subscriptions |Manager, Writer|
|`DELETE /imfpush/v1/apps/{applicationId}/subscriptions` |Delete subscriptions |Manager|
|`GET /imfpush/v1/apps/{applicationId}/subscriptions` |Get Subscriptions |Manager, Reader, Writer|
|`POST /imfpush/v1/apps/{applicationId}/webhooks` |Create webhook |Manager, Writer|
|`PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Update webhook |Manager, Writer|
|`DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName}` |Delete webhook |Manager|
|`GET /imfpush/v1/apps/{applicationId}/webhooks/*` |Get webhook |Manager, Reader, Writer|-|

## Working with API keys
{: #apikeys}

Upon creating service creadentials, you may notice an apiKey is displayed instead of the appSecret.

To use any REST APIs, you must generate the access token using the following curl command:

### Parameters

```
  curl -k -X POST \ 
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```

### Response

```
{
    "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```

Upon generating the access token using the preceding curl command, you may now operate the Rest API’s by passing the ‘Bearer <value of access_token>’ in the Authorization header

For example:

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \ 
   "message": { \ 
     "alert": "Notification alert message" \ 
   } \ 
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

For more information about IAM, see [IAM Access](https://cloud.ibm.com/docs/iam?topic=iam-userroles).
