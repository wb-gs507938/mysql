# Bind tags {#reference_wxm_lkn_12b .reference}

## Description {#section_l21_v32_12b .section}

Bind the existing or newly created tags to instances. The limitations are as follows:

-   Each tag is composed of a TagKey and a TagValue. The TagKey cannot be blank, while the TagValue can be blank.

-   The TagKey and TagValue values cannot start with aliyun.

-   The TagKey and TagValue are not case sensitive.

-   The maximum length of TagKey is 64 characters and the maximum length of TagValue is 128 characters.

-   Each instance can be bound to a maximum of 10 tags.  Each tag bound to the same instance must have a unique TagKey. If tags with duplicate TagKeys are bound to the same instance, the tag bound last overwrites the existing tag.


## Request Parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: AddTagsToResource.|
|RegionId|String|Yes|Region where the instance is located. For example, cn-hangzhou.|
|DBInstanceId|String|Yes| -   Instance ID. Up to 30 IDs can be entered at a time.
-   Format: instance1,instance2,instance3.

 |
|Tags|JSON string|Yes| -   The list of tags to bind, including the TagKeys and TagValues. 
-   Up to 5 pairs of value can be entered at a time. 
-   The TagKey cannot be blank, but the TagValue can.
-   Format Sample: \{“key1”:”value1”,“key2”:””\}.

 |

## Return Parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|None|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

