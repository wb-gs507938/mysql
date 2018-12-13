# SQL Server实例级别数据库上云 {#concept_r5l_jcm_cgb .concept}

本文档介绍如何通过全量备份文件将用户本地自建或者ECS上自建的SQL Server数据库一键迁移到阿里云RDS for SQL Server。

## 应用场景 {#section_kcx_nvl_cgb .section}

RDS for SQL Server已经发布了基于OSS上云的方法包括：[全量备份数据上云SQL Server 2008 R2版](cn.zh-CN/RDS for SQL Server用户指南/数据迁移/全量备份数据上云SQL Server 2008 R2版.md#)、[全量备份数据上云SQL Server 2012/2016版本](cn.zh-CN/RDS for SQL Server用户指南/数据迁移/全量备份数据上云SQL Server 2012__2016版本.md#)和[增量备份数据上云SQL Server 2012/2016版本](cn.zh-CN/RDS for SQL Server用户指南/数据迁移/增量备份数据上云SQL Server 2012__2016版本.md#)。以上SQL Server迁移上云的方法都是基于数据库级别的方式实现上云，即每次将用户线下的一个数据库迁移上云。

假如用户线下SQL Server实例有几十上百个数据库需要迁移上云，显然以上三种上云方法不适用于这种场景。为了解决用户大批量数据库迁移上云问题，RDS for SQL Server推出了实例级别大批量数据库一键迁移上云的功能。您只需将线下实例所有数据库完整备份文件上传到OSS Bucket的一个文件夹中，执行实例级别迁移上云脚本python脚本即可。

## 前提条件 {#section_ntp_svl_cgb .section}

-   **仅支持实例级别完整备份文件上云**

    本功能仅支持实例内所有数据库完整备份文件全量迁移上云，不支持增量上云。

-   **要求RDS for SQL Server为以下版本：**

    -   RDS for SQL Server 2008R2企业版的高可用系列（即双机版）
    -   RDS for SQL Server 2012/2016 Web版、企业版的基础系列（即单机版）
    -   RDS for SQL Server 2012/2016标准版、企业版的高可用系列（即双机版）
-   **OSS Bucket与RDS for SQL Server所在地域相同**

    请确保OSS Bucket和RDS for SQL Server所在地域相同，以提高RDS for SQL Server下载备份文件的效率，否则可能会出现RDS for SQL Server无法下载备份文件而导致任务失败。

-   阿里云主账号和子账号都可以实现实例级别迁移上云，但阿里云子账号默认不具有访问OSS和RDS的权限，如果您需要使用子账号实现迁移上云，请为子账号授权，方法如下：
    1.  在阿里云产品与服务中单击**访问控制**，打开访问控制RAM控制台。
    2.  在左侧列表选**用户管理**查看用户列表，找到您需要授权的子账号，单击**授权**打开编辑个人授权策略窗口。
    3.  为账户授权**AliyunOSSFullAccess**、**AliyunOSSReadOnlyAccess**、**AliyunRDSFullAccess**和**AliyunRDSReadOnlyAccess**四个权限，单击**确定**，完成授权，如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994534169_zh-CN.png)

-   **数据库备份文件名约束**

    为保证实例级别数据库完整备份文件迁移上云成功，用户线下数据库的备份文件名需要满足命名约束要求（我们是通过提取备份文件名来获取迁移上云数据库名字）。

    数据库备份文件命名格式为：`databaseName_backupType_backupTime.bak`，即`数据库名字_备份类型_备份时间.bak`。

    例如，`TestDb_FULL_20180518153544.bak`表示：

    -   数据库名字为TestDb；
    -   数据库备份类型为FULL完整备份；
    -   备份时间为20180518153544；
    -   备份文件后缀名为bak。

        推荐您直接使用阿里云提供的数据库备份脚本，详情参见准备工作内的**备份线下实例所有数据库**。


## 准备工作 {#section_rdq_svl_cgb .section}

准备工作您只需做一次，包括python安装、依赖包安装、创建OSS Bucket。

