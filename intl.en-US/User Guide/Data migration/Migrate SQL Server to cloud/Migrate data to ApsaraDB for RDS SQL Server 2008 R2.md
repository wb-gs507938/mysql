# Migrate data to ApsaraDB for RDS SQL Server 2008 R2 {#concept_swt_smw_ydb .concept}

Instances of the SQL Server 2008 R2 version support easy data migration to the cloud database. You only have to back up the complete data using the official backup function of Microsoft on the self-built database, upload the backup file to the [Object Storage Service \(OSS\)](https://www.alibabacloud.com/help/doc-detail/31817.htm) of Alibaba Cloud, and then move the full amount of data to the specified RDS database through the RDS console. This feature takes advantage of Microsoft’s official backup and recovery program, realizes 100% compatibility, and is combined with the powerful capabilities of OSS. All these functions make it a highly efficient feature for the data migration to the cloud database.

## Prerequisite {#section_z4d_hnw_ydb .section}

The migration target database is created in RDS. For more information, see [Create database and account for SQL Server 2008 R2](https://www.alibabacloud.com/help/doc-detail/26145.htm).

**Note:** The name of the target database in RDS can be the same with that of the local database to be migrated.

## Billing details {#section_q1w_3nw_ydb .section}

When you migrate data to the cloud, no additional fees are charged for RDS but you must pay for OSS, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7997/4362_en-US.png)

Figure description:

-   Uploading local data backup files to OSS is free of charge.

-   OSS storage is chargeable, if you store backup files on OSS. For more information, see [Pricing](https://www.alibabacloud.com/product/oss?spm=a3c0i.7990255.247275.8.7a40749en97oY9#pricing).

-   If you migrate backup files from OSS to RDS through the intranet, no extra fees are charged. If it is through the Internet, OSS charges for the Internet outbound traffic. For more information, see [Pricing](https://www.alibabacloud.com/product/oss?spm=a3c0i.7990255.247275.8.7a40749en97oY9#pricing).

    **Note:** The RDS instance and OSS bucket can connect to each other through intranet only when they are located in the same region. Therefore, make sure that the backup files are uploaded to the bucket that is located in the same region as the target RDS instance.


## Procedure {#section_fm1_34w_ydb .section}

1.  Prepare the local database. The detailed procedure is as follows:
    1.  Start the Microsoft SQL Server Management Studio \(SSMS\) client.
    2.  Log on to the database to be migrated to RDS.
    3.  Run the following command to check the Recover Mode of the local database.

        ```
        use master;
        go
        select name, case recovery_model
        when 1 then FULL
        when 2 then BULD_LOGGED
        when 3 then SIMPLE end model from sys.databases
        where name not in (master,tempdb,model,msdb);
        go
        ```

        Check the model value of the local database:

        -   If the model value is not FULL, perform Step d.

        -   If the model value is FULL, perform Step e.

    4.  Run the following command to set the Recover Mode of the source database to FULL.

        **Note:** Setting Recover Mode to FULL increases SQL Server logs. Therefore, make sure to leave sufficient disk space for the logs.

        ```
        ALTER DATABASE [dbname] SET RECOVERY FULL;
        go
        ALTER DATABASE [dbname] SET AUTO_CLOSE OFF;
        go
        ```

    5.  Run the following command to back up the source database. This example uses filename.bak as the backup file name.

        ```
        use master;
        go
        BACKUP DATABASE [testdbdb] to disk =d:\backup\filename.bak WITH COMPRESSION,INIT;
        go
        ```

    6.  Run the following command to verify the integrity of the backup file.

        ```
         USE master
         GO
         RESTORE FILELISTONLY 
           FROM DISK = ND:\Backup\filename.bak;
        ```

        Returned result description:

        -   If a result set is returned, the backup file is valid.

        -   If an error is returned, the backup file is invalid. Back up the database again.

    7.  Run the following command to recover the Recover Mode of the source database.

        **Note:** If you do not perform Step iv \(that is, the original Recover Mode of the database is FULL\), skip this step.

        ```
        ALTER DATABASE [dbname] SET RECOVERY SIMPLE;
        go
        ```

2.  Upload the local backup file to OSS and retrieve the file URL. The detailed procedure is as follows:
    1.  Upload the backup file to OSS:
        -   For the procedure of uploading a file smaller than 5 GB, see [Upload an object](https://www.alibabacloud.com/help/doc-detail/31886.htm).

        -   For the procedure of uploading multiple files or a file larger than 5 GB, see [Multipart upload](https://www.alibabacloud.com/help/doc-detail/31850.htm). To use a GUI, see [ossbrowser](https://www.alibabacloud.com/help/doc-detail/61872.htm).

    2.  In the left-side navigation pane of the [OSS console](https://oss.console.aliyun.com/), select the bucket where the backup file belongs.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7997/4363_en-US.png)

    3.  Select **Files**.
    4.  Click the name of the target backup file.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7997/4364_en-US.png)

    5.  In the **Signature** field, change the validity period of the link. We recommend that you set the validity period to 28,800s, that is, eight hours.

        **Note:** When you migrate the backup file from OSS to RDS, the URL of the backup file is required. If the link validity period for the URL expires, the data migration fails. Therefore, we recommend that you set the validity period to the maximum value, which is 28,800s.

    6.  Click **Copy File URL**. The default URL is the Internet connection address of the file.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7997/4365_en-US.png)

    7.  If you want to migrate data through the intranet, change the endpoint in the backup file URL to the intranet endpoint. The intranet endpoint varies depending on the network type and region. For more information, see [Access domain name and data center](https://www.alibabacloud.com/help/doc-detail/31837.htm).

        For example, if the backup file URL is `http://rdstest-yanhua.oss-cn-shanghai.aliyuncs.com/testmigraterds_20170906143807_FULL.bak?Expires=1514189963&OSSAccessKeyId=TMP.AQGVf994YTPfArSpw78uix2rdGBi-dPe_FzQSLwOLP7MVlR-XXXX`, change the Internet endpoint `oss-cn-shanghai.aliyuncs.com` in the URL to the intranet endpoint `oss-cn-shanghai-internal.aliyuncs.com`.

3.  Migrate the backup file from OSS to RDS. The detailed procedure is as follows:
    1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
    2.  Select the region where the target instance is located.
    3.  Click the ID of the target instance to go to the **Basic Information** page.
    4.  In the left-side navigation pane, select **Databases** to go to the **Databases** page.
    5.  Find the target database and click **Migrate backup files from OSS** in the **Action** column.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7997/4366_en-US.png)

    6.  In the **Import Guide** dialog box, read the prompt and click **Next** to go to the **Upload the backup files** page.
    7.  Read the prompt and click **Next** to go to the **Import data** page.
    8.  In the **Backup file OSS URL** box, enter the backup file URL in OSS.

        **Note:** Currently, RDS supports only one cloud migration solution, that is **one-time migration of the full backup file**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7997/4367_en-US.png)

    9.  Click **OK**.
    10. In the left-side navigation pane, select **Data Migration to Cloud** to go to the page listing the tasks of migrating backup files from OSS to RDS.
    11. Find the target migration task. If the **Tasks Status** is **Success**, the data is successfully migrated to the RDS database. If the migration task status does not change to **Success** after a long time, click **View File Details** next to the migration task to view the failure causes. After solving the problems, perform the required steps to migrate the backup file again.

