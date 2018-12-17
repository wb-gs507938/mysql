# 通过内部SQL命令验证 {#concept_o2g_cdv_ydb .concept}

通过读写分离地址登录实例可以使用内部SQL命令对读写分离效果进行验证。

**说明：** 该SQL语句目前为内部测试功能，后期根据实际情况可能会做调整，请暂勿用于生产环境。

## 查看一条SQL命令被发送到哪个实例执行 {#section_il5_5cv_ydb .section}

**操作步骤**

1.  通过客户端使用读写分离地址[连接RDS实例](../cn.zh-CN/快速入门MySQL版/连接实例.md#)。
2.  执行如下命令查看执行SQL命令的实例ID。

    ```
    /*PROXY_INTERNAL*/show last route;
    ```

    **说明：** 

    -   只有通过**读写分离地址**连接才可以使用该命令。
    -   使用mysql字符终端连接时，需要加入-c，否则会忽略注释，返回如下错误：

        ```
        ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that
        corresponds to your MySQL server version for the right syntax to use near 'last route' at
        line 1
        ```


**查看结果**

返回的`last_bkid`表示上一条SQL（hint的上一条）发送的目的库ID，这个ID是每个RDS实例的唯一性标识。如下图所示。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7923/15450395034252_zh-CN.png)

**说明：** 由于RDS的SQL负载是按批负载，现在是以每100条为最小单位，所以您可能看到第一次select在一个实例ID上执行，第二次还是在这个ID上执行，要执行100次之后才会发现到另外一个ID上执行。可以通过写个简单的SQL文件来验证，如下面的a.sql所示：

```
select 1;
/*PROXY_INTERNAL*/show last route;select 1;
***100条***;
select 1;
/*PROXY_INTERNAL*/show last route;
```

这时就可以看到第101条SQL被路由到另外一个ID（假设您有超过2个只读实例ID可以负载）。

## 验证写请求都发送到主库（主实例）执行 {#section_v22_jdv_ydb .section}

RDS实例开通读写分离功能后，写请求只能发送到主实例，因为所有的只读实例都是read\_only，即使系统或路由出错了（假设把某条写SQL路由到只读实例），系统会根据出错原因（read\_only error）再次把该写请求发到主实例上执行。

另外，您可以先执行一条insert语句，再执行如下hint SQL来确定写请求是否都发送到了主实例。

```
/*PROXY_INTERNAL*/show last route;
```

