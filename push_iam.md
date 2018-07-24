---

copyright:
  years:  2017
lastupdated: "2017-10-09"

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

For more information about IAM, see [IAM Access](/docs/iam/users_roles.html).

## User roles
{: #roles}

The scope of an access policy is based on a user's assigned role.
{: shortdesc}

Policies enable access to be granted at different levels. Some of the options include:
<ul><ul>
  <li>Access across all instances of the service in your account</li>
  <li>Access to an individual service instances in your account</li>
  <li>Access to a specific resource within an instance</li>
  <li>Access to all IAM-enabled services in your account</li>
</ul></ul>

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

For more information about assigning user roles in the UI, see [Managing IAM access](/docs/iam/mngiam.html#iammanidaccser).


## {{site.data.keyword.mobilepushshort}} access policies
{: #access}

Every user who accesses the {{site.data.keyword.mobilepushshort}} service in your account must be assigned an access policy with an IAM user role defined. That policy determines what actions the user can perform within the context of the service or instance you select.
{: shortdesc}

The actions are customized and defined by the {{site.data.keyword.Bluemix_notm}} service as operations that are allowed to be performed in the service. The actions are then mapped to IAM user roles. Some of the actions taken you can track with the {{site.data.keyword.cloudaccesstrailshort}} service. In the following table, the actions and required permissions for {{site.data.keyword.mobilepushshort}} are mapped.

<table>
  <tr>
    <th>Action</th>
    <th>Explanation</th>
    <th>Required role</th>
  </tr>
  <tr>
    <td><code> GET /imfpush/v1/apps/{applicationId}/settings/* </code></td>
    <td>Get app settings</td>
    <td>Manager, Writer, Reader</td>
  </tr>
  <tr>
    <td><code>DELETE /imfpush/v1/apps/{applicationId}/settings/* </code></td>
    <td>Delete app settings</td>
    <td>Manager</td>
  </tr>
  <tr>
    <td><code>PUT /imfpush/v1/apps/{applicationId}/settings/* </code></td>
    <td>Update app settings</td>
    <td>Manager</td>
  </tr>
  <tr>
    <td><code>GET /imfpush/v1/apps/{applicationId}/devices/* </code></td>
    <td>Get devices </td>
    <td>Manager, Reader, Writer</td>
  </tr>
  <tr>
    <td><code>POST /imfpush/v1/apps/{applicationId}/devices </code></td>
    <td>Register device</td>
    <td>Manager, Writer</td>
  </tr>
  <tr>
    <td><code>PUT /imfpush/v1/apps/{applicationId}/devices/{deviceId} </code></td>
    <td>Update device</td>
    <td>Manager, Writer</td>
  </tr>
  <tr>
    <td><code>DELETE /imfpush/v1/apps/{applicationId}/devices/{deviceId} </code></td>
    <td>Delete device</td>
    <td>Manager</td>
  </tr>
  <tr>
    <td><code>POST /imfpush/v1/apps/{applicationId}/messages </code></td>
    <td>Send messages</td>
    <td>Manager, Writer</td>
  </tr>
  <tr>
    <td><code>POST /imfpush/v1/apps/{applicationId}/messages/bulk </code></td>
    <td>Send bulk messages</td>
    <td>Manager, Writer</td>
  </tr>
  <tr>
    <td><code>DELETE /imfpush/v1/apps/{applicationId}/messages/{messageId} </code></td>
    <td>Delete a message</td>
    <td>Manager</td>
  </tr>
  <tr>
    <td><code>GET /imfpush/v1/apps/{applicationId}/messages/* </code></td>
    <td>Get messages</td>
    <td>Manager, Reader, Writer</td>
  </tr>
  <tr>
    <td><code>PUT /imfpush/v1/apps/{applicationId}/messages/{messageId}/deliverystatus </code></td>
    <td>Update message delivery status</td>
    <td>Manager, Writer</td>
  </tr>  
  <tr>
    <td><code>POST /imfpush/v1/apps/{applicationId}/tags </code></td>
    <td>Create tags</td>
    <td>Manager, Writer</td>
  </tr>  
  <tr>
    <td><code>PUT /imfpush/v1/apps/{applicationId}/tags/{tagName} </code></td>
    <td>Update tag</td>
    <td>Manager, Writer</td>
  </tr>  
  <tr>
    <td><code>DELETE /imfpush/v1/apps/{applicationId}/tags/{tagName} </code></td>
    <td>Delete tag</td>
    <td>Manager</td>
  </tr>  
  <tr>
    <td><code>GET /imfpush/v1/apps/{applicationId}/tags/* </code></td>
    <td>Get tags</td>
    <td>Manager, Reader, Writer</td>
  </tr>  
  <tr>
    <td><code>POST /imfpush/v1/apps/{applicationId}/subscriptions </code></td>
    <td>Create subscriptions</td>
    <td>Manager, Writer</td>
  </tr>  
  <tr>
    <td><code>DELETE /imfpush/v1/apps/{applicationId}/subscriptions </code></td>
    <td>Delete subscriptions</td>
    <td>Manager</td>
  </tr>  
  <tr>
    <td><code>GET /imfpush/v1/apps/{applicationId}/subscriptions </code></td>
    <td>Get Subscriptions</td>
    <td>Manager, Reader, Writer</td>
  </tr>    
  <tr>
    <td><code>POST /imfpush/v1/apps/{applicationId}/webhooks </code></td>
    <td>Create webhook</td>
    <td>Manager, Writer</td>
  </tr>  
  <tr>
    <td><code>PUT /imfpush/v1/apps/{applicationId}/webhooks/{webhookName} </code></td>
    <td>Update webhook</td>
    <td>Manager, Writer</td>
  </tr>  
  <tr>
    <td><code> DELETE /imfpush/v1/apps/{applicationId}/webhooks/{webhookName} </code></td>
    <td>Delete webhook</td>
    <td>Manager</td>
  </tr>  
  <tr>
    <td><code>GET /imfpush/v1/apps/{applicationId}/webhooks/* </code></td>
    <td>Get webhook</td>
    <td>Manager, Reader, Writer</td>
  </tr>    
</table>





