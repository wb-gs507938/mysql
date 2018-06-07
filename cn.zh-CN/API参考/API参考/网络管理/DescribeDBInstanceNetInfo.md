# DescribeDBInstanceNetInfo {#reference_kvb_zyh_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查看指定实例的所有连接信息。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDBInstanceNetInfo。|
|DBInstanceId|String|是|单个实例名。|
|ConnectionStringType|String|否|查询连接串类型：-   Normal：查询普通连接
-   ReadWriteSplitting：查询读写分离连接
-   不传则返回所有连接：

|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceNetInfos|List<DBInstanceNetInfo\>|实例的连接信息。|
|InstanceNetworkType|String| -   Classic：经典网络。
-   VPC：VPC网络

 |

## DBInstanceNetInfo {#section_xtt_lzh_12b .section}

|名称|类型|描述|
|--|--|--|
|ConnectionString|String|DNS连接串。|
|IPAddress|String|IP地址。|
|IPType|String| -   经典网络类型的实例IPType为：Inner、Public；
-   VPC类型的实例IPType为：Private、Public。

 |
|Port|String|端口信息。|
|VPCId|String|VPC ID。|
|VSwitchId|String|VSwitch ID，多个值用英文逗号“,”隔开。|
|ConnectionStringType|String|连接串类型：-   Normal：普通连接地址
-   ReadWriteSplitting：读写分离地址

|
|MaxDelayTime|String|最大延迟时长阈值，读写分离链路时返回该参数。超过该时长的只读不分配流量，单位是秒。|
|DistributionType|String|读请求分配策略，仅在读写分离链路返回该参数：-   Standard：指按规格自动分配权重
-   Custom：指自定义分配权重

|
|DBInstanceWeights|List|实例权重信息，只有读写分离链路返回该参数。|

## DBInstanceWeight {#section_mfw_yzh_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例ID。|
|DBInstanceType|String|实例类型：-   Master：主实例
-   Readonly：只读实例

|
|Weight|String|实例当前权重。|
|Availability|String|实例可用状态：-   Unavailable：不可用
-   Available：可用

|

