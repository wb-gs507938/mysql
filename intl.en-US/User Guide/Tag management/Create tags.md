# Create tags {#concept_dmq_yw4_ydb .concept}

If you have a large number of instances, you can bind tags to facilitate classification and management. Each tag is composed of a key-value pair, enabling you implement two-level classification for the instances you created.

## Constraints {#section_h5m_fx4_ydb .section}

-   Up to 10 tags can be bound to a single instance and they must have unique TagKeys. Tags with the same TagKeys are overwritten.
-   You cannot bind/unbind more than 5 tags immediately.
-   Tag information is independent in different regions.
-   After unbinding a tag, if it is not bound to any other instances, it is deleted.

## Procedure {#section_ktf_hx4_ydb .section}

1.  Log on to the [RDS Console](https://rds.console.aliyun.com/) and click **Instances** on the left.
2.  Select the region where the target instance is located.
3.  Add tags to the instances. There are two methods:
    -   Add tags to a single instance: Locate an instance, and click **More** \> **Edit tags** .
    -   Add tags to multiple instances: Select multiple instances, and click **Edit tags**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7971/4152_en-US.png)

4.  If you want to add a new tag, click **Create**. Enter the tag Keyand Value, and click **Confirm**.

    **Note:** If you want use the existing tags, click **Available Tags**, select the tag key and tag value, and click Confirm.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7971/4153_en-US.png)

5.  When the tags you need have been added to the tag table, click **Confirm**.

