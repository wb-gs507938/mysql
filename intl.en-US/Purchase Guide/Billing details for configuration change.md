# Billing details for configuration change {#concept_syv_qk2_vdb .concept}

You can change the configuration of your instance based on business requirements. The following table describes the configuration change and associated billing details.

|Billing method|Configuration change description| Billing description|
|--------------|--------------------------------|--------------------|
|Subscription| -   You can only upgrade the instance configuration during the contract period.

-   You can choose to upgrade or downgrade the instance configuration when you renew the instance upon expiration.

 | -   You can change the instance configuration in real time within the contract period. However, configuration change is not allowed when the same account has an unpaid renewal order.

    -   Upgrade costs = \(Daily price of the instance after upgrade – Daily price of the instance before upgrade\) × Number of days from the upgrade date to the expiration date

    -   If the number of days from the upgrade date to the expiration date is less than 365, the daily price of the instance after upgrade is equal to the monthly price. If the number of days is equal to or more than 365, the daily price of the instance after upgrade is equal to the annual price. For more information on the billing standard, see [Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a3c0i.7938564.220486.9.42173afcq1FHk9#pricing).

-   The configuration change you select upon renewal within the contract period takes effect during the new billing cycle, and your instance is billed based on the new configuration and length of service time. For example, if a monthly subscription instance expires on June 20, 2017, and you renew the instance and upgrade the instance configuration on May 10, 2017, then the instance is renewed and upgraded on June 20, 2017.

-   If you upgrade or downgrade the instance configuration when you renew the instance upon expiration, the instance is billed based on the new configuration and subscription period.

 |
|Pay-As-You-Go|The instance configuration can be upgraded or downgraded at any time.| -   Billing is based on the instance configuration used when a billing order is generated. For more information on the billing standard, see [Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a3c0i.7938564.220486.9.42173afcq1FHk9#pricing).

-   For more information on the configuration change procedure, see [Change configurations](../../../../intl.en-US/User Guide/Instance management/Change configurations.md).

 |

