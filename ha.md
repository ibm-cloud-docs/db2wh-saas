---

copyright:
  years: 2014, 2024
lastupdated: "2024-11-08"

keywords:

subcollection: Db2whc

---

 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# High availability (HA) 
{: #ha}

The measure of a successful database solution is its availability. The architecture of {{site.data.keyword.dashdblong}} features multiple tiers of reliability, which allows for fast, automated recovery from any issues that the data warehouse might encounter.
{: shortdesc}




### Compute HA
{: #compute_ha}

Any node failure is immediately detected by the cloud provider's container service. The containers and pods that were running in the failed node are scheduled to a new node automatically by the HA process. The system is back to 100% normal operation after a short downtime.

### Storage HA
{: #storage_ha}

{{site.data.keyword.dashdbshort_notm}} uses highly-reliable block storage, designed to provide consistent performance and protect data integrity and availability through maintenance events and unplanned failures. Storage is provisioned and managed independently of compute.

### Network HA
{: #net_ha}

Network connections are made highly available by provisioning your service with a redundant network interface card (NIC). 

If the container service detects a network issue, pods and containers can automatically restart after a short downtime.

