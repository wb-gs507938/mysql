# Public parameters {#reference_krn_wkh_12b .reference}

## Public request parameters {#section_l21_v32_12b .section}

Public request parameters refer to the request parameters that every interface must use.

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Format|String|No|Type of the returned value. Values: JSON and XML. Default value: JSON.|
|Version|String|Yes|API version number. Format: YYYY-MM-DD \(date\). The current version number is 2016-11-01.|
|AccessKeyId|String|Yes|Secret key ID issued by Alibaba for user access|
|Signature|String|Yes|Signature result string. For more information about the signature calculation method, see [Signature](intl.en-US/API Reference/Use APIs/Signature.md#).|
|SignatureMethod|string|Yes|Signature method. Currently, HMAC-SHA1 is supported.|
|Timestamp|String|Yes|Timestamp of a request. The date format follows the ISO8601 standard and uses UTC time. Format: `YYYY-MM-DDThh:mm:ssZ`, for example, `2013-08-15T12:00:00Z` \(20:00:00, August 15, 2013, Beijing time\).|
|SignatureVersion|String|Yes|Signature algorithm version. The current version is 1.0|
|SignatureNonce|String|Yes|Unique random number, used to prevent replay attacks. Different random numbers are used for different requests.|

## Public return parameters {#section_qzx_w32_12b .section}

Each time the you sends a call request to an interface, the system returns a unique identification code \(RequestId\) no matter whether the request is successful or not.

## Request example {#section_hgz_vpn_12b .section}

```
https://rds.aliyuncs.com/
Format=xml
&Version=2014-08-15
&Signature=Pc5WB8gokVn0xfeu%2FZV%2BiNM1dgI%3D 
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&OwnerId=12345678
&Timestamp=2014-10-10T12:00:00Z
```

## Returned results {#section_jyq_1qn_12b .section}

After the API service is called, data is returned in a unified format. The returned HTTP status code 2xx indicates that the call is successful. The returned HTTP status code 4xx or 5xx indicates that the call fails. For successful calls, the primary formats of returned data are XML and JSON. When a request is sent, an external system can generate a parameter to define the format of returned data, which is XML by default. In this document, examples of returned results are formatted in a way that is easier to view. The actual returned results do not contain line breaks and indentation.

**Successful results**

**Returned XML results include the request processing result \(successful or failed\) and the specific service data. Example:**

```
<? xml version="1.0" encoding="utf-8"? > 
<!—Result Root Node-->
<Interface Name+Response>
    <!—Return Request Tag-->
    <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
    <!—Returned Result Data-->
</Interface Name+Response>
```

**JSON format:**

```

    "RequestId": "4C467B38-3910-447D-87BC-AC049166F216",
    /* Returned Result Data*/

```

**Error results**

When an error occurs in an interface call, no result is returned. You can refer to [Client error code table](intl.en-US/API Reference/API Reference/Appendix/Client error code table.md#) to identify the error cause.

When an error occurs in a call, the HTTP status code 4xx or 5xx is returned for the HTTP request. The returned message body contains the specific error code and error message. The message body also contains the globally unique RequestId and the requested HostId. If you cannot identify the error cause, contact Alibaba Cloud Customer Service for help and provide the HostId and RequestId for support engineers to solve the problem as quickly as possible.

**XML format:**

```
<? xml version="1.0" encoding="UTF-8"? >
<Error>
   <RequestId>8906582E-6722-409A-A6C4-0E7863B733A5</RequestId>
   <HostId>rds.aliyuncs.com</HostId>
   <Code>UnsupportedOperation</Code>
   <Message>The specified action is not supported.</Message>
</Error>
```

**JSON example:**

```

    "RequestId": "7463B73D-35CC-4D19-A010-6B8D65D242EF",
    "HostId": "rds.aliyuncs.com",
    "Code": "UnsupportedOperation",
    "Message": "The specified action is not supported."

```

