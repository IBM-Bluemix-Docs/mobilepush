---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-11"

keywords: push notifications, notification provider credentials

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 第 2 步：获取通知提供程序凭证
{: #push_step_1}

要设置 {{site.data.keyword.mobilepushshort}} 服务，需要从推送通知提供程序处获取所需的凭证。 

## 对于 Android
{: #push_step_1_android}

Firebase 云消息传递 (FCM) 是用于向 Android 设备、Google Chrome 浏览器和 Chrome Apps & Extensions 传递推送通知的网关。要在控制台上设置 {{site.data.keyword.mobilepushshort}} 服务，您需要获取 FCM 凭证（发送方标识和 API 密钥）。 

API 密钥以安全方式存储，并由 {{site.data.keyword.mobilepushshort}} 服务用于连接到 FCM 服务器，而发送方标识（项目编号）由客户机端的适用于 Google Chrome 和 Mozilla Firefox 的 Android SDK 和 JS SDK 使用。 

要设置 FCM 并获取凭证，请完成以下步骤：

1. 访问 [Firebase 控制台 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.firebase.google.com/?pli=1){: new_window}。这需要 Google 用户帐户。 
2. 选择**添加项目**。 
3. 在“创建项目”窗口中，提供项目名称，选择国家/地区并单击**创建项目**。
4. 在导航窗格中，选择**设置** > **项目设置**。
5. 选择“云消息传递”选项卡，以获取项目凭证 -“服务器 API 密钥”和“发送方标识”。请注意，FCM 中列出的“服务器密钥”与“服务器 API 密钥”相同。
   
	![获取 FCM 的凭证](images/FCM_settings_2.jpg "选择了“云消息传递”选项卡的“设置”页面，其中显示项目凭证")

您可能还需要生成 `google-services.json` 文件。完成以下步骤：

1. 在 Firebase 控制台中，单击**项目设置**图标。
    
	![Firebase 项目设置](images/FCM_settings_6.jpg "选择了“项目设置”选项的 Firebase 控制台")

2. 在“您的应用程序”窗格的“常规”选项卡中选择**添加应用程序**或**将 Firebase 添加到您的 Android 应用程序**图标。
    
3. 在“将 Firebase 添加到您的 Android 应用程序”窗口中，首先添加 **com.ibm.mobilefirstplatform.clientsdk.android.push** 作为程序包名称。“应用程序昵称”字段为可选字段。单击**注册应用程序**。
 
    
	![将 Firebase 添加到您的 Android 窗口](images/FCM_1.jpg "“输入应用程序详细信息”选项卡上的“将 Firebase 添加到您的 Android 应用程序”屏幕，其中显示程序包和应用程序名称字段")

4. 现在，通过在“将 Firebase 添加到您的 Android 应用程序”窗口中输入应用程序的程序包名称，包含此程序包名称。“应用程序昵称”字段为可选字段。单击**注册应用程序**。
请查看以下示例：

	![添加应用程序的程序包名称](images/FCM_settings_4.jpg "“注册应用程序”选项卡上的“将 Firebase 添加到您的 Andriod 应用程序”屏幕，其中显示程序包和应用程序名称字段")

5. 生成 `google-services.json` 文件。 

一旦获取了 FCM 凭证并生成了 `google-services.json` 文件，下一步是[创建服务实例](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2)。

Google 已弃用 GCM，并且已将“云消息传递”与 Firebase 集成。您必须将 Android 上的 GCM 客户机应用程序迁移到 FCM。
{: note}

## 对于 iOS
{: #push_step_1_ios}

对于 iOS 设备和应用程序，通过 Apple 推送通知服务 (APNs)，应用程序开发者可以将远程通知从 IBM Cloud 上的 {{site.data.keyword.mobilepushshort}} 服务实例（提供者）发送到 iOS 设备和应用程序。消息会发送到设备上的目标应用程序。 

您需要获取并配置 APNs 凭证。APNs 证书由 {{site.data.keyword.mobilepushshort}} 服务安全管理，在连接到 APNs 服务器（提供者）时需要使用该证书。


### 注册应用程序标识
{: #push_step_1_ios_2}

应用程序标识（捆绑标识）是用于标识特定应用程序的唯一标识。每个应用程序都需要应用程序标识。像 {{site.data.keyword.mobilepushshort}} 服务这类的服务都是配置给应用程序标识的。

1. 请确保您具有 [Apple Developer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com/){: new_window} 帐户。这是必备的先决条件。

2. 转至 [Apple Developer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com){: new_window} 门户网站，单击 **Member Center**，然后选择 **Certificates, Identifiers & Profiles**。
3. 转至 **Identifiers** > **App IDs** 部分。
4. 在 **Registering App IDs** 页面中 App ID Description 下的 Name 字段中，提供应用程序名称。例如：ACME Push Notifications。
5. 为 App ID Prefix 提供字符串。  
6. 对于 App ID Suffix，选中 **Explicit App ID**，并提供 Bundle ID 值。建议提供逆向域名样式的字符串。例如：`com.ACME.push`。
7. 选中 **Push Notifications** 复选框，然后单击 **Continue**。
8. 完成设置，然后单击 **Register** > **Done**。

现在，您的应用程序标识已注册。 

   ![已注册的应用程序标识](images/push_ios_register_appid.jpg "选择了应用程序标识导航选项的 Apple 开发人员门户网站屏幕，其中显示应用程序标识")
  

### 创建开发和分发 APNs SSL 证书
{: #push_step_1_ios_3}

在获取 APNs 证书之前，必须首先生成一个证书签名请求 (CSR)，然后将其提交给 Apple（认证中心 (CA)）。CSR 中包含您公司的标识信息，以及您用于签署 Apple 推送通知的公用密钥和专用密钥信息。然后，在 iOS 开发者门户网站上生成 SSL 证书。该证书与其公用密钥和专用密钥一起存储在“钥匙串访问”中。

您可以在两种模式下使用 APN： 

* 用于开发和测试的沙箱模式。
* 在 App Store（或其他企业分发机制）中分发应用程序时的生产模式。

必须分别针对开发环境和分发环境获取证书。证书与接收远程通知的应用程序的应用程序标识相关联。对于生产方式，最多可创建两个证书。IBM Cloud 使用证书与 APNs 建立 SSL 连接。

<!-- Create a development and distribution SSL certificate. -->

1. 转至 [Apple Developer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com){: new_window} 网站，单击 **Member Center**，然后选择 **Certificates, Identifiers & Profiles**。
2. 在 **Identifiers** 区域中，单击 **App IDs**。
3. 在应用程序标识列表中，选择您的应用程序标识，然后选择 **Edit**。
4. 选中 **Push Notifications** 复选框，然后：
	-  在 Development SSL certificate 窗格中，单击 **Create Certificate...**
	-  在 Production SSL certificate 窗格中，单击 **Create Certificate...**

	![推送通知 SSL 证书](images/certificate_createssl.jpg "“编辑应用程序标识”屏幕，其中显示已选择了 Push Notifications 选项、开发 SSL 证书和生产 SSL 证书选项")

5. 在 **About Creating a Certificate Signing Request (CSR) screen** 显示时，启用 Mac 上的**钥匙串访问**应用程序以创建证书签名请求 (CSR)。单击 **Continue**。
6. 对于 Upload CSR file 选项，单击 **Choose File**，然后选择 `CertificateSigningRequest.certSigningRequest` 文件。 
7. 单击 **Continue**。
8. 在 Download, Install and Backup 窗格中，单击 **Download**。这将下载 `aps_development.cer` 文件。
	
	![下载证书](images/push_certificate_download.jpg "“安装和备份”页面，其中显示已选择了“下载”按钮")	
	
9. 从菜单选择**钥匙串访问 > 证书助理 > 从证书颁发机构请求证书…** 
10. 在**证书信息**中，输入与您的 App Developer 帐户相关联的电子邮件地址和常用名称。提供有意义的名称来帮助您识别此为开发（沙箱）证书还是分发（生产）证书；例如，_sandbox_apns_certificate_ 或 _production_apns_certificate_。
11. 选择**另存到磁盘**，以将 `.certSigningRequest` 文件下载到桌面，然后单击**继续**。
12. 在**另存为**菜单选项中，对 `.certSigningRequest` 文件命名并单击**保存**。
13. 单击**完成**。您现在就有一个 CSR 了。
14. 返回 **About Creating a Certificate Siging Request (CSR)** 窗口并单击 **Continue**。 
15. 在 **Generate** 屏幕中，单击 **Choose File...**，选择保存在桌面上的 CSR 文件。然后，单击 **Generate**。


	![生成证书](images/generate_certificate.jpg "用于生成证书的“证书、标识和个人档案”页面，其中选择了“选择文件”选项")
16. 证书准备就绪后，单击 **Done**。
17. 在 **Push Notifications** 屏幕中，单击 **Download** 以下载证书，然后单击 **Done**。
 
	
	![下载证书](images/certificate_download.jpg "“编辑应用程序标识”屏幕，其中显示开发 SSL 证书的“撤销”和“下载”按钮")

18. 在 Mac 上，转至**钥匙串访问 > 我的证书**，然后找到新安装的证书。双击该证书，以将其安装到“钥匙串访问”中。
19. 选择证书和专用密钥，然后选择**导出**，以将证书转换成个人信息交换格式（`.p12` 格式）。


	![导出证书和密钥](images/keychain_export_key.jpg "“我的证书”页面，其中显示证书上的右键单击选项，并突出显示“导出”菜单选项")
20. 在**存储为**字段中，为证书提供有意义的名称。例如，`sandbox_apns.p12_certifcate` 或 `production_apns.p12`，然后单击**保存**。

	
	![导出证书和密钥](images/certificate_p12v2.jpg "“另存为”屏幕，其中显示“另存为”字段的文本输入")
21. 在**输入密码**字段中，输入用于保护导出项的密码，然后单击**确定**。您可以使用此密码，在 Push Notifications 服务控制台上配置 APNs 设置。

	
	![导出证书和密钥](images/export_p12.jpg "密码和验证字段，用于输入密码以保护导出的项目")
22. **Key Access.app** 会提示您从**密钥串**屏幕导出密钥。输入 Mac 的管理员密码，以允许系统导出这些项，然后选择**总是允许**选项。这将在桌面上生成一个 `.p12` 证书。


### 创建开发供应概要文件
{: #create-push-credentials-dev-profile}

供应概要文件与应用程序标识一起来确定哪些设备可以安装并运行您的应用程序，以及您的应用程序可以访问哪些服务。对于每个应用程序标识，都可创建两个供应概要文件：一个用于开发，另一个用于分发。Xcode 使用开发供应概要文件来确定允许哪些开发者构建应用程序，以及允许哪些设备在应用程序上进行测试。

请确保您已执行以下操作：注册应用程序标识，针对 {{site.data.keyword.mobilepushshort}} Service 启用该标识，然后将其配置为使用开发和生产 APNs SSL 证书。

创建开发供应概要文件，如下所示：

1. 转至 [Apple Developer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com){: new_window} 门户网站，单击 **Member Center**，然后选择 **Certificates, Identifiers & Profiles**。
2. 转至 [Mac Developer Library ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com/library/mac/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW62site){: new_window}，滚动至 **Creating Development Provisioning Profiles** 部分，然后遵循指示创建开发概要文件。
**注**：配置开发供应概要文件时，请选择以下选项：
	* **iOS App Development**
	* **对于 iOS 和 watchOS 应用程序**


### 创建应用商店分发供应概要文件
{: #create-push-credentials-apns-distribute_profile}

使用应用商店供应概要文件可提交应用程序以分发到 App Store。

1. 转至 [Apple Developer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com){: new_window} 门户网站，单击 **Member Center**，然后选择 **Certificates, Identifiers & Profiles**。
2. 双击所下载的供应概要文件，以将其安装到 Xcode 中。

获取凭证后，下一步是[配置服务实例](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2)。

## 对于 Web 浏览器和 Chrome Apps & Extensions
{: #configure-credential-for-browsers}

IBM {{site.data.keyword.mobilepushshort}} 服务扩展了功能，可以向浏览器和 Chrome Apps & Extensions 发送通知。

{{site.data.keyword.mobilepushshort}} 服务需要 Web 站点 URL 或 Web 站点的域名来识别需要允许的请求。 

例如：`https://www.acmebanks.com`

{{site.data.keyword.mobilepushshort}} 服务实例一次仅支持一个域名。因此，确保针对 Chrome、Firefox 和 Safari 设置相同的值。Chrome 和 Safari 浏览器需要针对 Web 推送进行额外的配置。您需要 FCM API 密钥，因为 FCM 端点用于在 Chrome 中传递消息。 

要为 Chrome、Firefox 浏览器和 Chrome Apps & Extensions 设置该服务，请参阅[配置服务实例](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2)。


### 针对 Safari Web 推送进行配置 
{: #configure-safari}

在 Safari 上受支持的 {{site.data.keyword.mobilepushshort}} 服务是 10.0。您需要通过 Apple Developer 帐户生成证书，然后才能配置浏览器来接收通知。

#### 生成证书
{: #certificate-generation}

确保您已拥有 Apple Developer 帐户。您需要注册 Web 站点推送标识，并生成证书，以配置您的 Safari 浏览器来接收通知。以下步骤将帮助您开始使用该功能。

1. 在 Apple Developer Member 中心，单击 **Certificates, ID & Profiles**。 
2. 单击 **Identifiers**，然后单击 **Website Push IDs**。
3. 通过选择加号图标来选择创建新条目。![Push Notifications 控制台](images/safari_1.jpg "显示 Website Push IDs 导航选项的 Apple 开发人员门户网站")

4. 在 Register Website Push ID 面板中，提供相应的 Web 站点推送标识描述和识别标识。建议使用反向域名格式，以 `web` 开头。例如：`web.com.acmebanks`。
5. 注册 Web 站点推送标识。您现在已有 Web 站点推送标识 
6. 选择**编辑**以创建要用于 Web 站点推送标识的证书。
7. 在证书信息的“证书助理”窗口中，提供您的电子邮件标识和通用名称。将认证中心电子邮件地址保留为空白。
8. 单击**保存到磁盘**并选择**继续**。
9. 选择将证书保存到相应的文件夹。
10. 向导中提示时选择在磁盘上创建的 `.certSigningRequest`，以生成证书。请确保您已下载以 `.cer` 格式创建的 Web 站点推送证书。
11. 在“钥匙串访问”工具中打开证书。右键单击并导出为 p12 证书。记下在生成 p12 证书时提供的密码。

生成证书后，下一步是[配置服务实例](/docs/services/mobilepush?topic=mobile-pushnotification-push_step_2)。
