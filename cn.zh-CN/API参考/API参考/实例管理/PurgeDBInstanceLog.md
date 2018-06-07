# PurgeDBInstanceLog {#reference_ovn_l1f_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于清空MySQL类型实例的所有BINLOG日志，或者使SQL Server类型实例产生一个临时备份，临时备份完成后将收缩RDS磁盘空间。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为PurgeDBInstanceLog。|
|DBInstanceId|String|是|待收缩磁盘空间的实例。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=PurgeDBInstanceLog
&DBInstanceId=rdsaiiabnaiiabn
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<PurgeDBInstanceLogResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</PurgeDBInstanceLogResponse>
```

**JSON格式**

```
{
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
}
```

