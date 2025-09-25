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

# Loading data from IBM Cloud Object Storage
{: #load_cos}

## External Tables
{: #cos_et}

You can load data from {{site.data.keyword.Bluemix_notm}} Object Storage (COS) into {{site.data.keyword.dashdblong}} by using the built-in External Tables functionality. 
{: shortdesc}

Here's an example SQL statement that inserts COS data into a {{site.data.keyword.dashdbshort_notm}} table by using External Tables:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )
```
{: codeblock}

For {{site.data.keyword.Bluemix_notm}} Object Storage, to create HMAC credentials when creating new service credentials, specify {"HMAC:true"} in the *Add Inline Configuration Parameters* field.
{: note}




## Db2 LOAD utility
{: #cos_load}

You can also load data from {{site.data.keyword.Bluemix_notm}} Object Storage (COS) into {{site.data.keyword.dashdbshort_notm}} by using the built-in Db2 **LOAD** utility. 

Here’s an example SQL statement that uses the Db2 LOAD utility to load COS data into {{site.data.keyword.dashdbshort_notm}}:

```
CALL SYSPROC.ADMIN_CMD('LOAD FROM "S3::<cos-endpoint-url>::<cos-access-key-ID>::<cos-secret-access-key>:
:<cos-bucket-name>::<path-to-data-file>" OF <filetype> <additional-load-options> INTO <table-name>)
```
{: codeblock}

For more information about the Db2 LOAD utility, see: [LOAD command](https://www.ibm.com/docs/en/db2/11.5?topic=commands-load){: external}.
