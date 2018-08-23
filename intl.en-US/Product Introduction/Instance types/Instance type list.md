# Instance type list {#reference_lbw_tyw_5db .reference}

## RDS for MySQL {#section_f33_wwz_xdb .section}

|Series|Version|Type|Type code|CPU/Memory|Maximum number of connections|Maximum IOPS|Storage capacity|
|------|-------|----|---------|----------|-----------------------------|------------|----------------|
|Basic Edition|5.7|Common instances|mysql.n1.micro.1|1-core 1 GB|2,000|IOPS=min\{30 x storage capacity, 20,000\}|20 GB - 1000 GB|
|mysql.n2.small.1|1-core 2 GB|2,000|
|mysql.n2.medium.1|2-core 4 GB|4,000|
|mysql.n4.medium.1|2-core 8 GB|6,000|20 GB - 2000 GB|
|mysql.n4.large.1|4-core 16 GB|8,000|
|mysql.n4.xlarge.1|8-core 32 GB|10,000|
|mysql.n4.2xlarge.1|16-core 64 GB|15,000|
|mysql.n4.4xlarge.1|32-core 128 GB|20,000|
|mysql.n8.4xlarge.1|32-core 256 GB| 64,000|
|mysql.n4.8xlarge.1|56-core 224 GB| 64,000|
|mysql.n8.8xlarge.1|56-core 480 GB| 64,000|
|High-availability Edition|5.5/5.6/5.7|Common instances|rds.mysql.t1.small|1-core 1 GB|300|600|5 GB - 2,000 GB|
|rds.mysql.s1.small|1-core 2 GB|600|1,000|
|rds.mysql.s2.large|2-core 4 GB|1,200|2,000|
|rds.mysql.s2.xlarge|2-core 8 GB|2,000|4,000|
|rds.mysql.s3.large|4-core, 8 GB|2,000|5,000|
|rds.mysql.m1.medium|4-core 16 GB|4,000|7,000|
|rds.mysql.c1.large|8-core 16 GB|4,000|8,000|
|rds.mysql.c1.xlarge|8-core 32 GB|8,000|12,000|
|rds.mysql.c2.xlarge|16-core 64 GB|16,000|14,000|5 GB - 3,000 GB|
|rds.mysql.c2.xlp2|16-core 96 GB|24,000|16,000|
|Dedicated instances \(with large memory\)|mysql.x8.medium.2|2-core 16 GB|2,500|4,500|250 GB|
|mysql.x8.large.2|4-core 32 GB|5,000|9,000|500 GB|
|mysql.x8.xlarge.2|8-core 64 GB|10,000|18,000|1,000 GB|
|mysql.x8.2xlarge.2|16-core 128 GB|20,000|36,000|2,000 GB or 3,000 GB|
|Dedicated instances \(with high CPU\)|mysql.x4.large.2|4-core 16 GB|2,500|4,500|250 GB or 500 GB|
|mysql.x4.xlarge.2|8-core 32 GB|5,000|9,000|500 GB or 1,000 GB|
|mysql.x4.2xlarge.2|16-core 64 GB|10,000|18,000|1,000 GB, 2,000 GB or 3,000 GB|
|mysql.x4.4xlarge.2|32-core 128 GB|20,000|36,000|2,000 GB or 3,000 GB|
|Dedicated-host instances|rds.mysql.st.d13|30-core 220 GB| 64,000|20,000|3,000 GB|
|rds.mysql.st.h43|60-core 470 GB|100,000|50,000|3,000 GB|
|Financial Edition \(formerly: Three-node Enterprise Edition\)|5.6|Dedicated instances \(with high CPU\)|mysql.x4.large.3|4-core 16 GB|2,500|4,500|250 GB or 500 GB|
|mysql.x4.xlarge.3|8-core 32 GB|5,000|9,000|500 GB or 1,000 GB|
|mysql.x4.2xlarge.3|16-core 64 GB|10,000|18,000|1,000 GB, 2,000 GB or 3,000 GB|
|mysql.x4.4xlarge.3|32-core 128 GB|20,000|36,000|2,000 GB or 3,000 GB|
|Dedicated instances \(with large memory\)|mysql.x8.medium.3|2-core 16 GB|2,500|4,500|250 GB|
|mysql.x8.large.3|4-core 32 GB|5,000|9,000|500 GB|
|mysql.x8.xlarge.3|8-core 64 GB|10,000|18,000|1,000 GB|
|mysql.x8.2xlarge.3|16-core 128 GB|20,000|36,000|2,000 GB or 3,000 GB|
|mysql.x8.4xlarge.3|32-core 256 GB|40,000|72,000|3,000 GB|
|Dedicated-host instances|mysql.st. 8xlarge.3|60-core 470 GB|100,000|120,000|3,000 GB|
|Read-only instance|5.6/5.7|Common instances|rds.mysql.t1.small|1-core 1 GB|300|600|5 GB - 2,000 GB|
|rds.mysql.s1.small|1-core 2 GB|600|1,000|
|rds.mysql.s2.large|2-core 4 GB|1,200|2,000|
|rds.mysql.s2.xlarge|2-core 8 GB|2,000|4,000|
|rds.mysql.s3.large|4-core, 8 GB|2,000|5,000|
|rds.mysql.m1.medium|4-core 16 GB|4,000|7,000|
|rds.mysql.c1.large|8-core 16 GB|4,000|8,000|
|rds.mysql.c1.xlarge|8-core 32 GB|8,000|12,000|
|rds.mysql.c2.xlarge|16-core 64 GB|16,000|14,000|5 GB - 3,000 GB|
|rds.mysql.c2.xlp2|16-core 96 GB|24,000|16,000|
|Dedicated instances \(with large memory\)|mysqlro.x8.medium. 1|2-core 16 GB|2,500|4,500|250 GB|
|mysqlro.x8.large.1|4-core 32 GB|5,000|9,000|500 GB|
|mysqlro.x8.xlarge.1|8-core 64 GB|10,000|18,000|1,000 GB|
|mysqlro.x8.2xlarge.1|16-core 128 GB|20,000|36,000|2,000 GB or 3,000 GB|
|Dedicated instances \(with high CPU\)|mysqlro.x4.large.1|4-core 16 GB|2,500|4,500|250 GB or 500 GB|
|mysqlro.x4.xlarge.1|8-core 32 GB|5,000|9,000|500 GB or 1,000 GB|
|mysqlro.x4.2xlarge.1|16-core 64 GB|10,000|18,000|1,000 GB, 2,000 GB or 3,000 GB|
|mysqlro.x4.4xlarge.1|32-core 128 GB|20,000|36,000|2,000 GB or 3,000 GB|
|Dedicated-host instances|rds.mysql.st.d13|30-core 220 GB| 64,000|20,000|3,000 GB|

