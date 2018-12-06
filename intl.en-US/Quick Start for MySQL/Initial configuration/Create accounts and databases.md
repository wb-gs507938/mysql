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
5.  Click Create account.
6.  Set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Database Account**| Fill in the account name. The requirements are as follows:

     -   Begin with letters and end with letters or numbers;
    -   Consists of lower case letters, numbers, or underscores;
    -   The length is 2-256 characters.
 **Note:** If the account name of the High-privilege account you created is the same as that of the existing regular account, the original ordinary account will be replaced with the high-privilege account.

 |
    |**Belongs to Current Account**|Select a high-privilege account here.|
    |**Password**| Set the account password. The requirements are as follows:

     -   By the capital letter, the lower case letter, the number, the special character in any three kinds of composition;

Special characters! @\#$%^&\*\(\)\_+-=。

    -   Length is 8 ~ 32 characters.

 |
    |**Confirm password**|Enter the password again.|
    |**Remarks**|Note the relevant information of this account, so as to facilitate the follow-up account management. Supports a maximum of 256 characters.|

7.  Click **OK**.

## Reset account privileges {#section_tnt_dth_w2b .section}

If there is a problem with the high-privilege account itself, for example, permissions have been unexpectedly recovered \), you can recover through a reset of account permissions.

1.  Log in to the RDS console.
2.  In the upper-left corner of the page, select the region of the instance.
3.  Locate the target instance and click the instance id.
4.  In the left-hand navigation bar, click Account Management.
5.  Click Reset Account permissions to the right of the High-privilege account.
6.  Enter the High-privilege account password to reset the account permissions.

## Create a regular account {#section_nym_xr5_q2b .section}

1.  Log in to the RDS console.
2.  In the upper-left corner of the page, select the region of the instance.
3.  Locate the target instance and click the instance id.
4.  In the left-hand navigation bar, click Account Management.
5.  Click Create account.
6.  Set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Database Account**| Fill in the account name. The requirements are as follows:

     -   Begin with letters and end with letters or numbers;
    -   Consists of lower case letters, numbers, or underscores;
    -   The length is 2-256 characters.
 |
    |**Belongs to Current Account**|Choose a regular account here.|
    |**Authorization Database**|Grant permissions to one or more databases for this account. This parameter can be left blank, after account creation and account authorization.    1.  Select one or more databases from the left, and click grant to add to the right.
    2.  In the right-hand box, select read-write, read-only, pant, or DML for a database.

If you want to set the same permissions for multiple databases in bulk, click the button in the upper-right corner of the right-hand box, if all are set to read and write.

**Note:** The button in the upper-right corner changes as you click. For example, when you click Set read and write all, the button becomes read-only in all settings.

|
    |**Password**| Set the account password. The requirements are as follows:

     -   By the capital letter, the lower case letter, the number, the special character in any three kinds of composition;

Special characters! @\#$%^&\*\(\)\_+-=。

    -   Length is 8 ~ 32 characters.
 |
    |**Confirm password**|Enter the password again.|
    |**Remarks**|Non-mandatory. Note the relevant information of this account, so as to facilitate the follow-up account management. Supports a maximum of 256 characters.|

7.  Click **OK**.

## Create a database {#section_efz_yt5_q2b .section}

Each instance can create up to 500 databases.

1.  Log in to the RDS console.
2.  In the upper-left corner of the page, select the region of the instance.
3.  Locate the target instance and click the instance id.
4.  Click the required instance to go to its Basic Information page, and then in the left-side navigation pane, click Databases.
5.  Click Create Database.
6.  Set the following parameters.

    |Parameters|Description|
    |----------|-----------|
    |**Database \(DB\) name**|     -   Begin with letters and end with letters or numbers;
    -   Contian only lowercase letters, digits, underscores \(\_\), and hyphens \(-\);
    -   The length is 2-256 characters.
    -   Each table name in an instance must be unique.
 |
    |**Support character set**|Select utv8, GBK, Latin1, or fig.If you need a different character set, select all, and then select the desired character set from the list.

|
    |**Authorized account number**|Select the account that you want to access this database. This parameter can be left blank and the account can be bound after the database has been created.**Note:** The regular account is displayed here only, because the high-privilege account has all the permissions for all databases, no authorization is required.

|
    |**Belongs to Current Account**|Select the permissions that you want to grant to your account: read-write, read-only, pant-only, or DML-only.|
    |**Remarks**|Non-mandatory. You can enter related information of the database to facilitate subsequent database management. You can enter a maximum of 256 English characters.|

7.  Click **OK**.

## List of account privileges {#section_qgv_4q5_tfb .section}

|Belongs to Current Account|Authorization type|Permission|
|--------------------------|------------------|----------|
|**a high-privilege account.**|-|SELECT|INSERT|UPDATE|DELETE|CREATE|
|DROP|Reload|Process|References|INDEX|
|ALTER|Create maid tables|Lock tables|EXECUTE|Replication slave|
|Replication Client|CREATE VIEW|Show View|Create routine|Alter routine|
|CREATE USER|Event|Trigger| | |
|**Ordinary account**|**Read-only**|SELECT|Lock tables|Show View|Process|Replication slave|
|Replication Client| | | | |
|**Read/write**|SELECT|INSERT|UPDATE|DELETE|CREATE|
|DROP|References|INDEX|ALTER|Create maid tables|
|Lock tables|EXECUTE|CREATE VIEW|Show View|Create routine|
|Alter routine|Event|Trigger|Process|Replication slave|
|Replication Client| | | | |
|**Div only**|CREATE|DROP|INDEX|ALTER|Create maid tables|
|Lock tables|CREATE VIEW|Show View|Create routine|Alter routine|
|Process|Replication slave|Replication Client| | |
|**DML only**|SELECT|INSERT|UPDATE|DELETE|Create maid tables|
|Lock tables|EXECUTE|Show View|Event|Trigger|
|Process|Replication slave|Replication Client| | |

