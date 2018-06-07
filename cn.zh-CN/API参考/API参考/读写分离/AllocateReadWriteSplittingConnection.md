# AllocateReadWriteSplittingConnection {#reference_nzs_lhf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

对拥有只读实例的主实例，在高安全访问模式下，可以申请一个读写分离访问地址。申请该地址后，不影响原主实例、只读实例的既有访问地址，以及正常的内外网申请。

实例状态必须满足如下所有条件，否则将会操作失败：

-   实例状态为运行中。

-   实例没有迁移任务。

-   只支持在拥有只读实例的主实例上申请。

-   实例链路必须是高安全模式。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为AllocateReadWriteSplittingConnection。|
|DBInstanceId|String|是|现有主实例名。|
|ConnectionStringPrefix|String|否| -   读写分离连接串前缀名，全局唯一；
-   由小写字母和中划线组成，需以字母开头，长度不超过30个字符；
-   默认以“实例名+rw”字符串组成前缀。

 |
|Port|Int|否|端口，范围为3001-3999，默认为3306。|
|MaxDelayTime|Int|否| -   延迟阈值，单位为秒，范围是0-7200，不传该参数则默认为30。
-   当只读实例延迟超过该阈值时，读取流量不发往该实例。

 |
|NetType|String|否|读写分离连接串的网络类型-   Internet：外网
-   Intranet：内网，默认为内网，且内网类型与主实例保持一致

|
|PrivateIpAddress|String|否| -   若当前实例为VPC网络类型，且创建读写分离链路指定网络类型为内网，则可传入该参数指定读写分离链路的VPC IP。
-   若不传，则由系统自动分配 。

 |
|DistributionType|String|是|读权重分配模式，取值如下：-   Standard：指按规格自动分配权重
-   Custom：指自定义分配权重

|
|Weight|Json/ String|否| -   读流量权重分配，即传入主实例和只读实例的读请求权重；
-   以100递增，最大值为1000。
-   按如下格式传入：\{“Instanceid“:”Weight”,”Instanceid”:”Weight”\}
-   当DistributionType为Custom时，必须传入该参数
-   当DisrtibutionType为Standard时，传入该参数无效。

 |

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

