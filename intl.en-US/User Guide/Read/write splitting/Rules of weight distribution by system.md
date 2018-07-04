# Rules of weight distribution by system {#concept_oqf_j5p_wdb .concept}

## Weight values list {#section_txj_n5p_wdb .section}

When the read weights are automatically set for instances by the system, the values of these weights are fixed, as shown in the following table:

|Specification code|Specification type|Memory|CPU|Weight|
|------------------|------------------|------|---|------|
|rds.mys2.small|Common Instance|240 MB|3|100|
|rds.mys2.mid|Common Instance|600 MB|5|100|
|rds.mys2.standard|Common Instance|1,200 MB|6|400|
|rds.mys2.large|Common Instance|2,400 MB|9|400|
|rds.mys2.xlarge|Common Instance|6,000 MB|10|800|
|rds.mys2.2xlarge|Common Instance|12,000 MB|10|800|
|rds.mys2.4xlarge|Common Instance|24,000 MB|12|1000|
|rds.mys2.8xlarge|Common Instance|48,000 MB|13|1000|
|rds.mysql.t1.small|Common Instance|1 GB|1|100|
|rds.mysql.s1.small|Common Instance|2 GB|1|100|
|rds.mysql.s2.large|Common Instance|4 GB|2|200|
|rds.mysql.s2.xlarge|Common Instance|8 GB|2|200|
|rds.mysql.s3.large|Common Instance|8 GB|4|400|
|rds.mysql.m1.medium|Common Instance|16 GB|4|400|
|rds.mysql.c1.large|Common Instance|16 GB|8|800|
|rds.mysql.c1.xlarge|Common Instance|32 GB|8|800|
|rds.mysql.c2.xlarge|Common Instance|64 GB|16|1600|
|rds.mysql.c2.xlp2|Common Instance|96 GB|16|1600|
|rds.mysql.c2.2xlarge|Common Instance|128 GB|16|1600|
|mysql.x8.medium.2|Dedicated Instance|16 GB|2|200|
|mysql.x8.large.2|Dedicated Instance|32 GB|4|400|
|mysql.x8.xlarge.2|Dedicated Instance|64 GB|8|800|
|mysql.x8.2xlarge.2|Dedicated Instance|128 GB|16|1600|
|rds.mysql.st.d13|Dedicated Host|220 GB|30|3000|
|rds.mysql.st.h13|Dedicated Host|470 GB|60|6000|

## Specify whether an SQL is sent to the master instance or a read-only instance by using Hint { .section}

In addition to the weight distribution system of read/write splitting, Hint serves as a complementary SQL syntax to specify whether an SQL is executed on the master instance or a read-only instance.

The Hint formats supported by RDS read/write splitting are as follows:

-   `/*FORCE_MASTER*/`: specifies that the SQL is executed on the master instance.
-   `/*FORCE_SLAVE*/`: specifies that the SQL is executed on a read-only instance.

For example, after Hint is prefixed to the following statement, the statement is always routed to and executed on the master instance regardless of the set weight.

`/*FORCE_MASTER*/ SELECT * FROM table_name;`

