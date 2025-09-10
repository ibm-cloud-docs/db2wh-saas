---

copyright:
  years: 2014, 2020
lastupdated: "2022-02-23"

keywords:

subcollection: db2wh-saas

---

# Logging and Monitoring

{: #logg_mon}

 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:video: .video}

Open a Support Case to enable this feature on your instance. {: important}

When this feature is enabled, if you already have a Log Analysis with LogDNA configured as Platform Logs, you will see a large amount of messages from your Db2 Warehouse on Cloud instances. See the following sections on how to limit logging. {: note}

## Platform logs overview

{: #platform_log}

The service can be provisioned from its [catalog page](https://cloud.ibm.com/catalog/services/logdnaat?callback=%2Fobserve%2Factivitytracker%2Fcreate){: external} or from an existing [Observability Dashboard](https://cloud.ibm.com/login?redirect=%2Fobserve%2Factivitytracker).

The Log Analysis with LogDNA service has a Lite plan that is free to use, but it only offers streaming events. To take advantage of the tagging, export, retention, and other features, you need to use one of the paid plans.

After you provision the Log Analysis with LogDNA service, messages from db2diag.log are automatically forwarded from all of your Db2 Warehouse on Cloud deployments in the same region.

## Enabling platform logs from the Logging dashboard

{: #enable_platform}

To configure a logging instance, you must set on the platform logs configuration setting. If your logging instance in a region is already enabled to collect platform logs, the `db2diag.log` from Db2 Warehouse on Cloud are collected automatically and available for analysis through your instance.

If you have multiple Db2 Warehouse on Cloud instances, all of the `db2diag` logs will be sent to a single LogAnalysis w/ LogDNA instance in the same region. That instance is the only instance that can be configured as Platform Logs. Refer to https://cloud.ibm.com/docs/log-analysis?topic=log-analysis-config_svc_logs on how to configure your LogAnalysis w/ LogDNA to accept Db2 Warehouse on Cloud logs. {: important}

## Viewing logs

{: #view_logs}

You can access Log Analysis with LogDNA through the Observability tab of your deployment's Manage page. The Manage Logging button links to the main list of all LogAnalysis instances in your IBM Cloud account. Select the instance where you set your database logs to be forwarded. Click Open dashboard to view the messages.

The `dashdb` prefix is used to identify log entries by message ID. After the message is forwarded to the service, each message can be expanded to a detailed view by clicking the arrow to the left of the time stamp.

IBM Log Analysis service offers searching, filtering, and export of events so you can customize retention for your use case. You can also use it to configure alerts.

If you have multiple Db2 Warehouse on Cloud instances flowing into LogAnalysis w/ LogDNA, you can filter Source to get instance(s) [CRN](https://cloud.ibm.com/docs/account?topic=account-crn) you would like to observe. You can view your instance's CRN by clicking on the instance in your [Resource List](https://cloud.ibm.com/resources). You can filter App with dashdb for messages from Db2 Warehouse on Cloud. {: note}

## Control logging infrastructure costs by customizing what logs to manage through IBM Log Analysis

{: #control_log}

`db2diag.log` can produce a high volume of messages which can result in unexpected cost. We recommend that you leverage the Exclusion Rules feature to limit the messages to your IBM Log Analysis instance.

You can access the Exclusion Rules feature through the Usage tab of your IBM Log Analysis dashboard. Create a rule by clicking Add Rule. Complete the form to start controlling your cost for this instance.

## Suggested Regions

| Deployment region | LogAnalysis region |
|----------|-----------|
| Dallas | us-south |
| Washington | us-east |
| Frankfurt | eu-de |
| London | eu-gb |
| Sydney | au-syd |
| Tokyo | jp-tok |
| São Paulo | br-sao |
| Toronto | ca-tor |
{: caption="LogAnalysis regions" caption-side="top"}

[def]: https://cloud.ibm.com/docs/account?topic=account-crn
