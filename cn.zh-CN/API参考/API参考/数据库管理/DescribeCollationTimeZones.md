# DescribeCollationTimeZones {#reference_vxw_v1f_sfb .reference}

查看RDS for SQL Server 2012或以上版本实例的系统库支持的字符集排序规则和时区。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 系统规定参数，取值：

 DescribeCollationTimeZones。

 |

## 返回参数 {#section_axs_2bf_sfb .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|详见[公共参数](https://help.aliyun.com/document_detail/26224.html)。|
|Items|List|支持的字符集排序规则和时区列表。|

## Item参数 {#section_lff_4bf_sfb .section}

|名称|类型|描述|
|--|--|--|
|TimeZone|String|时区|
|Collation|String|字符集|
|Description|String|描述|

## 示例 {#section_ssp_rbf_sfb .section}

**请求示例**

```
https://rds.aliyuncs.com/?Action=DescribeCollationTimeZones
```

**返回示例**

**JSON格式**

```
{
 "CollationTimeZones": {
   "CollationTimeZone": [
     {
       "StandardTimeOffset": "(UTC+04:30)",
       "Description": "Kabul",
       "TimeZone": "Afghanistan Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC–09:00)",
       "Description": "Alaska",
       "TimeZone": "Alaskan Standard Time"
     },
     {
       "StandardTimeOffset": "Arabian Standard Time",
       "Description": "Abu Dhabi, Muscat",
       "TimeZone": "(UTC+04:00)"
     },
     {
       "StandardTimeOffset": "(UTC-04:00)",
       "Description": "Atlantic Time (Canada)",
       "TimeZone": "Atlantic Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+09:30)",
       "Description": "Darwin",
       "TimeZone": "AUS Central Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+10:00)",
       "Description": "Canberra,Melbourne,Sydney",
       "TimeZone": "AUS Eastern Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+03:00)",
       "Description": "Minsk",
       "TimeZone": "Belarus Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-06:00)",
       "Description": "Saskatchewan",
       "TimeZone": "Canada Central Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-01:00)",
       "Description": "Cabo Verde Is.",
       "TimeZone": "Cape Verde Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+09:30)",
       "Description": "Adelaide",
       "TimeZone": "Cen.Australia Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-06:00)",
       "Description": "Central America",
       "TimeZone": "Central America Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+06:00)",
       "Description": "Astana",
       "TimeZone": "Central Asia Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-04:00)",
       "Description": "Cuiaba",
       "TimeZone": "Central Brazilian Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+01:00)",
       "Description": "Belgrade, Bratislava, Budapest, Ljubljana, Prague",
       "TimeZone": "Central Europe Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+01:00)",
       "Description": "Sarajevo, Skopje, Warsaw, Zagreb",
       "TimeZone": "Central European Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+11:00)",
       "Description": "Solomon Islands, New Caledonia",
       "TimeZone": "Central Pacific Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC–06:00)",
       "Description": "Central Time (US and Canada)",
       "TimeZone": "Central Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-06:00)",
       "Description": "Guadalajara, Mexico City, Monterrey",
       "TimeZone": "Central Standard Time (Mexico)"
     },
     {
       "StandardTimeOffset": "(UTC+08:00)",
       "Description": "Beijing, Chongqing, Hong Kong, Urumqi",
       "TimeZone": "China Brazilian Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+03:00)",
       "Description": "Nairobi",
       "TimeZone": "E. Africa Brazilian Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+10:00)",
       "Description": "Brisbane",
       "TimeZone": "E. Australia Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+02:00)",
       "Description": "Chisinau",
       "TimeZone": "E. Europe Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-03:00)",
       "Description": "Brasilia",
       "TimeZone": "E. South America Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-05:00)",
       "Description": "Eastern Time (US and Canada)",
       "TimeZone": "Eastern Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+04:00)",
       "Description": "Tbilisi",
       "TimeZone": "Georgian Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC)",
       "Description": "Dublin, Edinburgh, Lisbon, London",
       "TimeZone": "GMT Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-03:00)",
       "Description": "Greenland",
       "TimeZone": "Greenland Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC)",
       "Description": "Monrovia, Reykjavik",
       "TimeZone": "Greenwich Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+02:00)",
       "Description": "Athens, Bucharest",
       "TimeZone": "GTB Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-10:00)",
       "Description": "Hawaii",
       "TimeZone": "Hawaiian Brazilian Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+05:30)",
       "Description": "Chennai, Kolkata, Mumbai, New Delhi",
       "TimeZone": "India Brazilian Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+02:00)",
       "Description": "Amman",
       "TimeZone": "Jordan Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+09:00)",
       "Description": "Seoul",
       "TimeZone": "Korea Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+02:00)",
       "Description": "Beirut",
       "TimeZone": "Middle East Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-07:00)",
       "Description": "Mountain Time (US and Canada)",
       "TimeZone": "Mountain Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-07:00)",
       "Description": "Chihuahua, La Paz, Mazatlan",
       "TimeZone": "Mountain Standard Time (Mexico)"
     },
     {
       "StandardTimeOffset": "(UTC-07:00)",
       "Description": "Arizona",
       "TimeZone": "US Mountain Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+12:00)",
       "Description": "Auckland, Wellington",
       "TimeZone": "New Zealand Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-03:30)",
       "Description": "Newfoundland",
       "TimeZone": "Newfoundland Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-03:00)",
       "Description": "Santiago",
       "TimeZone": "Pacific SA Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-08:00)",
       "Description": "Pacific Time (US and Canada)",
       "TimeZone": "Pacific Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-08:00)",
       "Description": "Baja California",
       "TimeZone": "Pacific Standard Time (Mexico)"
     },
     {
       "StandardTimeOffset": "(UTC+03:00)",
       "Description": "Moscow, St. Petersburg, Volgograd",
       "TimeZone": "Russian Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-05:00)",
       "Description": "Bogota, Lima, Quito, Rio Branco",
       "TimeZone": "SA Pacific Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+07:00)",
       "Description": "Bangkok, Hanoi, Jakarta",
       "TimeZone": "SE Asia Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+08:00)",
       "Description": "Kuala Lumpur, Singapore",
       "TimeZone": "China Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+09:00)",
       "Description": "Osaka, Sapporo, Tokyo",
       "TimeZone": "Tokyo Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC-05:00)",
       "Description": "Indiana (East)",
       "TimeZone": "US Eastern Standard Time"
     },
     {
       "StandardTimeOffset": "UTC",
       "Description": "Coordinated Universal Time",
       "TimeZone": "UTC"
     },
     {
       "StandardTimeOffset": "(UTC-02:00)",
       "Description": "Coordinated Universal Time–02",
       "TimeZone": "UTC–02"
     },
     {
       "StandardTimeOffset": "(UTC-08:00)",
       "Description": "Coordinated Universal Time–08",
       "TimeZone": "UTC–08"
     },
     {
       "StandardTimeOffset": "(UTC-09:00)",
       "Description": "Coordinated Universal Time–09",
       "TimeZone": "UTC–09"
     },
     {
       "StandardTimeOffset": "(UTC-11:00)",
       "Description": "Coordinated Universal Time–11",
       "TimeZone": "UTC–11"
     },
     {
       "StandardTimeOffset": "(UTC+12:00)",
       "Description": "Coordinated Universal Time+12",
       "TimeZone": "UTC+12"
     },
     {
       "StandardTimeOffset": "(UTC+08:00)",
       "Description": "Perth",
       "TimeZone": "W. Australia Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+01:00)",
       "Description": "West Central Africa",
       "TimeZone": "W. Central Africa Standard Time"
     },
     {
       "StandardTimeOffset": "(UTC+01:00)",
       "Description": "Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna",
       "TimeZone": "W. Europe Standard Time"
     }
   ]
 },
 "RequestId": "4EAED246-DB18-4C8D-9EB5-C319626F2A77"
}
```

