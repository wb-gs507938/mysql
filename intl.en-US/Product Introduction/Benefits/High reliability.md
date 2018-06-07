# High reliability {#concept_c3s_4y5_tdb .concept}

## Hot standby {#section_w3n_ry5_tdb .section}

RDS uses hot standby, so if a physical server fails, the service is switched over in seconds  without interruptions to application services.

## Multi-copy redundancy {#section_x3n_ry5_tdb .section}

The data in RDS server is built on RAID, and the data backup is stored on OSS.

## Data backup {#section_y3n_ry5_tdb .section}

RDS offers an automatic backup mechanism.  You can set a backup schedule or initiate a temporary backup at any time. For more information, see [Backup recovery](https://www.alibabacloud.com/help/zh/doc-detail/53622.htm).

## Data recovery {#section_z3n_ry5_tdb .section}

Data can be recovered from a backup.  Generally, data can be recovered within 7 days to a temporary RDS instance.  After the data is verified, the data can be migrated back to the master RDS instance. For more information, see [Backup recovery](https://www.alibabacloud.com/help/zh/doc-detail/53622.htm).

