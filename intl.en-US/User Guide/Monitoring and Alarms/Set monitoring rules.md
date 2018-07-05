# Set monitoring rules {#concept_ir2_twp_wdb .concept}

The RDS instance offers the instance monitoring function, and sends messages to users after detecting an exception in the instance. Besides, when the instance is locked due to the insufficient disk space, the system sends a message to notify users.

## Background information {#section_fth_vwp_wdb .section}

Alibaba CloudMonitor offers monitoring and alarm rules service. CloudMonitor monitors the metrics and you can use the alarm rules service as well. This service helps you to set the alarm rules for the metrics. You must add the alarm contact while forming the contact group. The alarm contact and the contact group is notified immediately when an alarm is triggered in the event of exception. You can create an alarm contact group corresponding to the metric.

## Procedure {#section_wvv_wwp_wdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/) .
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the **Basic Information** page.
4.  Select **Monitoring and Alarms** in the left-side navigation pane.
5.  Select the **Alarms** tab.
6.  Click **Set Alarm Rules** to open the CloudMonitor console.

    **Note:** You can click **Refresh** to manually refresh the current status of the alarm metric.

7.  Select **Alarms** \> **\> Alarm Contacts** in the left-side navigation pane to open the **Alarm Contact Management** page.

    **Note:** When alarm rules are set for the first time, if the alarm notification object is not a contact of the Alibaba Cloud account of RDS, the alarm contact and alarm contact group must be created first. If you have already set the alarm contact and the alarm contact group, go to Step 10.

8.  Click **Create Alarm Contact**.
9.  Enter the alarm contact information on the Set Alarm Contact dialog box, click **Send verification code**, enter the verification code sent to your mailbox, and click **Save**.

    **Note:** 

    -   We recommend that you perform the next step to create the alarm contact group after you add all alarm notification objects.

    -   Click **Edit** to modify a contact, or click **Delete** to delete a contact.

10. On the Alarm Contact Management page, select the Alarm Contact Group tab.
11. Click **Create Alarm Contact Group**.
12. Fill in Group Name and Description, select a contact from the **Existing Contacts**, and click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7953/3108_en-US.png) to add the contact to Selected Contacts, and click **OK**.

    **Note:** On the **Alarm Contact Group** page, you can click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7953/3109_en-US.png) to modify a contact group, click **X** to delete a contact group, or click **Delete** to delete a member in the contact group.

13. After creating the alarm contact group, select **Cloud Service Monitoring** \> **\> ApsaraDB for RDS** in the left-side navigation pane.
14. Select the region of RDS for which the alarm rule is to be set.
15. Find the target instance and click **Alarm Rules** in the **Actions** column.

    The system displays the metrics of the current alarm.

16. Click **Create Alarm Rule** to add new alarm rules.

    **Note:** You can click **Modify**, **Disable**, or **Delete** for the metrics as needed.


