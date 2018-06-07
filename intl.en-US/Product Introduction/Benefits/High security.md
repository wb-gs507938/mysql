# High security {#concept_rvl_gy5_tdb .concept}

## Anti-DDoS attack {#section_phx_ly5_tdb .section}

When Internet connection is used to access RDS instances, the risk of DDoS attacks occurring on the network is possible.  If this occurs, the RDS security system enables flow cleaning operation first.  If the flow cleaning operation fails or the attack reaches the black hole threshold, black hole processing is triggered. Please refer to attack [Protection and attack protection](https://help.aliyun.com/document_detail/66893.html?spm=a2c4g.11186623.2.4.tuvQ0O) for details.

**Notice:** We recommend that RDS instances are accessed over the intranet to avoid DDoS attacks.

## Access control policy {#section_qhx_ly5_tdb .section}

-   You can define the IP addresses that are allowed to access RDS. IP addresses that have not been specified are denied access.

-   Each account can only view and operate its own database.


Please refer to [Access control](https://help.aliyun.com/document_detail/53617.html) for more information.

## System security {#section_shx_ly5_tdb .section}

-   RDS is protected by multiple firewall layers that can effectively block a variety of malicious attacks and guarantee data security.

-   Direct logon to the RDS server is not allowed. Only the port required by the specific database service is open.

-   The RDS server cannot initiate an external connection. It can only accept access requests.


For more information, refer to [Access control](https://www.alibabacloud.com/help/zh/doc-detail/53617.htm).

## Professional support team {#section_uhx_ly5_tdb .section}

Alibaba Cloud’s security team provide rapid security technology support for RDS.

**Related Topics**

-   [Cheap and ease-to-use](intl.en-US/Product Introduction/Benefits/Cheap and ease-to-use.md#)
-   [High performance](intl.en-US/Product Introduction/Benefits/High performance.md#)
-   [High reliability](intl.en-US/Product Introduction/Benefits/High reliability.md#)
-   [EN-US\_TP\_7778.md\#](intl.en-US/Product Introduction/Benefits/Comparison between ApsaraDB for RDS and local databases.md#)

