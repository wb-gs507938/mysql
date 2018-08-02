# DescribeDBInstanceProxyConfiguration {#reference_qhj_jr4_p2b .reference}

## 描述 {#section_lqx_vr4_p2b .section}

该接口用于查看数据库代理设置。

## 请求参数 {#section_mcq_wr4_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：DescribeDBInstanceProxyConfiguration。|
|DBInstanceId|String|是|实例ID。|

## 返回参数 {#section_cbt_zr4_p2b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|TransparentSwitchConfiguration|String|是否开启透明切换：-   Enable：开启；
-   Disable：关闭。

返回值格式为json字符串，如：`{"status":"Enable"}`。

|
|PersistentConnectionsConfiguration|String|是否开启短连接优化：-   Enable：开启；
-   Disable：关闭。

返回值格式为json字符串，如：`{"status":"Disable"}`。

|
|AttacksProtectionConfiguration|JSON/String|是否开启防暴力破解：-   Enable：开启；
-   Disable：关闭。

返回值格式为json字符串，如：

```
{"status":"Disable", "check_interval_seconds": 60,
              "max_failed_login_attempts": 60, "blocking_seconds": 600}
```

参数说明及取值范围：

-   对于每一个客户端，check\_interval\_seconds秒内最多允许max\_failed\_login\_attempts次错误密码登录，否则将对该客户端IP禁止登录blocking\_seconds秒钟。
-   取值范围：
    -   check\_interval\_seconds：\[30-600\]，单位为秒；
    -   max\_failed\_login\_attempts：\[10-5000\]，单位为次数；
    -   blocking\_seconds：\[30-3600\]，单位为妙。

|

