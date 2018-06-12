# View the database file list {#reference_ifs_4bm_12b .reference}

## Description {#section_l21_v32_12b .section}

**Note:** This API is only applicable to SQL Server instances.

View the file list on the file server. You can use the “Getting a File Upload Address” interface to obtain the account required to upload files to the file server. RDS updates the data file status after data files are uploaded. The user can use the “Viewing the Database File List” interface to check whether data files are available. If files are available, the user can import data and obtain information about the import process.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeFilesForSQLServer.|
|DBInstanceId|String|Yes|Instance ID.|
|StartTime|String|Yes|Query start time, for example, 2011-06-11T15:00Z.|
|EndTime|String|Yes|Query end time, which must be later than the query start time, for example, 2011-06-11T16:00Z.|
|PageSize|Integer|No|Number of records on every page. Values: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|Page number, which must be greater than 0, but must not exceed the maximum Integer value. Default value: 1.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBInstanceId|String|Instance ID.|
|TotalRecordCount|Integer|Total number of records.|
|PageNumber|Integer|Page number.|
|PageRecordCount|Integer|Number of SQL statements displayed on the current page.|
|Items| ```
List<SQLServerUploadFile>
```

 |None.|

## SQLServerUploadFile parameters {#section_tcz_tbm_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBName|String|Name of a database.|
|FileName|String|Data file name, with the extension.|
|FileSize|Long|Data file size, in the unit of bytes.|
|InternetFtpServer|String|File server.|
|InternetPort|Integer|Port number on the file server.|
|IntranetFtpserver|String|IP address of the server on the intranet.|
|Intranetport|Integer|Port number on the server on the Intranet.|
|UserName|String|Account used to log on to the file server.|
|Password|String|Password used to log on to the file server.|
|FileStatus|String|File status. Values:-   Unavailable
-   Available
-   NotStarted
-   Uploading
-   UploadFailed
-   Virus
-   Deleted
-   Success

|
|CreationTime|String|FTP file generation time. Format: YYYY-MM-DD’T’HH:mm:ssZ, for example, 2011-05-30 T12:11:4Z.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeFilesForSQLServer
&DBInstanceId=rianeurbfaeuq2u2a1370572118496
&StartTime=2014-06-11T15:00Z
&EndTime=2014-06-11T16:00Z
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
< DescribeFilesForSQLServerResponse> 
  <RequestId>08A3B71B-FE08-4B03-974F-CC7EA6DB1828</RequestId>
<TotalRecordCount>1</TotalRecordCount>
<PageNumber>1</PageNumber>
<PageRecordCount>1<PageRecordCount>
<Items>
<SQLServerUploadFile>
<DBName>testdb01</DBName>
<FileName>testdb01_1370572475975.bak</FileName>
<FileSize>1243435</FileSize>
       <InternetFtpServer>10.230.239.1</InternetFtpServer>
       <InternetPort>3021</InternetPort>
       <IntranetFtpServer></IntranetFtpServer>
       <IntranetPort></IntranetPort>
       <UserName>MKEakJbyG</UserName>
<Password>aT2Y_XN1GGnOLzm</Password>
<FileStatus>Success</FileStatus>
<CreationTime>2014-06-11T15:02:40Z</CreationTime>
</SQLServerUploadFile>
</Items>
</DescribeFilesForSQLServerResponse>
```

**JSON format**

```

"PageNumber":1,
"TotalRecordCount":1,
"PageRecordCount":1
"Items":
{"Maid ":


"DBName":"testdb01"
"FileName":"testdb01_1370572475975.bak"
"FileSize ":"1243435"
         "InternetFtpServer ":"10.230.239.1"
         "InternetPort":3021
         "IntranetFtpServer":""
         "IntranetPort":
         "UserName":"MKEakJbyG"
         "Password":"aT2Y_XN1GGnOLzm"
"Filestaris": "success"
"CreationTime": "2014-06-11T15:02:40Z"
 


"RequestId": "08A3B71B-FE08-4B03-974F-CC7EA6DB1828"

```

