# Set parameters through RDS console {#concept_lfl_xmn_wdb .concept}

RDS allows you to define some instance parameters. For more information about the parameters that can be configured, see Parameter Settings on the RDS console. This document describes how to modify parameters and view the modification history. For information about API operations, see API references.

**Note:** 

-   PostgreSQL instances do not support user-defined parameters.

-   To set parameters for instances of SQL Server 2012 and later versions, use SQL commands. For more information, see [Use SQL commands to set parameters](https://help.aliyun.com/document_detail/61161.html).


## Background information {#section_kcg_dnn_wdb .section}

RDS is compatible with the native database service, with similar parameter setting methods. You can configure parameters through the [RDS console](https://rds.console.aliyun.com/?spm=a2c63.p38356.a3.1.514e5c6dFW5iGI) by referring to this example, or by using the [ModifyParameter](https://help.aliyun.com/document_detail/26286.html) API.

For a description of the database parameters, click the following link to view the official documents of the different database versions.

-   MySQL

    -   [MySQL 5.5](http://dev.mysql.com/doc/refman/5.5/en/server-system-variables.html)

    -   [MySQL 5.6](http://dev.mysql.com/doc/refman/5.6/en/server-system-variables.html)

    -   [MySQL 5.7](http://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html)

-   SQL Server

    -   [SQL Server 2008 R2](https://msdn.microsoft.com/library/mt590198.aspx)

## Considerations {#section_mkp_gnn_wdb .section}

-   Configure parameters only within the permissible value ranges shown on the parameter settings page.

-   The instance must be restarted after modifying certain parameters. See the **Force Restart** parameter on the Parameters page to confirm if a restart is required. Before restarting, to avoid any interruption of production, you must guarantee the appropriate business arrangements. Restarting instances may have the following impact:

    -   When you restart an instance, it automatically performs minor version upgrades \(for example, from MySQL 5.6.1 to 5.6.2\). After the upgrade, compatibility issues may occur and cause your business to be unavailable. Therefore, before you restart an instance, we recommend that you create a new instance and use it to perform a compatibility test. After making sure the new version will not cause problems, restart the instance.

    -   In addition, a restart will disconnect the instance. Exercise caution to restart the instances.


## Procedure {#section_wmp_lnn_wdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/?spm=a2c63.p38356.a3.1.514e5c6dFW5iGI).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select **Parameters** on the left-side navigation pane to access the Parameters page.
5.  Select the **Modifiable Parameters** tab.
6.  Select the parameter modification method.
    -   To modify a parameter

        1.  Click the icon ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/26179/cn_zh/1466499669749/Image%20005.png) following the parameter to modify.
        2.  In the dialog box window, enter the target value in the field marked as 1 and click **OK**.
        3.  Click **Submit modify** to confirm the setting, marked as 2 in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7895/3045_en-US.png)

    -   To modify multiple parameters:

        1.  Click **Export Parameters** to export the parameter file \(.txt\) to your local device, marked as 1 in the following figure.
        2.  Open the parameter file and batch modify the relevant parameters.
        3.  Click **Import Parameters**, marked as 2 in the following figure.
        4.  In the Import Parameters window, paste the parameters to modify and the parameter values and click **OK**, marked as 3 and 4 in the following figure.
        5.  Confirm the parameter modification results in the parameter list and click **Submit modify**, marked as 5 in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7895/3046_en-US.png)


## View the modification history {#section_fvg_vnn_wdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/?spm=a2c63.p38356.a3.1.514e5c6dFW5iGI).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select **Parameters** in the left-side navigation pane.
5.  Select the **Modification History** tab.
6.  Select the time range that you want to query, and click **Query**.

## API references {#section_jkb_znn_wdb .section}

-   [DescribeParameterTemplates](https://help.aliyun.com/document_detail/26284.html)

-   [DescribeParameters](https://help.aliyun.com/document_detail/26285.html)

-   [ModifyParameter](https://help.aliyun.com/document_detail/26286.html)


## Best practices {#section_cfc_14n_wdb .section}

[Parameter optimization for MySQL instances](https://help.aliyun.com/document_detail/63255.html)

