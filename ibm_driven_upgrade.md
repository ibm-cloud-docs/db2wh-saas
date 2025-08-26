---

copyright:
  years: 2024, 2025
lastupdated: "2025-08-26"

keywords:

subcollection: db2wh-saas

---

# IBM Driven Upgrade

{: #ibm_driven_upgrade}

 
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

Outdated instance versions may be automatically upgraded to the next generation (Gen 3) of {{site.data.keyword.dashdblong}} during the scheduled maintenance window. This implicit upgrade ensures all environments are moved to Gen 3 and benefit from the latest enhancements with minimal manual intervention.

## Move Data from Block to Cloud Object Storage

{: #migr_move}

To start saving on storage costs, you will need to move eligible data from block storage to cloud object storage and then shrink the freed block storage. The limitations on what type of tables are eligible can be found within this documentation. There are two ways to move tables:

1. Via the service console, utilizing the Table Explorer, where a single table at a time can be moved to the pre-created cloud object storage tablespace.

2. Via a command line tool, which can automate bulk table moves and more. Details on how to install and use the tool can be found here.

## Shrink Block Storage

{: #migr_shrink}

After tables have been moved to cloud object storage, the block storage will need to be shrunk. The shrink operation can be performed as many times as required, however keep in mind that it is an offline operation and requires downtime. The shrink operation can be initiated via the service console as shown here.
For information about posting questions on a forum or opening a support ticket, 

## What should I expect after the upgrade?

{: #q_after_ibm_driven_upgrade}

The implicit upgrade upgrades your system to the new generation of {{site.data.keyword.dashdbshort_notm}} and VPC Gen2 infrastructure, and also updates the database to the latest version automatically. This ensures that you immediately benefit from all new features introduced in the latest database version and no separate update action is required. Both v4 and v5 of the {{site.data.keyword.dashdbshort_notm}} REST API will remain fully functional after the upgrade.

After the upgrade, the Web Console URL will be updated. Please note the following changes:

- **Before Upgrade**  
  `https://<hostname>/console`

- **After Upgrade**  
 Follow these steps to open the {{site.data.keyword.dashdbshort_notm}}  web console:
  1. Navigate to the [IBM Cloud Resources list](https://cloud.ibm.com/resources).
  2. Under the **Databases** section, select your Db2 Warehouse database.
  3. Click the **Go to UI** button to launch the IBM Db2 Warehouse SaaS web console.

Please make sure to update any bookmarks, scripts, or integrations that rely on the old URL.
{: note}

For most customers, you can resume working with your data as before. However, certain customers may encounter specific circumstances requiring further actions:

*Private Connections from IBM Cloud VPC:* If you have workloads running on IBM Cloud VPC, you can leverage private connectivity (Private Link) to connect securely to your Db2 Warehouse instances using IBM Cloud’s private network. Follow the steps outlined [here](https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-connect_options#connecting-to-db2-warehouse-on-cloud-with-private-link).

To enable private connectivity:

   * First, enable private connectivity through the console.
   * Then, create a *Virtual Private Endpoint Gateway* on your VPC. The private endpoint and port will be provided in the Connections section of the console.

Private connectivity is a *regional service*, meaning that the Virtual Private Endpoint Gateway must be created in the same region as your Db2 Warehouse on Cloud instance.
{: note}

*VPN Connectivity:* If you currently connect via VPN, follow the instructions in the [VPN Connectivity guide](https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-connect_options#vpn) to ensure proper setup after the upgrade.