1.  安装python

    请根据[Python官网](https://www.python.org/downloads/)的引导安装合适的Python版本，推荐安装2.7.10。

2.  安装完毕后，查看Python版本。
    -   如果是Windows操作系统：

        执行`C:\>c:\Python27\python.exe -V`查看Python版本，如果输出内容为：`Python 2.7.10`表明您已成功安装了Python 2.7.10版本。

        如果提示不是内部或外部命令， 请检查配置Path环境变量，增加Python的安装路径和pip命令的目录，如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994534170_zh-CN.png)

    -   如果是Mac/Linux/Unix操作系统：

        执行`$ python -V`查看Python版本，如果输出内容为：`Python 2.7.10`表明您已成功安装了Python 2.7.10版本。

3.  安装SDK依赖包。

    使用pip安装或者git clone源码安装，任选其一。

    -   Pip安装

        ```
        pip install aliyun-python-sdk-rds
        pip install oss2
        ```

    -   源码安装

        ```
        # git 克隆openapi
          git clone https://github.com/aliyun/aliyun-openapi-python-sdk.git
          # 安装阿里云 SDK 核心库
          cd aliyun-python-sdk-core
          python setup.py install
          # 安装阿里云 RDS SDK
          cd aliyun-python-sdk-rds
          python setup.py install
          # git 克隆OSS SDK
          git clone https://github.com/aliyun/aliyun-oss-python-sdk.git
          cd aliyun-oss-python-sdk
          # 安装OSS2
          python setup.py install
        ```

4.  创建OSS Bucket，请确保OSS Bucket与目标实例RDS所在地域相同，如果Bucket已经存在，请跳过本步骤。
    1.  登录阿里云[OSS控制台](https://oss.console.aliyun.com/)。
    2.  单击存储空间后面的加号**+**。
    3.  设置Bucket名称、地域、存储类型和读写权限，单击**确定**，如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994534171_zh-CN.png)

