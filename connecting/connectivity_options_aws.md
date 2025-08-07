---

copyright:
  years: 2014, 2019
lastupdated: "2024-07-31"

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

# Connectivity options on Amazon Web Services
{: #connect_options_aws}

{{site.data.keyword.dashdblong}} offers secure connectivity options for your application connection requirements.  
{: shortdesc}

For application connections, do not use IP addresses to connect to the {{site.data.keyword.dashdbshort_notm}} instance, as the IP addresses resolved from the hostname may change. Use hostnames to reference your connection properties where it is available.
{: important}

## Connecting to Db2 Warehouse SaaS with Amazon Web Services PrivateLink
{: #PrivateLink}

[Amazon Web Services (AWS) PrivateLink](https://aws.amazon.com/privatelink/){: external} gives you the ability to securely and privately connect to a {{site.data.keyword.dashdbshort_notm}} instance that is deployed on AWS from your own AWS VPCs, services, and applications. With AWS PrivateLink, traffic between {{site.data.keyword.dashdbshort_notm}} and your AWS VPCs, services, and applications does not traverse the public internet.

If you'd like to use AWS PrivateLink with {{site.data.keyword.dashdbshort_notm}}, complete the following steps:

1. Create an AWS principal to access {{site.data.keyword.dashdbshort_notm}}. The AWS principal can be AWS accounts, IAM users, or IAM roles.

2. Open the console, navigate to **Settings → Access restriction**, then:
   - Enable **Private Endpoints**.
   - Add the principal created in step 1 to the allowlist
  
3. In the **Db2 Warehouse as a Service console**, go to the **Connections** tab to get the PrivateLink service name.  
   The service name will follow this format:  
   `com.amazonaws.vpce.<region>.<service-name>`

4. From your **AWS account**:
   - Open the **AWS Console** and go to the **VPC** tab.
   - Click on **Endpoints**, then select **Create endpoint**.
   - Choose **PrivateLink Ready partner services**.
   - Enter the **service name** retrieved in step 3.
   - Verify the service, then proceed to **create the endpoint**.


## Connecting to the private web console of {{site.data.keyword.dashdbshort_notm}}
{: #PrivateWebConsole}

- When you enable private endpoint, the private web console becomes available. When private endpoint is enabled, you can still access a lite version of the web console to get connection information.
- Should you want to use the private web console, use the same AWS endpoint created from the above steps, but ensure that TCP traffic is allowed through port 8443 on your VPC.
    

#### Considerations and limitations

- AWS PrivateLink currently supports only TCP traffic. Tools that rely on UDP traffic are not supported by PrivateLink. To load data, load directly from Amazon S3 into {{site.data.keyword.dashdbshort_notm}}. See [Loading data from Amazon S3](/docs/Db2whc?topic=Db2whc-load_s3).

  Extra charges might apply when you transfer data by using the public endpoint.
  {: note}

- You must create the Endpoint Service for accessing {{site.data.keyword.dashdbshort_notm}} in the same AWS region where the {{site.data.keyword.dashdbshort_notm}} instance is deployed. To access your instance from other AWS regions, you can use VPC Peering. See [Example: Services Using AWS PrivateLink and VPC Peering](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-peer-region-example.html){: external} or setup a AWS Transit Gateway.

- For the current generation of plans on AWS, connectivity to the web UI is available only over the public network, even if you have enabled PrivateLink. This restriction is temporary, and will be removed in an upcoming update.

For more information about AWS PrivateLink, see [Interface VPC Endpoints (AWS PrivateLink)](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html){: external}.

## Using IP Allowlists with your Instance

An **allowlist** is a security mechanism that specifies which IP addresses are allowed to access a resource. Any IP address not on the allowlist is blocked. This approach helps protect your environment by filtering traffic based on trusted sources.

You can use IP allowlists to restrict access to your formation. Once an allowlist is configured, only IP addresses included in the allowlist or within a specified range can connect.

### Key Points:
- Allowlists can be applied **only to public endpoints**.
- If the allowlist is **empty** (no IPs are listed), the restriction is **disabled** and connections from any IP address are allowed.
- Allowlists will regulate traffic **only for DB connectivity** (port `50001`). There is **no impact** on web console access or rest API over port `443`.

## Setting an Allowlist Configuration

To enable IP allowlisting:

1. Open a support ticket with IBM Cloud.
2. Provide the IP address to be allowlisted.
3. Include a short description for the allowlist entry.

### IP Address Format

You can specify an IP in either of the following formats:

- A single IP address (e.g., `170.225.223.5`)
- A CIDR block (e.g., `192.168.1.0/24` or `170.225.227.6/32`)

### Description

Each allowlist entry requires a description. This should be meaningful for identification—such as a customer name, project code, or employee ID.