## RDS for SQL Server {#section_ptf_rwz_xdb .section}

|Series|Version|Type|Type code|CPU/Memory|Maximum number of connections|Maximum IOPS|Storage capacity|
|------|-------|----|---------|----------|-----------------------------|------------|----------------|
|Basic Edition|2012 Enterprise \(formerly 2012\)|Common instances|rds.mssql.s2.large|2-core 4 GB|Not limited|IOPS=min\{30 x storage capacity, 20,000\}|20 GB - 2000 GB|
|rds.mssql.s2.xlarge|2-core 8 GB|
|rds.mssql.s3.large|4-core, 8 GB|
|rds.mssql.m1.medium|4-core 16 GB|
|rds.mssql.c1.large|8-core 16 GB|
|rds.mssql.c1.xlarge|8-core 32 GB|
|rds.mssql.c2.xlarge|16-core 64 GB|
|2012/2016 Web|Dedicated instances|mssql.x2.medium.w1|2-core 4 GB|Not limited|IOPS=min\{30 x storage capacity, 20,000\}|20 GB - 2000 GB|
|mssql.x2.large.w1|4-core, 8 GB|
|mssql.x2.xlarge.w1|8-core 16 GB|
|mssql.x2.2xlarge.w1|16-core 32 GB|
|mssql.x4.medium.w1|2-core 8 GB|
|mssql.x4.large.w1|4-core 16 GB|
|mssql.x4.xlarge.w1|8-core 32 GB|
|mssql.x4.2xlarge.w1|16-core 64 GB|
|High-availability Edition|2008 R2 Enterprise|Common instances|rds.mssql.s1.small|1-core 2 GB|600|1,000|10 GB - 2,000 GB|
|rds.mssql.s2.large|2-core 4 GB|1,200|2,000|
|rds.mssql.s2.xlarge|2-core 8 GB|2,000|4,000|
|rds.mssql.s3.large|4-core, 8 GB|2,000|5,000|
|rds.mssql.m1.medium|4-core 16 GB|4,000|7,000|
|rds.mssql.c1.large|8-core 16 GB|4,000|8,000|
|rds.mssql.c1.xlarge|8-core 32 GB|8,000|12,000|
|rds.mssql.c2.xlarge|16-core 64 GB|16,000|14,000|
|rds.mssql.c2.xlp2|16-core 96 GB|24,000|16,000|
|Dedicated instances|mssql.x8.medium.2|2-core 16 GB|2,500|4,500|250 GB|
|mssql.x8.large.2|4-core 32 GB|5,000|9,000|500 GB|
|mssql.x8.xlarge.2|8-core 64 GB|10,000|18,000|1,000 GB|
|mssql.x8.2xlarge.2|16-core 128 GB|20,000|36,000|2,000 GB|
|Dedicated-host instances|rds.mssql.st.d13|30-core 220 GB| 64,000|20,000|2,000 GB|
|rds.mssql.st.h43|60-core 470 GB|100,000|50,000|2,000 GB|

