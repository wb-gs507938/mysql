# Cluster Edition {#concept_vcs_h1c_5fb .concept}

Currently, only RDS for SQL Server 2017 Enterprise Edition supports the Cluster Edition, which is based on the native AlwaysOn technology of SQL Server. The Cluster Edition separates computing from storage, and supports read/write splitting. By default, each read-only instance in the cluster also provides an independent intranet connection string.

The following figure shows the architecture of the Cluster Edition.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62203/154304183532574_en-US.png)

## Advantages {#section_wcv_gh2_wfb .section}

-   **Achievable zero Recovery Point Object \(RPO\)**

    To achieve ultimate data reliability, you can build a database with an RPO of zero by setting the REQUIRED\_SYNCHRONIZED\_SECONDARIES\_TO\_COMMIT parameter.

    **Note:** However, after this parameter is turned on, performance is affected because every write request is completed only after data is written into the slave instance.

-   **Horizontally scalable read capability**

    You can add read-only instances to linearly increase the cluster's read capability. Additionally, the specifications of read-only instances can be different from those of the master instance. Therefore, you can add read-only instances with high specifications to achieve even better read capability.

    **Note:** By default, read-only instances do not support high availability. To implement high availability of read-only instances, at least two read-only instances are required.

-   **Flexibly controllable costs**

    In the Cluster Edition, you can create read-only instances of common specifications, which are cost-effective options. Additional read-only instances can process more read requests so that the overall system configuration is optimized.

    In addition, specifications of read-only instances can be lower than those of the master instance. Therefore, you can choose cost-effective read-only instance with lower specifications for background applications, such as intelligent analysis applications.

    In the near future, the Cluster Edition will also support the maximum performance mode, which can be used during peak hours to implement asynchronous replication between the master and slave nodes, so that the cluster performance is maximized.


## Scenarios {#section_jtz_132_wfb .section}

-   **Use read-only instances to handle read requests during peak traffic hours**

    For example, to prepare for peak trading events like Double 11 Festival, online retail enterprises can buy additional read-only instances with high specifications to process the majority of read requests while implementing read/write splitting and traffic control on the service level. In this way, the enterprises can handle several times the amount of usual traffic.

-   **Assign analysis tasks to read-only instances**

    Enterprises generally have demand for intelligent data analysis. An independent read-only instance dedicated for data analysis can reduce the probability of the master instance becoming unresponsive, improve concurrency, and reduce the impact on core service queries, thereby ensuring service stability.