5.  创建目标实例数据库。
    -   如果您的目标实例是RDS for SQL Server 2012及以上版本，请跳过该步骤。
    -   如果您的目标实例是RDS for SQL Server 2008R2版本，请通过RDS控制台，在目标实例下创建所有相同名字的数据库，且保持数据库为空。RDS for SQL Server 2008R2创建数据库的方法请参见[创建数据库和账号SQL Server 2008 R2版](../../../../cn.zh-CN/快速入门SQL Server版/初始化配置/创建数据库和账号/创建数据库和账号SQL Server 2008 R2版.md#)。
6.  备份线下实例所有数据库。

    在对本地数据库做全量备份之前，请确保已停止写入数据。备份过程中新写入的数据将不会被备份。

    您可以按已知的方式执行全量备份，但备份文件名必须满足[前提条件内的数据库备份文件名约束](#)。推荐使用如下方法进行全量备份：

    1.  下载[备份脚本](https://rdshelpattachments.oss-cn-beijing.aliyuncs.com/Migration/RDSBackupSpecifiedDatabasesToLocal.sql)，用SSMS打开备份脚本。
    2.  根据实际情况，修改如下4个参数：

        |配置项|说明|
        |---|--|
        |@backup\_databases\_list|需要备份的数据库，多个数据库以分号或者逗号分隔。|
        |@backup\_type|备份类型，参数值如下：        -   FULL：全量备份；
        -   DIFF：差异备份；
        -   LOG：日志备份。
|
        |@backup\_folder|备份文件所在的本地目录。如不存在，会自动创建。|
        |@is\_run|是否执行备份，参数值如下：        -   1：执行备份；
        -   0：只做检查，不执行备份。
|

    3.  执行备份脚本。
7.  上传备份文件到OSS。

    如果您的线下数据库位于ECS上自建SQL Server中，且ECS实例位于VPC中。为了能通过内网模式上传备份文件到OSS，加快备份文件上传的效率（VPC模式下上传速度可以达到100 MB/s），在使用OSS Browser工具登录时，请用OSS endpoint的VPC地址。

    1.  获取OSS Endpoint VPC地址方法如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994634172_zh-CN.png)

    2.  OSS Browser设置的方法：

        AK登录OSS Browser，Endpoint选择自定义， Endpoint地址中输入VPC地址，例如，`http://oss-cn-beijing-internal.aliyuncs.com` ，输入AccessKeyId和AccessKeySecret。

        |方法|详情|
        |--|--|
        |使用OSS Browser工具上传|         -   推荐使用OSS Browser工具上传备份文件到OSS。
        -   具体操作请参考[OSS Browser](https://help.aliyun.com/document_detail/61872.html?spm=a2c4g.11186623.2.30.2a796271ygyY59)。
 |
        |使用OSS控制台上传|         -   如果备份文件小于5GB，可以直接使用OSS控制台上传。
        -   具体操作请参考[使用OSS控制台上传](https://help.aliyun.com/document_detail/31886.html)。
 |
        |使用OSS API上传|         -   如果您有全自动无人干预上云需求，请使用OSS OpenAPI，通过断点续传的方式上传备份文件到OSS Bucket。
        -   具体操作请参考[断点续传](https://help.aliyun.com/document_detail/31850.html)。
 |

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994634173_zh-CN.png)


## 视频演示 {#section_fmq_svl_cgb .section}



## 文本操作步骤 {#section_zsq_svl_cgb .section}

1.  下载python脚本。

    下载实例级别迁移上云脚本`RDSSQLCreateMigrateTasksBatchly.py`，下载地址：[单击下载](https://rdshelpattachments.oss-cn-beijing.aliyuncs.com/Migration/RDSSQLCreateMigrateTasksBatchly.py)。

2.  执行`$ python ~/Downloads/RDSSQLCreateMigrateTasksBatchly.py -h`查看帮助信息。

    结果如下：

    ```
    ~/Downloads/RDSSQLCreateMigrateTasksBatchly.py -k <access_key_id> -s <access_key_secret> -i <rds_instance_id> -e <oss_endpoint> -b <oss_bucket> -d <directory>
    ```

    参数说明：

    |参数|说明|
    |--|--|
    |access\_key\_id|阿里云账号对应的access key id。|
    |access\_key\_secret|阿里云账号对应的access key secret。|
    |rds\_instance\_id|RDS SQL Server目标实例ID。|
    |oss\_endpoint|备份文件所在的OSS Bucket endpoint地址，获取方法请参见文末OSS Endpoint错误中截图。|
    |oss\_bucket|备份文件所在的OSS Bucket名字。|
    |directory|OSS Bucket中，备份文件所在的目录，如果是根目录，请传入“/”。|

3.  执行实例级别迁移上云脚本，完成迁移任务。

    如下示例将OSS Bucket atp-test-on-ecs中，目录Migration/OPENAPIDemo下所有满足条件的备份文件全量迁移到RDS for SQL Server实例rm-2zesz5774ud8s71i5上。

    ```
    python ~/Downloads/RDSSQLCreateMigrateTasksBatchly.py -k LTAIQazXKPRwwErT -s BMkIUhroubQOLpOMqfA09IKlqp4G2k -i rm-2zesz5774ud8s71i5 -e oss-cn-beijing.aliyuncs.com -b atp-test-on-ecs -d Migration/OPENAPIDemo
    ```

    如下示例是将OSS Bucket根目录（根目录用“/”表示）下，满足条件的所有数据库备份文件迁移到RDS for SQL Server实例上。

    ```
    python ~/Downloads/RDSSQLCreateMigrateTasksBatchly.py -k LTAIQazXKPRwwErT -s BMkIUhroubQOLpOMqfA09IKlqp4G2k -i rm-2zesz5774ud8s71i5 -e oss-cn-beijing.aliyuncs.com -b atp-test-on-ecs -d /
    ```

4.  控制台查看迁移上云任务。

    执行完实例级别迁移上云脚本以后，您可以在RDS控制台查看提交的所有任务，查看方法如下所示：

    **RDS for SQL Server 2008 R2**

    1.  登录[RDS控制台](https://rdsnew.console.aliyun.com/)。
    2.  选择目标实例所在地域，单击目标实例的ID。
    3.  在左侧菜单栏中选择**数据上云**。
    4.  在数据上云页面，您可以查看所有提交的迁移上云任务，也可以单击右上角的**刷新**按钮查看迁移上云任务的最新状态，如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994634174_zh-CN.png)

    **RDS for SQL Server 2012及以上版本**

    您可以查看一段时间内的备份上云记录，操作如下：

    进入备份恢复页面，选择备份上云恢复记录，默认会展示最近一周的记录。您可以修改时间范围来查看特定时间段内的上云恢复记录。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994634175_zh-CN.png)


## 常见错误 {#section_rzq_svl_cgb .section}

**AccessKeyId错误**

**错误信息**

```
HTTP Status: 404 Error:InvalidAccessKeyId.NotFound Specified access key is not found. RequestID: XXXXXXXXXXXXXXXXX
```

**错误原因**

用户调用OPENAPI时使用的Access Key ID有错误，导致OPENAPI调用时报错。

**解决方法**

请传入正确的用户Access Key Id，用户可以通过如下方法找到自己的Access Key Id和Access Key Secret：

1.  登录[阿里云](https://home.console.aliyun.com/new#/)。
2.  将鼠标悬停在右上角的头像上，会出现如下图所示的页面。
3.  单击accessKeys，查看自己的Access Key Id和Access Key Secret。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994634176_zh-CN.png)


**Access Key Secret错误**

**错误信息**

```
HTTP Status: 400 Error:IncompleteSignature The request signature does not conform to Aliyun standards. server string to sign is:......
```

**错误原因**

用户调用OPEN API时使用的Access Key Secret有错误，导致OPEN API调用时报错。

**解决方法**

解决方法与上面的AccessKeyId错误一致。

**RDS引擎不支持**

**错误信息**

```
RDS engine doesn't support, this is only for RDS SQL Server engine.
```

**错误原因**

基于实例级别的数据库备份文件上云方案仅支持RDS for SQL Server，不支持其他的RDS引擎产品。

**RDS for SQL Server实例不存在**

**错误信息**

```
Couldn't find specify RDS [XXX].
```

**错误原因**

RDS for SQL Server实例ID不存在，导致OPENAPI找不到对应的RDS for SQL Server实例。

**解决方法**

请检查传入的RDS for SQL Server ID是否正确，并输入正确的RDS for SQL Server ID。

**OSS Endpoint错误**

**错误信息**

```
{'status': -2, 'request-id': '', 'details': "RequestError: HTTPConnectionPool(host='xxxxxxxxxxxxxxxxx', port=80): Max retries exceeded with url: /?bucketInfo= (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x10e996490>: Failed to establish a new connection: [Errno 8] nodename nor servname provided, or not known',))"}
```

**错误原因**

OSS Endpoint错误，导致连接OSS Endpoint时报告错误。

**解决方法**

请确保输入了正确的OSS Endpoint，查看OSS Endpoint的方法如下：

登录[OSS控制台](https://oss.console.aliyun.com/overview)，选择对应的Bucket名字，在**概览**页面中查看对应OSS Bucket的Endpoint地址，这里我们使用外网访问地址即可，如下图所示。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79835/154467994634177_zh-CN.png)

**OSS Bucket错误**

**错误信息**

```
{'status': 404, 'request-id': 'xxxxxxxxx', 'details': {'HostId': 'xxxxxxxxx', 'Message': 'The specified bucket does not exist.', 'Code': 'NoSuchBucket', 'RequestId': 'xxxxxxxx', 'BucketName': 'aaaatp-test-on-ecs'}}
```

**错误原因**

用户传入的OSS Bucket不存在，导致OPEN API无法找到对应的OSS Bucket。

**解决方法**

请传入正确的OSS Bucket名字。

**OSS Bucket中文件夹不存在或者没有备份文件**

**错误信息**

```
There is no backup file on OSS Bucket [xxxxxx] under [xxxxxxxxx] folder, check please.
```

**错误原因**

OSS Bucket中对应的文件夹不存在，或者文件夹中没有满足条件的SQL Server备份文件。

**解决方法**

请检查OSS Bucket中文件夹是否存在，检查文件夹中是否存在满足条件的备份文件。

**备份文件命名不合法**

**错误信息**

```
Warning!!!!!, [autotest_2005_ent_broken_full_dbcc_failed.bak] is not backup file, filtered.
```

**错误原因**

由于我们需要从备份文件名中提取上云数据库的名字，所以对备份文件命名规则有要求，详情参见[前提条件内的数据库备份文件名约束](#)。

**解决方法**

参照数据备份文件名约束中对数据完整备份文件名要求命名。

**OPEN API返回错误**

**错误信息**

```
OPENAPI Response Error !!!!! : HTTP Status: <Http Status Code> Error:<Error> <Description>. RequestID: 32BB6886-775E-4BB7-A054-635664EE6AE4
```

**错误原因**

调用OPEN API返回的错误，这种类型的错误需要仔细阅读**HTTP Status**后面的提示信息。

**解决方法**

这种类型的错误种类比较多，请参见下表。

|HTTP Status Code|Error|Description|解释|
|----------------|-----|-----------|--|
|403|InvalidDBName|The specified database name is not allowed.|非法的数据库名字，不允许取系统数据库名。|
|403|IncorrectDBInstanceState|Current DB instance state does not support this operation.|数据库实例状态不正确，比如，数据库实例在创建中。|
|400|IncorrectDBInstanceType|Current DB instance type does not support this operation.|RDS实例类型不支持，该功能仅支持RDS for SQL Server。|
|400|IncorrectDBInstanceLockMode|Current DB instance lock mode does not support this operation.|数据库锁定状态不正确。|
|400|InvalidDBName.NotFound|Specified one or more DB name does not exist or DB status does not support.|数据库不存在-   RDS for SQL Server 2008R2需要先创建数据库。
-   RDS for SQL Server 2012及以上版本，要求数据库不存在。

|
|400|IncorrectDBType|Current DB type does not support this operation.|数据库类型不支持该操作。|
|400|IncorrectDBState|Current DB state does not support this operation.|数据库状态不正确，比如，数据库在创建中或者正在上云任务中。|
|400|UploadLimitExceeded|UploadTimesQuotaExceeded: Exceeding the daily upload times of this DB.|上云次数超过限制，每个实例每个库每天不超过20次上云操作。|
|400|ConcurrentTaskExceeded|Concurrent task exceeding the allowed amount.|上云次数超过限制，每个实例每天上云总次数不超过500次。|
|400|IncorrectFileExtension|The file extension does not support.|备份文件后缀名错误。|
|400|InvalidOssUrl|Specified oss url is not valid.|用户提供的OSS下载链接地址不可用。|
|400|BakFileSizeExceeded|Exceeding the allowed bak file size.|数据备份文件最大不超过3TB。|
|400|FileSizeExceeded|Exceeding the allowed file size of DB instance.|备份文件还原回来超过用户规格实例大小。|

**子账号权限不足**

**错误信息**

如果您使用阿里云子账号来实现实例级别的迁移上云，子账号权限不足，可能会遇到类似以下错误：

```
HTTP Status: 403 Error:Forbidden.RAM The user is not authorized to operate the specified resource, or this operation does not support RAM. RequestID: xxxxx
{'status': 403, 'request-id': 'xxxx', 'details': {'HostId': 'atp-test-on-ecs.oss-cn-beijing.aliyuncs.com', 'Message': 'The bucket you visit is not belong to you.', 'Code': 'AccessDenied', 'RequestId': 'xxxx'}}
错误原因
```

**错误原因**

使用阿里云子账号，需要具有OSS和RDS的权限，如果没有为子账号授予相应的权限，就会报告类似以上的错误。

**解决方法**

参见[前提条件内的子账号授权方法](#)解决。