## RDS for PostgreSQL { .section}

|Series|Version|Type|Type code|CPU/Memory|Maximum number of connections|Maximum IOPS|Storage capacity|
|------|-------|----|---------|----------|-----------------------------|------------|----------------|
|High-availability Edition|9.4|Common instances|rds.pg.t1.small|1-core 1 GB|100|600|5 GB - 2,000 GB|
|rds.pg.s1.small|1-core 2 GB|200|1,000|
|rds.pg.s2.large|2-core 4 GB|400|2,000|
|rds.pg.s3.large|4-core, 8 GB|800|5,000|
|rds.pg.c1.large|8-core 16 GB|1,500|8,000|
|rds.pg.c1.xlarge|8-core 32 GB|2,000|12,000|
|rds.pg.c2.xlarge|16-core 64 GB|2,000|14,000|
|Dedicated instances \(with large memory\)|pg.x8.medium. 2|2-core 16 GB|2,500|4,500|250 GB|
|pg.x8.large.2|4-core 32 GB|5,000|9,000|500 GB|
|pg.x8.xlarge.2|8-core 64 GB|10,000|18,000|1,000 GB|
|pg.x8.2xlarge.2|16-core 128 GB|12,000|36,000|2,000 GB|
|Dedicated instances \(with high CPU\)|pg.x4.large.2|4-core 16 GB|2,500|4,500|250 GB or 500 GB|
|pg.x4.xlarge.2|8-core 32 GB|5,000|9,000|500 GB or 1,000 GB|
|pg.x4.2xlarge.2|16-core 64 GB|10,000|18,000|1,000 GB or 2,000 GB|
|pg.x4.4xlarge.2|32-core 128 GB|12,000|36,000|2,000 GB or 3,000 GB|
|Dedicated-host instances|rds.pg.st.d13|30-core 220 GB|4,000|20,000|3,000 GB|
|rds.pg.st.h43|60-core 470 GB|4,000|50,000|3,000 GB|

## RDS for PPAS {#section_xzc_fhx_5db .section}

