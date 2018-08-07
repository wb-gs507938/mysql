# ModifyDBInstanceProxyConfiguration {#reference_g2m_b54_p2b .reference}

## 描述 {#section_pyg_v54_p2b .section}

该接口用于设置数据库代理。

## 请求参数 {#section_qhs_w54_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：ModifyDBInstanceProxyConfiguration。|
|DBInstanceId|String|是|实例ID。|
|ProxyConfigurationKey|String|是|数据库代理的ProxyConfigurationKey，取值：-   TransparentSwitch：透明切换；
-   PersistentConnections：短连接优化；
-   AttacksProtection：防暴力破解。

|
|ProxyConfigurationValue|String|是|数据库代理的ProxyConfigurationValue，取值：-   TransparentSwitch：透明切换，取值为：
    -   Enable：开启，默认值为Enable；
    -   Disable：关闭。如：`{"status":"Enable"}`。
-   PersistentConnections：短连接优化，取值为：
    -   Enable：开启；
    -   Disable：关闭，默认值为Disable。如：`{"status":"Disable"}`。
-   AttacksProtection：防暴力破解，取值为：

    -   Enable：开启；
    -   Disable：关闭，默认值为Disable。如：`{"status":"Disable"}`。
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

## 返回参数 {#section_mx3_1x4_p2b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|RequestId|String|RequestId。|

