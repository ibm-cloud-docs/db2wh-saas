---

copyright:
  years: 2014, 2025
lastupdated: "2025-09-25"

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
{:video: .video}

# Loading data from Amazon S3
{: #load_s3}

## External Tables
{: #aws_s3_et}

You can load data from Amazon S3 into {{site.data.keyword.dashdblong}} by using the built-in External Tables functionality. 
{: shortdesc}

Here’s an example SQL statement that inserts Amazon S3 data into a {{site.data.keyword.dashdbshort_notm}} table by using External Tables:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3.amazonaws.com', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )
```
{: codeblock}




## Db2 LOAD utility
{: #aws_s3_load}

You can also load data from Amazon S3 into {{site.data.keyword.dashdbshort_notm}} by using the built-in Db2 **LOAD** utility. 

Here’s an example SQL statement that uses the Db2 LOAD utility to load Amazon S3 data into {{site.data.keyword.dashdbshort_notm}}:

```
CALL SYSPROC.ADMIN_CMD('LOAD FROM "S3::<s3-endpoint-url>::<s3-access-key-ID>::<s3-secret-access-key>:
:<s3-bucket-name>::<path-to-data-file>" OF <filetype> <additional-load-options> INTO <table-name>)
```
{: codeblock}

For more information about the Db2 LOAD utility, see: [LOAD command](https://test.cloud.ibm.com/docs/Db2whc?topic=Db2whc-load_cos){: external}.
