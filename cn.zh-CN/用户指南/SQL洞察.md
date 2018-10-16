# SQL洞察 {#concept_msp_gz1_mfb .concept}

为了更好地提供服务，RDS的SQL审计功能将升级为**SQL洞察**功能，继续为您的数据库提供安全审计、性能诊断等增值服务，升级过程中不影响实例的正常使用，升级后价格更低，功能更丰富。

为保证服务质量，全球的RDS实例将分批进行升级：

-   在升级日期后，新购的实例会默认开通SQL洞察功能（免费试用7天，7天后，如果还未将SQL日志存储时长[修改为30天或以上](#)，SQL洞察功能将自动关闭）
-   在升级日期后，存量的实例将在2个月内自动支持SQL洞察功能，您也可以通过提交工单提前申请。

具体的升级日期如下表所示。

|地域|升级日期|
|--|----|
|华北2（北京）、华东2（上海）、杭州金融云|10月23日|
|华北1（青岛）、华东1（杭州）、华南1（深圳）、深圳金融云|11月1日|
|其它地域|11月15日|

## 功能说明 {#section_ovx_hcv_lfb .section}

原SQL审计功能支持查看和搜索SQL明细、定期审计SQL。SQL洞察在此基础上，做了如下功能升级：

-   **增强搜索**：提供按照DB、User、客户端IP、线程ID、执行时长、扫描行数等多维度检索能力，并支持搜索结果的导出和下载。
-   **SQL分析**：新增SQL分析功能，可以对指定时间段的SQL日志进行可视化交互式分析，找出异常SQL，定位性能问题。
-   **降低成本**：采用新的列式存储和压缩技术，大幅降低了SQL日志存储空间，平均可帮您节省大约60%的成本。（由于SQL数据的不确定性，不保证所有实例的SQL日志占用空间都会降低，以上数字为统计意义上的平均值。）

## 开通SQL洞察 {#section_g4n_21b_mfb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  选择实例所在地域。
3.  单击实例的ID。
4.  在左侧导航栏中，选择**SQL洞察**。
5.  单击**立即开通**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23711/153968518813750_zh-CN.png)

6.  选择SQL日志的保存时长。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23711/153968518813755_zh-CN.png)

    -   **7天免费试用**：仅当该实例没有开通过SQL审计或SQL洞察功能时，才可以选择此选项。

        7天后，如果还未修改存储时长为30天或以上，SQL洞察功能将自动关闭。关闭后，已保存的SQL记录将被删除且无法恢复。

    -   如果选择30天或以上，系统将自动开始计费。

## 修改SQL日志的存储时长 {#section_sgz_q13_mfb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  选择实例所在地域。
3.  单击实例的ID。
4.  在左侧导航栏中，选择**SQL洞察**。
5.  单击**服务设置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23711/153968518813804_zh-CN.png)

6.  修改存储时长。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23711/153968518813805_zh-CN.png)


## 关闭SQL洞察 {#section_f4b_sb3_mfb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  选择实例所在地域。
3.  单击实例的ID。
4.  在左侧导航栏中，选择**SQL洞察**。
5.  单击**服务设置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23711/153968518813804_zh-CN.png)

6.  关闭SQL洞察的开关。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23711/153968518813807_zh-CN.png)


