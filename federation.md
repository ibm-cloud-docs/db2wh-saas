---

copyright:
  years: 2014, 2019
lastupdated: "2018-07-18"

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

# Data virtualization (federation)
{: #data_virt_fed}

Db2 data virtualization (also known as federation) is supported by {{site.data.keyword.dashdbshort_notm}}. Data virtualization gives you single-query access to all of your data that is on multiple distributed databases anywhere in your organization. You can access data that is on any of your Db2 or Informix data sources, both in the cloud and on premises. 
{: shortdesc}

This function is supported on all versions of {{site.data.keyword.dashdbshort_notm}}. 

## Use Cases
{: #use_cases}

### Consolidate data sources

By federating your data sources that are located both in the cloud and on premises anywhere in your organization, your virtualized data appears to be retrieved from a single source. Data virtualization eliminates the burdensome and costly data migration process, giving you the ability to analyze all of your data efficiently and cost effectively.



### Attach to Db2 on Cloud

Users of products in the Db2 family can federate data from {{site.data.keyword.Db2_on_Cloud_short}} and {{site.data.keyword.dashdbshort_notm}} databases. From a common interface to access the data, you can easily add, query, and analyze your data without complex ETL processes and without any additional code.







### Increase database capacity beyond fixed limits

Federation gives you the ability to increase the capacity of an on-premises database by federating with a database on the cloud. Data virtualization in this case is a great option if your on-premises database is running out of storage. Increasing the capacity of a database with federation is useful for new development because developers don't need to change a database already in production. You can also federate between two {{site.data.keyword.dashdbshort_notm}} databases to increase the database capacity beyond the current limits of the Flex plan.



## Getting started
{: #gtng_strtd}

The following steps are an example of how you go about federating your disparate data sources to appear as if the data is retrieved from a single source. The following example illustrates the federation of two {{site.data.keyword.dashdbshort_notm}} databases:

### On the Db2 Warehouse as a Service target machine
{: #targ}

Host name: targetdotcom

1. Create a table `testdata` in schema `admin2`.

2. From the {{site.data.keyword.dashdbshort_notm}} console, load the `testdata` table with data as user `admin2` with password `YYYY`.

### On a Db2 Warehouse as a Service machine being used as a federation source
{: #fed_src}

From the {{site.data.keyword.dashdbshort_notm}} console:



1. Create a server to talk to the target machine:<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   For example:<br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. Create the user mapping for admin2:<br/>
   `create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   For example:<br/>
   `create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. Create a nickname for the database:<br/>
   `create nickname <nickname> for <server_name>.<schema_name>.<table_name>`

   For example:<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. Test that you can pull data from the target server:<br/>
   `select * from <nickname>`

   For example:<br/>
   `select * from ntest1`

## Additional information

For more information about data virtualization (federation), see: [Federation](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:external}.

For information about the data sources supported by federation, see: [Federation Supported Data Sources](https://www.ibm.com/support/docview.wss?uid=swg27050561){:external}.
