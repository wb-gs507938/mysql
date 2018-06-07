# 通过内部SQL命令验证 {#concept_o2g_cdv_ydb .concept}

您可以通过执行命令来验证读写分离的效果。

```
/*PROXY_INTERNAL*/show last route;
```

**说明：** 该SQL语句目前为内部测试功能，后期根据实际情况可能会做调整，请暂勿用于生产环境。

## 查看一条SQL命令被发送到哪个库执行 {#section_il5_5cv_ydb .section}

执行如下SQL命令，即可查看SQL命令执行到的实例ID。

```
/*PROXY_INTERNAL*/show last route;
```

**说明：** RDS提供了内置的hint SQL（该SQL只能通过读写分离vip执行），如果您通过mysqlclient客户端访问，必须加-c选项，否则hit会被mysql client过滤掉，导致返回如下错误。

```
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that
corresponds to your MySQL server version for the right syntax to use near 'last route' at
line 1
```

返回结果：last\_bkid，即上条SQL（hit的上一条）发到哪个库的ID，这个ID是RDS每个实例的唯一标识，每个实例的ID唯一。详情如下图所示。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7923/4252_zh-CN.png)

**说明：** 由于RDS的SQL负载是按批负载，现在是以每100条为最小单位，所以您可能看到第一次select在一个实例ID上执行，第二次还是在这个ID上执行，要执行100次之后才会发现到另外一个ID上执行了。可以通过写个简单的SQL文件来验证，如下面的a.sql所示：

```
select 1;
/*PROXY_INTERNAL*/show last route;select 1;
***100条***;
select 1;
/*PROXY_INTERNAL*/show last route;
```

这时就可以看到第101条SQL被路由到另外一个ID（假设您有超过2个的只读实例ID可以负载）。

## 验证写请求都发送到主库（主实例）执行 {#section_v22_jdv_ydb .section}

RDS实例开通读写分离功能后，写请求只能发送到主库，因为所有的只读库都是read\_only，即使我们系统或路由出错了（假设把某条写的SQL路由到只读库），我们会根据出错原因（read\_only error）再次把该写请求发到主库上执行。

另外，您可以先执行一条insert语句，再执行如下hint SQL来确定写请求是否都发送到了主库。

```
/*PROXY_INTERNAL*/show last route;
```

## 验证读请求都发送到备库（只读实例）执行 {#section_syv_kdv_ydb .section}

执行如下hint SQL命令，查询执行度请求的实例ID，来确定读请求是否发送到了备库。

```
/*PROXY_INTERNAL*/show last route;
```

**说明：** 由于RDS的SQL负载是按批负载，现在是以每100条为最小单位，所以您可能看到第一次select在一个实例ID上执行，第二次还是在这个ID上执行，要执行100次之后才会发现到另外一个ID上执行了。可以通过写个简单的SQL文件来验证，如下面的a.sql所示：

```
select 1;
/*PROXY_INTERNAL*/show last route;select 1;
***100条***;
select 1;
/*PROXY_INTERNAL*/show last route;
```

这时就可以看到第101条SQL被路由到另外一个ID（假设您有超过2个的只读实例ID可以负载）。

