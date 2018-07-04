# Copy a database for SQL Server 2008 R2 {#concept_o5v_vlq_wdb .concept}

You can copy an existing database to produce an identical one. This article describes how to copy a database on the RDS console and applies only to SQL Server 2008 R2 instances. For instances of SQL Server 2012 and later versions, you can copy a database only by using SQL commands. For more information, see [Copy a database for SQL Server 2012 or later versions](intl.en-US/User Guide/Database management/Copy a database for SQL Server/Copy a database for SQL Server 2012 or later versions.md#).

## Attention {#section_xy3_ylq_wdb .section}

-   Only one database can be copied at a time.

-   The new database must be named differently from all the existing databases.


## Procedure {#section_egc_1mq_wdb .section}

1.  Log on to the [RDS console](https://rdsnew.console.aliyun.com/console/index#/rdsList/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  In the left-side navigation pane, select **Databases** to go to the Database page.
5.  Click **Copy Database**.
6.  Set the parameters.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7938/3112_en-US.png)

    **Parameter description:**

    |Parameter name|Description|
    |--------------|-----------|
    |Specify the new database name|The new database name consists of up to 64 characters including lowercase letters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter and end with a letter or digit.|
    |Select the database to copy|Select the database that you want to copy from the list of existing databases.|
    |Whether to retain the accounts of the source database|When copying a database, you can choose whether to transfer the account and permissions from the source database to the new database. The default option is **Retain**, which means transferring the accounts.|
    |Remarks|You can add information about the new database to facilitate subsequent database management. A maximum of 256 characters can be entered.|

7.  Click **OK**.

