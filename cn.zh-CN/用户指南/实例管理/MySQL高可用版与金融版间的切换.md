# MySQL高可用版与金融版间的切换 {#concept_k43_x4n_wdb .concept}

只有支持多可用区（含有三个可用区的多可用区）的地域才支持金融版实例，所以目前在华东1、华东2、华南1和华北2的MySQL 5.6版本的实例可以从高可用版升级到金融版或者从金融版切换到高可用版。对于包年包月实例，仅支持在合同期内的实时变配，在续费操作时不支持高可用版与金融版间的切换，关于变配后的计费说明，请参见[变配计费说明](../cn.zh-CN/产品定价/变配计费说明.md#)。

变更实例系列后，实例的连接地址不会改变，可能需要同时变更可用区，但同一地域不同可用区间的实例仍支持内网互通，所以不影响使用。若变更可用区，在变配期间底层需要做数据搬迁，数据量越大，变配生效所需时间越长，请您耐心等待。

高可用版和金融版对应不同的实例规格，每种规格的价格也不同。关于这两个系列所对应的实例规格详情，请参见[实例规格表](https://help.aliyun.com/document_detail/26312.html)。关于计费详情，请参见[云数据库RDS详细价格信息](https://help.aliyun.com/document_detail/https://www.aliyun.com/price/product?spm=5176.doc58263.2.6.8cyo9U.html#/rds/detail)。本文将介绍高可用版和金融版间的切换步骤。

## 前提条件 {#section_mnv_z4n_wdb .section}

-   包年包月实例未过期。

-   实例是在华东1、华东2、华南1或华北2的MySQL 5.6版本的实例。

-   网络类型是经典网络。目前，在VPC内的实例不能进行高可用版与金融版间的切换。关于网络类型的切换步骤，请参见[设置网络类型](https://help.aliyun.com/document_detail/26194.html)。


## 注意事项 {#section_nn1_kpn_wdb .section}

在切换实例系列生效期间，RDS服务可能会出现1次30秒的闪断，请您尽量在业务低谷执行升级操作，或确保您的应用有自动重连机制，以避免闪断造成的影响。

## 操作步骤 {#section_dcm_lpn_wdb .section}

1.  登录RDS管理控制台。
2.  选择目标实例所在地域。
3.  单击目标实例的ID，进入基本信息页面。
4.  在配置信息栏中，切换实例系列，步骤如下：
    -   从高可用版切换到金融版：

        1.  在配置信息栏中，单击**升级到金融版**，如下图所示。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7897/3047_zh-CN.png)

        2.  在变更配置页面，系列选择**金融版**，选择实例的可用区、规格和存储空间，如下图所示。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7897/3048_zh-CN.png)

        3.  单击**确认变更**。
    -   从金融版切换到高可用版：

        1.  在配置信息栏中，单击**变更配置**，如下图所示。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7897/3049_zh-CN.png)

        2.  在变更配置页面，系列选择**高可用版**，选择实例的可用区、规格和存储空间，如下图所示。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7897/3050_zh-CN.png)

        3.  单击**确认变更**。

