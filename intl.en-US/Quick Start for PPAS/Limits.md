# Limits {#concept_u5s_f4g_wdb .concept}

To guarantee the instance stability and security, ApsaraDB for PPAS has the following restrictions.

|Operation|Description|
|---------|-----------|
|Modify database parameter settings|Currently not supported|
|Database root permission|RDS does not offer the superuser permission to users.|
|Database backup|You can back up data only through pg\_dump.|
|Data migration to the cloud|You can only use psql to restore data backed up by pg\_dump.|
|Set up database replication| -   You do not need to set up data replication because the system has automatically set up PPAS stream replication based the HA mode.
-   The PPAS slave node is invisible to users, and cannot be used directly for access.

 |
|Restart an RDS instance|You must restart an instance through the [RDS console](https://rds.console.aliyun.com/) or APIs.|
|Network settings|If the [access mode](../../../../intl.en-US/User Guide/Network management/Set access mode.md#) of the instance is safe connection mode, enabling net.ipv4.tcp\_timestamps in SNAT mode is not allowed.|

