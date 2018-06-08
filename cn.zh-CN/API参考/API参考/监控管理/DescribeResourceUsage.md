# DescribeResourceUsage {#reference_qlz_4xl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查看实例的资源利用信息。返回用户的某个实例的已用空间大小，通过DBInstanceId来获取实例资源使用情况。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeResourceUsage。|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|实例名。|
|Engine|String|数据库类型。|
|DiskUsed|Integer|已用空间（DataSize+LogSize），单位：Byte，-1表示没有数据。|
|DataSize|Integer|数据文件占用空间，单位：Byte，-1表示没有数据。|
|LogSize|Integer|日志占用空间，单位：Byte，-1表示没有数据。|
|BackupSize|Integer|备份占用空间，单位：Byte，-1表示没有数据。|
|ColdBackupSize|Integer|冷备的存储量，单位：Byte，-1表示没有数据。|
|SQLSize|Integer|SQL的存储量，单位：Byte，-1表示没有数据。|