|Series|Version|Type|Type code|CPU/Memory|Maximum number of connections|Maximum IOPS|Storage capacity|
|------|-------|----|---------|----------|-----------------------------|------------|----------------|
|High-availability Edition|9.3 / 10|Common instances|rds.ppas.t1.small|1-core 1 GB \(for compatibility testing\)|100|1,200|150 GB|
|Dedicated instances|ppas.x4.small.2|1-core 4 GB|200|5,000|250 GB|
|ppas.x4.medium.2|2-core 8 GB|400|10,000|
|ppas.x8.medium.2|2-core 16 GB|2,500|15,000|
|ppas.x4.large.2|4-core 16 GB|2,500|20,000|250 GB or 500 GB|
|ppas.x8.large.2|4-core 32 GB|5,000|30,000|
|ppas.x4.xlarge.2|8-core 32GB|5,000|40,000|250 GB or 500 GB|
|ppas.x8.xlarge.2|8-core 64 GB|10,000|60,000|
|ppas.x4.2xlarge.2|16-core 64 GB|10,000|80,000|250 GB or 500 GB|
|ppas.x8.2xlarge.2|16-core 128 GB|12,000|120,000|
|ppas.x4.4xlarge.2|32-core 128 GB|12,000|160,000|2000 GB or 3000 GB|
|ppas.x8.4xlarge.2|32-core 256 GB|12,000|240,000|
|Dedicated-host instances|rds.ppas.st.h43|60-core 470 GB|12,000|450,000|

## Historical instance types of RDS for MySQL {#section_bpx_khx_5db .section}

The following table lists the historical instance types of RDS for MySQL. They are no longer available when you create a new instance.

|Type code|Number of CPU cores|Memory|Maximum number of connections|Maximum IOPS|
|---------|-------------------|------|-----------------------------|------------|
|rds.mys2.small|2|240 MB|60|150|
|rds.mys2.mid|4|600 MB|150|300|
|rds.mys2.standard|6|1,200 MB|300|600|
|rds.mys2.large|8|2,400 MB|600|1,200|
|rds.mys2.xlarge|9|6,000 MB|1,500|3,000|
|rds.mys2.2xlarge|10|12,000 MB|2,000|6,000|
|rds.mys2.4xlarge|11|24,000MB|2,000|12,000|
|rds.mys2.8xlarge|13|48,000 MB|2,000|14,000|

## Historical instance types of RDS for SQL Server {#section_c3f_shx_5db .section}

The following table lists the historical instance types of RDS for SQL Server. They are no longer available when you create a new instance.

|Type code|Number of CPU cores|Memory|Maximum number of connections|Maximum IOPS|
|---------|-------------------|------|-----------------------------|------------|
|rds.mss1.small|6|1,000 MB|100|500|
|rds.mss1.mid|8|2,000 MB|200|1,000|
|rds.mss1.standard|9|4,000 MB|400|2,000|
|rds.mss1.large|10|6,000 MB|600|3,000|
|rds.mss1.xlarge|11|8,000 MB|800|4,000|
|rds.mss1.2xlarge|12|12,000 MB|1,200|6,000|
|rds.mss1.4xlarge|13|24,000MB|2,000|12,000|
|rds.mss1.8xlarge|13|48,000 MB|2,000|14,000|

## Historical instance types of RDS for PPAS {#section_lph_jhd_x2b .section}

The following table lists the historical instance types of RDS for PPAS. They are no longer available when you create a new instance.

|Type code|Number of CPU cores|Memory|Maximum number of connections|Maximum IOPS|
|---------|-------------------|------|-----------------------------|------------|
|rds.ppas.s1.small|1|2 GB|200|1,000|
|rds.ppas.s2.large|2|4 GB|400|2,000|
|rds.ppas.s3.large|4|8 GB|800|5,000|
|rds.ppas.m1.medium|4|16 GB|1,500|8,000|
|rds.ppas.c1.xlarge|8|32 GB|2,000|12,000|
|rds.ppas.c2.xlarge|16|64 GB|2,000|14,000|

