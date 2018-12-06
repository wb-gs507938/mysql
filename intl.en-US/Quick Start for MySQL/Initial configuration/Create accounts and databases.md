# Create accounts and databases {#concept_jyq_tc5_q2b .concept}

This article describes how to create accounts and databases for an RDS for MySQL instance.

## Account types {#section_b3f_whz_q2b .section}

RDS for MySQL supports two types of database accounts: superuser accounts and standard accounts. You can manage all your accounts and databases on the console. For specific permissions, see [Account permissions](#).

|Account Type|Description|
|------------|-----------|
|**Superuser account**| -   Can only be created and managed through the console or API.
-   Each instance can have only one superuser account, which can be used to manage all databases and standard accounts.
-   Has more permissions than standard accounts and can manage permissions at a more fine-grained level. For example, it can assign table-level query permissions to other accounts.
-   Has permissions on all databases in the instance.
-   Can disconnect the connections established by any other accounts.

 |
|**Standard account**| -   Can be created and managed through the console, API, or SQL statements.
-   Each instance can have more than one accounts. The specific quantity depends on the instance kernel.
-   Need to be manually granted with database permissions.
-   Cannot create or manage other accounts, or disconnect the connections established by other accounts.

 |

## Create the superuser account {#section_wkq_j35_q2b .section}

1.  Log in to the RDS console.
2.  In the upper-left corner of the page, select the region where the instance is located.
3.  Locate the target instance and click the instance ID.
4.  In the left-hand navigation pane, select **Accounts**.
5.  Click **Create Account**.
6.  Set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Database Account**| Fill in the account name. Requirements are as follows:

     -   Consists of 2 to 256 characters.
    -   Begin with a letter and end with a letter or digit.
    -   Consists of lower-case letters, digits, or underscores.
 |
    |**Account Type**|Select **Superuser Account**.|
    |**Password**| Set the account password. Requirements are as follows:

     -   Consists of 8 to 32 characters.
    -   Contain at least three of the following types: upper-case letters, lower-case letters, digits, and special characters !@\#$%^&\*\(\)\_+-=
 |
    |**Re-enter Password**|Enter the password again.|
    |**Note**|Enter relevant information, with up to 256 characters.|

7.  Click **OK**.

## Reset permissions of the superuser account {#section_tnt_dth_w2b .section}

If the superuser account is abnormal \(for example, permissions are unexpectedly recovered\), you can reset the permissions.

1.  Log in to the RDS console.
2.  In the upper-left corner of the page, select the region where the instance is located.
3.  Locate the target instance and click the instance ID.
4.  In the left-hand navigation pane, click **Accounts**.
5.  Click **Reset Account Permissions** for the superuser account.
6.  Enter the superuser account password to reset the account permissions.

## Create a standard account {#section_nym_xr5_q2b .section}

1.  Log in to the RDS console.
2.  In the upper-left corner of the page, select the region where the instance is located.
3.  Locate the target instance and click the instance ID.
4.  In the left-hand navigation bar, click **Accounts**.
5.  Click **Create Account**.
6.  Set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Database Account**| Fill in the account name. Requirements are as follows:

     -   Consists of 2 to 256 characters.
    -   Begin with a letter and end with a letter or digit.
    -   Consists of lower-case letters, digits, or underscores.
 |
    |**Account Type**|Select **Standard Account**.|
    |**Authorized Database**|Grant database permissions to this account. You can also leave this field blank and grant permissions to the account after the account is created.    1.  Select one or more databases from the left, and click **Authorize** to add to the right.
    2.  In the right-hand box, select **Read/Write**, **Read-only**, **DDL Only**, or **DML Only**.

If you want to set the same permissions for multiple databases at the same time, click the button \(such as **Grant All Read/Write**\) in the upper-right corner of the right-hand box.

**Note:** The button in the upper-right corner changes as you click.

|
    |**Password**| Set the account password. Requirements are as follows:

     -   Consists of 8 to 32 characters.
    -   Contain at least three of the following types: upper-case letters, lower-case letters, digits, and special characters !@\#$%^&\*\(\)\_+-=
 |
    |**Re-enter Password**|Enter the password again.|
    |**Note**|Enter relevant information, with up to 256 characters.|

7.  Click **OK**.

## Create a database {#section_efz_yt5_q2b .section}

Each instance can have up to 500 databases.

1.  Log in to the RDS console.
2.  In the upper-left corner of the page, select the region where the instance is located.
3.  Locate the target instance and click the instance ID.
4.  In the left-side navigation pane, click **Databases**.
5.  Click **Create Database**.
6.  Set the following parameters.

    |Parameters|Description|
    |----------|-----------|
    |**Database Name**|     -   Begin with letters and end with letters or numbers;
    -   Contian only lowercase letters, digits, underscores \(\_\), and hyphens \(-\);
    -   The length is 2-256 characters.
    -   Each table name in an instance must be unique.
 |
    |**Supported Character Set**|Select utf8, gbk, latin1, or utf8mb4.If you need a different character set, select **all**, and then select from the list.

|
    |**Authorized Account**|Select the account that needs to access this database. You can also leave this field blank and set the authorized account after the database is created.**Note:** Only standard accounts are displayed, because the superuser account already has permissions for all databases.

|
    |**Remarks**|Enter relevant information, with up to 256 characters.|

7.  Click **OK**.

## Account permissions {#section_qgv_4q5_tfb .section}

|Account Type|Permission|Permission|
|------------|----------|----------|
|**Superuser account**|-|SELECT|INSERT|UPDATE|DELETE|CREATE|
|DROP|RELOAD|PROCESS|REFERENCES|INDEX|
|ALTER|CREATE TEMPORARY TABLES|LOCK TABLES|EXECUTE|REPLICATION SLAVE|
|REPLICATION CLIENT|CREATE VIEW|SHOW VIEW|CREATE ROUTINE|ALTER ROUTINE|
|CREATE USER|EVENT|TRIGGER| | |
|**Standard account**|**Read-only**|SELECT|LOCK TABLES|SHOW VIEW|PROCESS|REPLICATION SLAVE|
|REPLICATION CLIENT| | | | |
|**Read/write**|SELECT|INSERT|UPDATE|DELETE|CREATE|
|DROP|REFERENCES|INDEX|ALTER|CREATE TEMPORARY TABLES|
|LOCK TABLES|EXECUTE|CREATE VIEW|SHOW VIEW|CREATE ROUTINE|
|ALTER ROUTINE|EVENT|TRIGGER|PROCESS|REPLICATION SLAVE|
|REPLICATION CLIENT| | | | |
|**DDL only**|CREATE|DROP|INDEX|ALTER|CREATE TEMPORARY TABLES|
|LOCK TABLES|CREATE VIEW|SHOW VIEW|CREATE ROUTINE|ALTER ROUTINE|
|PROCESS|REPLICATION SLAVE|REPLICATION CLIENT| | |
|**DML only**|SELECT|INSERT|UPDATE|DELETE|CREATE TEMPORARY TABLES|
|LOCK TABLES|EXECUTE|SHOW VIEW|EVENT|TRIGGER|
|PROCESS|REPLICATION SLAVE|REPLICATION CLIENT| | |

