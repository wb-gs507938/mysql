# Get a file upload address {#reference_t52_1bm_12b .reference}

## Description {#section_l21_v32_12b .section}

**Note:** This API is only applicable to SQL Server instance.

Create the account and password for file server logon and the path information for files to be uploaded. The user can upload data files based on the preceding information. When the upload is completed, the user can call the data import interface to migrate external data. The restrictions are as follows:

-   Instance status: active.

-   Database status: active.

-   Up to 20 files can be created for a single database every day. A 24-hour period is considered as a single day. For example, if the last creation time was 2012-03-15 18:30:12, the next creation time must be later than 2012-03-16 18:30:12.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: CreateUploadPathForSQLServer.|
|DBInstanceId|String|Yes|Instance ID.|
|DBName|String|Yes|Name of a database.|

## Response parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US//Public parameters.md#).|
|InternetFtpServer|String|File server on the Internet.|
|InternetPort|Integer|Port number on the file server on the Internet.|
|IntranetFtpServer|String|IP address of the server on the intranet.|
|IntranetPort|Integer|Port number on the server on the Intranet.|
|UserName|String|Account used to log on to the file server.|
|Password|String|Password used to log on to the file server.|
|FileName|String|File name, with the extension.|

## Example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action= CreateUploadPathForSQLServer
&DBInstanceId=rianeurbfaeuq2u2a1370572118496
&DBName=testdb01
&<Public request parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<CreateUploadPathForSQLServerResponse>
       <RequestId>66816822-CEC1-4C8D-AB26-2530A7D4DCA5</RequestId>
       <InternetFtpServer>10.230.239.1</InternetFtpServer>
       <InternetPort>3021</InternetPort>
       <IntranetFtpServer></IntranetFtpServer>
       <IntranetPort></IntranetPort>
       <UserName>MKEakJbyG</UserName>
       <Password>aT2Y_XN1GGnOLzm</Password>
       <FileName>testdb01_1370572475975.bak</FileName>
</CreateUploadPathForSQLServerResponse>
```

**JSON format**

```

       "RequestId":"66816822-CEC1-4C8D-AB26-2530A7D4DCA5"
       "InternetFtpServer ":"10.230.239.1"
       "InternetPort":3021
       "IntranetFtpServer":""
       "IntranetPort":
       "UserName":"MKEakJbyG"
       "Password":"aT2Y_XN1GGnOLzm"
       "FileName":"testdb01_1370572475975.bak"

```

