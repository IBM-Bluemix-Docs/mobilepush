---

copyright:
  years: 2021
lastupdated: "2021-02-09"

keywords: push notifications, push notification, notifications, sysdig, monitoring

subcollection: mobilepush

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:java: .ph data-hd-programlang='java'}
{:ruby: .ph data-hd-programlang='ruby'}
{:c#: .ph data-hd-programlang='c#'}
{:objectc: .ph data-hd-programlang='Objective C'}
{:python: .ph data-hd-programlang='python'}
{:javascript: .ph data-hd-programlang='javascript'}
{:php: .ph data-hd-programlang='PHP'}
{:swift: .ph data-hd-programlang='swift'}
{:reactnative: .ph data-hd-programlang='React Native'}
{:csharp: .ph data-hd-programlang='csharp'}
{:ios: .ph data-hd-programlang='iOS'}
{:android: .ph data-hd-programlang='Android'}
{:cordova: .ph data-hd-programlang='Cordova'}
{:xml: .ph data-hd-programlang='xml'}

# Monitoring {{site.data.keyword.mobilepushshort}} service metrics with {{site.data.keyword.mon_full_notm}}
{: #push_sysdig}

{{site.data.keyword.mon_full}} is a third-party cloud-native, and container-intelligence management system that you can include as part of your {{site.data.keyword.cloud_notm}} architecture. Use it to gain operational visibility into the performance and health of your applications, services, and platforms. It offers administrators, DevOps teams, and developers full stack telemetry with advanced features to monitor and troubleshoot, define alerts, and design custom dashboards.
{: shortdesc}

To get started, you need to [Provision a Sysdig](https://{DomainName}/catalog/services/ibm-cloud-monitoring-with-sysdig) instance on your {{site.data.keyword.cloud_notm}} account. For more information on provisioning a Sysdig instance, see [here](https://cloud.ibm.com/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-provision).

Currently, {{site.data.keyword.mon_full_notm}} integration is available for {{site.data.keyword.mobilepushshort}} service deployments according to the following table:

| Deployment Region | Sysdig Region    |
|-------------------|------------------|
| `Dallas`          | `Dallas`         |
| `London`          | `London`         |
| `Tokyo`           | `Tokyo`          |
| `Sydney`          | `Sydney`         |
| `Washington DC`   | `Washington DC`  |
{: caption="Table 1. Sysdig regions" caption-side="top"}

## Opting in to and enabling {{site.data.keyword.mobilepushshort}} Sysdig metrics
{: #push_opt_in_metrics}

Before you can start using {{site.data.keyword.mobilepushshort}} Sysdig metrics, you must first opt in and then [enable platform metrics](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-platform_metrics_enabling). 

You can configure only one instance of the {{site.data.keyword.mon_full_notm}} service per region to collect platform metrics. 
* To configure the Sysdig instance, you must turn on the *platform metrics* configuration setting. 
* If a Sysdig instance in a region is already enabled to collect platform metrics, metrics from enabled-Sysdig services are collected automatically and available for monitoring through this instance. For more information about enabled-Sysdig services, see [{{site.data.keyword.cloud}} services](https://www.ibm.com/cloud/services).

To monitor platform metrics, check that the {{site.data.keyword.mon_full_notm}} instance is provisioned in the same region where the {{site.data.keyword.cloud_notm}} instance is provisioned.
{: important}

## Enabling platform metrics from the {{site.data.keyword.cloud_notm}} dashboard
{: #push_enable_platform_metrics}

Complete the following steps to configure platform metrics:

1. Log in to {{site.data.keyword.cloud_notm}}. The {{site.data.keyword.cloud_notm}} dashboard opens.
1. Click **View all** in the Resource summary section of the dashboard.
1. In the *Services* section, click the {{site.data.keyword.mobilepushshort}} instance that you plan to monitor. The {{site.data.keyword.mobilepushshort}} UI *Manage* page opens.
1. Click **Actions** > **Add monitoring** to configure *platform metrics* in the region of your {{site.data.keyword.mobilepushshort}} instance. 

   If the menu choices include the **Monitoring** option, then your instance is already configured for platform metrics. 
   {: note}
    
   ![Monitoring menu](images/pn-monitoring.png){: caption="Figure 1. Add monitoring" caption-side="bottom"}

1. Provision an instance of the {{site.data.keyword.mon_full_notm}} service.

   After you provision the Sysdig instance, the *Observabvility* page opens. To continue working with {{site.data.keyword.mobilepushshort}}, go back to the {{site.data.keyword.mobilepushshort}} UI.
   {: note}

## Viewing metrics
{: #push_view_metrics}

To monitor {{site.data.keyword.mobilepushshort}} metrics, you must launch the Sysdig web UI instance that is enabled for platform metrics in the region where your {{site.data.keyword.mobilepushshort}} instance is available.
{: important}

There are different options to launch the Sysdig web UI and monitor metrics that are described in the following section.

### Launching Sysdig web UI from the {{site.data.keyword.mobilepushshort}} dashboard
{: #push_view_metrics_opt1}

Complete the following steps to launch the Sysdig web UI from the {{site.data.keyword.mobilepushshort}} dashboard:

1. Log in to {{site.data.keyword.cloud_notm}}. The {{site.data.keyword.cloud_notm}} dashboard opens. 
1. Click **View all** in the Resource summary section of the dashboard.
1. In the *Services* section, click the {{site.data.keyword.mobilepushshort}} instance that you plan to monitor. The {{site.data.keyword.mobilepushshort}} UI *Manage* page opens.
1. Click the **Actions** menu, and select **Monitoring**.

   ![Monitoring menu](images/pn-monitoring1.png){: caption="Figure 2. Monitoring menu" caption-side="bottom"}

   A new tab in your browser opens and displays the *Default* dashboard named ** {{site.data.keyword.mobilepushshort}} ** within the context of your {{site.data.keyword.mobilepushshort}} instance.

### Launching Sysdig web UI from the Observability page
{: #pn_view_metrics_opt2}

Complete the following steps to launch the Sysdig web UI from the *Observability* page:

1. [Launch the Sysdig web UI](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-launch).
1. Click **DASHBOARDS**.
1. In the **Default Dashboards** section, expand **{{site.data.keyword.IBM_notm}}**.
1. Choose the {{site.data.keyword.mobilepushshort}} dashboard from the list.

   To access your deployment's Sysdig dashboard from Sysdig, it's in the sidebar, under {{site.data.keyword.IBM_notm}}.

   ![{{site.data.keyword.mobilepushshort}} dashboard](images/mp-dashboard-link.png){: caption="Figure 3. {{site.data.keyword.mobilepushshort}} dashboard" caption-side="bottom"}

   Next, change the scope or make a copy of the *Default* dashboard to monitor an {{site.data.keyword.mobilepushshort}} service instance.  

## {{site.data.keyword.mobilepushshort}} metrics details
{: #pn_metrics_details}

The following tables describe the specific metrics provided by {{site.data.keyword.mobilepushshort}}. 

| Metadata          | Description                                                                              |
|-------------------|------------------------------------------------------------------------------------------|
| `Metric Name`     | `ibm_imfpush_message_sent_count`                                                         |
| `Metric Type`     | `counter`                                                                                |
| `Value Type`      | `None`                                                                                   |
| `Segment By`      | `ibm_ctype`, `ibm_service_name`, `ibm_location`, `ibm_scope`, `ibm_service_instance`     |
{: caption="Table 2. {{site.data.keyword.mobilepushshort}} metrics" caption-side="top"}

