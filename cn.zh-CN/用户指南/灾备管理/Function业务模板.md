# Function业务模板 {#concept_b4x_lj1_tfb .concept}

## Redis缓存淘汰 { .section}

以bls业务为例，bls-manager是管控核心组件，对元数据库执行读写操作，但bls-console是外围组件，负责运维页面的api，基本是一些查询操作，bls-console会把查到的数据缓存到redis中，现在存在的问题就是bls-manager更新了元数据，但bls-console不知道，还要等key过期后才会重新从元数据库获取。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61601/154175434330974_zh-CN.png)

为了解决元数据更新后，redis中缓存未及时清除的问题，考虑实时订阅rds的binlog，根据相应dml语句，对redis中的key执行delete操作

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61601/154175434330975_zh-CN.png)

## Java { .section}

java项目初始化过程请参考[这里](https://yuque.antfin-inc.com/bls/rds_lambda/auyrg3#%E5%9F%BA%E6%9C%AC%E8%AE%BE%E7%BD%AE)。

project: [项目链接](http://gitlab.alibaba-inc.com/bls/bls-subscription-java-example)

```
package com.aliyun.bls.subscription.example;

import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;

import com.aliyun.bls.subscription.protocol.Entry;
import com.aliyun.bls.subscription.protocol.Field;
import com.aliyun.bls.subscription.protocol.Message;
import com.aliyun.fc.runtime.Context;
import com.aliyun.fc.runtime.FunctionComputeLogger;
import com.aliyun.fc.runtime.StreamRequestHandler;
import com.google.protobuf.ByteString;
import redis.clients.jedis.Jedis;

public class CacheEvictor implements StreamRequestHandler {

    @Override
    public void handleRequest(InputStream inputStream, OutputStream outputStream, Context context) throws IOException {
        FunctionComputeLogger logger = context.getLogger();

        String host = System.getenv("REDIS_HOST");
        String port = System.getenv("REDIS_PORT");
        String password = System.getenv("REDIS_PASSWORD");

        logger.info("connect to redis: " + host + ":" + port + " with password: " + password);

        Jedis jedis = new Jedis(host, Integer.valueOf(port), 5000);
        jedis.connect();
        jedis.auth(password);

        Message message = Message.parseFrom(inputStream);

        for (Entry entry : message.getEntriesList()) {
            String tableName = String.format("`%s`.`%s`", entry.getDbName(), entry.getTableName());

            ByteString pk = null;
            for (Field field : entry.getRowList()) {
                if (field.getIsPk()) {
                    pk = field.getValue();
                }
            }

            if (pk == null) {
                continue;
            }

            String key = tableName + "." + pk.toString();

            logger.info("delete key: " + key);
            jedis.del(key);
        }
        logger.info(message.toString());
    }
}
```

## Python { .section}

project: [项目链接](http://gitlab.alibaba-inc.com/bls/bls-subscription-python-example)

```
from proto import service_pb2


def handler(event, context):
    message = service_pb2.Message()
    message.ParseFromString(event)

    result = []
    for entry in message.entries:
        table_name = entry.db_name + "." + entry.table_name

        if entry.operation not in [service_pb2.OpType.Value('UPDATE'), service_pb2.OpType.Value('DELETE')]:
            continue

        pk = None

        for field in entry.before_row:
            if field.is_pk:
                pk = field.value

        if not pk:
            continue

        expired_key = table_name + "." + str(pk)
        result.append(expired_key)

    return result


if __name__ == "__main__":
    handler(None, None)

```

