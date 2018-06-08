# DeleteDBInstance {#reference_yvz_xh2_12b .reference}

## 描述 {#section_awy_b32_12b .section}

该接口用于释放RDS实例，要求如下：

-   实例状态为运行中。
-   实例没有被人为锁定。
-   实例类型为主实例（按量付费类型）、只读实例、灾备实例、临时实例。

## 请求参数 {#section_zrb_232_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DeleteDBInstance。|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_y43_h32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_tt5_332_12b .section}

```
https://rds.aliyuncs.com/?Action=DeleteDBInstance
&DBInstanceId=rdsaiiabnaiiabn
&<[公共请求参数]>
```

## 返回示例 {#section_frd_k32_12b .section}

**XML格式**

```
<DeleteDBInstanceResponse>  
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</DeleteDBInstanceResponse>
```

**JSON格式**

```
 {
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
  }
```

