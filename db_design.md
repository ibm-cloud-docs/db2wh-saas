---

copyright:
  years: 2014, 2020
lastupdated: "2020-04-27"

keywords:

subcollection: db2wh-saas

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

# Database design best practices
{: #db_design_bp}

{{site.data.keyword.dashdblong}} is a managed cloud data warehouse service that is preconfigured for optimal performance. The following section provides best practices for {{site.data.keyword.dashdbshort_notm}} database design.
{: shortdesc}

## Design tips
{: #db_design_tips}

- In {{site.data.keyword.dashdbshort_notm}}, all tables are column organized by default for optimal performance on analytical workloads. While you can create row-organized tables, it is strongly recommended that you create all tables as column organized for good performance on analytical queries.

- As a SaaS offering, {{site.data.keyword.dashdbshort_notm}} automatically manages table spaces, buffer pools, and database partition groups to ensure optimal performance. When you create your {{site.data.keyword.dashdbshort_notm}} instance, you'll find the following database objects created by default:

  - One regular table space: `USERSPACE1` (32K page size)
  - One temporary table space: `TEMPSPACE1` (32K page size)
  - One buffer pool: `IBMDEFAULTBP` (32K page size)
  - One database partition group: `IBMDEFAULTGROUP`

  It is strongly recommended to not create additional table spaces, temporary table spaces, buffer pools, or database partition groups.

- If you’re using any one of the {{site.data.keyword.dashdbshort_notm}} [multi-partitioned plans](/docs/Db2whc?topic=Db2whc-about#plans_cfgs), you can optimize performance by defining a good set of table distribution keys. A good distribution key distributes data evenly across database partitions so that all of your database partitions can help process data for your queries. A poorly-chosen distribution key results in data skew. This means that data is stored unevenly across database partitions such that only a subset of data partitions participate in the processing while the rest remain idle. For more information about distribution keys, see [Distribution keys for multi-partitioned plans](/docs/Db2whc?topic=Db2whc-distribution_keys).

  If you’re using a single-partitioned plan, there’s no need to worry about distribution keys because all of the data is stored on one data partition.
  {: note}



- The Db2 engine includes many registry and environment variables, and database configuration parameters. As a SaaS offering, IBM Db2 Warehouse SaaS is deployed with preconfigured variables and parameters to optimize performance.

  Changing any of these settings might result in adverse effects on database operation or performance and is therefore **strongly discouraged**.

  If you think your system might benefit from changes to some registry variables, environment variables, or database configuration parameters, open a support case to request guidance from our service experts.

  Please note that IBM decides on any request for parameter customization on a case-by-case basis and may deny the request if it is not supported on your plan/instance.

  Some of the customizations that can be requested include:

  * **Time zone**  
    The default time zone for your instance is **UTC**. You may request to modify it to a time zone of your choosing.

  * **LOGSECOND**  
    This configuration parameter specifies the number of **secondary transaction log files** that your database instance can dynamically allocate and use when the primary log files are exhausted.

    By default, IBM Db2 Warehouse SaaS calculates an optimal value for `LOGSECOND` based on the instance block storage size. You may request an increase in the value of `LOGSECOND` if the block storage associated with your Db2 Warehouse SaaS instance is large enough to support the increase.

    Even when the value of `LOGSECOND` is updated based on your request, subsequent changes in block storage size can result in changes to the value of `LOGSECOND`:

    - During a **storage scale-up**, the value of `LOGSECOND` may increase if the customer-provided value falls short of IBM's calculated value.
    - During a **storage shrink**, the value of `LOGSECOND` may be capped to a lower value if the customer-provided value cannot be supported by the block storage.

    **Effective value of `LOGSECOND` on your instance = greater of 1 & 2 below:**

    1. IBM calculated optimal value based on your block storage size  
    2. Customer requested value  
       *(Capped based on your instance block storage capacity)*
