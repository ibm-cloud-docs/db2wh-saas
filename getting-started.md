---

copyright:
  years: 2014, 2025
lastupdated: "2025-03-07"

keywords:

subcollection: Db2whc

---

 
{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
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

# Getting started with IBM Db2 Warehouse as a Service
{: #getting-started}

You can provision an instance of {{site.data.keyword.dashdbshort_notm}} through the [IBM Cloud catalog](https://cloud.ibm.com/catalog/db2-warehouse). Create a [free account](https://cloud.ibm.com/registration?target=%2Fcatalog%2Fservices%2Fdb2-warehouse) and get an IBM Cloud credit of $200 that you can use towards {{site.data.keyword.dashdbshort_notm}}. You can also get a $1000 promo code to try out {{site.data.keyword.dashdbshort_notm}} by following the instructions [here.](https://cloud.ibm.com/registration/premium1?target=/catalog/services/db2-warehouse&cm_mmca1=000030YW&cm_mmca2=DAFWW&S_PKG=ov34433&uucid=0040c3e10b80999b&cm_sp=cloud-product---onpagenav-ibmcloudplatform_db2-warehouse-on-cloud---bm_nsl_customize_leadspace)

After creating the {{site.data.keyword.dashdbshort_notm}} service, you can create a user name and password by clicking the **Service credentials** tab on your service page and selecting **New credential**.

While logged in as the **IAM** user that provisioned the instance, you can log into the web console by clicking on the **Go to UI** button on the **Manage** tab. In order to activate and administer Q Replication, you must login as a **IAM** user with with appropiate priveleges.

You can create database/JDBC users, which you will use to connect to the database, by navigating to the **Administration** --> **User Management** panel. Additionally, you may want to give admin access to an IAM user to allow them to use console administration functions such as user management, backup, and restore. Before you can add an IAM user in the console, you must first give the user access to the service in IAM". For more information, see [Identity and access management (IAM) on IBM Cloud](https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-iam).












