# RDS函数计算触发器用户测试流程 {#concept_k33_sk1_tfb .concept}

## 原理 { .section}

RDS函数计算触发器原理如下：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436730986_zh-CN.png)

优势

-   您无需关心服务器和服务部署，只需要开发业务代码，非常轻量
-   您无需关心RDS主备切换和迁移等事件，我们会处理好binlog位点，binlog可能会少量重复，但不会丢失

## 支持范围 { .section}

-   规格

    ```
    支持mysql 5.6、5.7，高可用版以及基础版
    ```

-   网络

    ```
    支持经典网络和vpc
    ```

-   地域

    ```
    当前支持地域：北京、青岛、上海、杭州、深圳、香港、美东、美西、新加坡、澳大利亚、德国
    ```


## 功能限制 { .section}

-   不支持大事务

    ```
    消息最大为6MB，这个是函数计算的限制，后期考虑优化
    
    ```


## 创建函数 { .section}

需要用户创建函数，函数计算相关概念和控制台使用，请先阅读其文档[快速入门](https://help.aliyun.com/document_detail/73329.html?spm=a2c4g.11186623.6.543.2d0710f3HFTovI)。

1.  在杭州region创建服务test\_service\_for\_rds。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436730987_zh-CN.png)

2.  创建函数，选择**空白函数**，然后选择**RDS事件触发器**，填写触发相关的配置，然后下一步。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436730988_zh-CN.png)

3.  填写函数名称『test\_function\_for\_rds』，语言选择**python3**，函数代码如下

    ```
    # -*- coding: utf-8 -*-
    import logging  
    
    def handler(event, context):
      logger = logging.getLogger()
      logger.info('hello world')
      return 'hello world'
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436730989_zh-CN.png)

4.  用户需要给RDS授权，选择**快捷授权**，然后点击**授权**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436730990_zh-CN.png)

5.  在弹出来的授权页面，选择**同意授权**，然后会自动跳转回函数创建页面，显示授权成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436730991_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436830992_zh-CN.png)

6.  点击下一步，确认函数相关信息，没有问题的话，点击**创建**，就完成函数的创建了。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/61607/154175436830993_zh-CN.png)


## 测试 { .section}

授权和创建函数两步完成后，即可开始测试。

