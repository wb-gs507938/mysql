# Limits {#concept_zvw_n1g_wdb .concept}

To guarantee instance stability and security, ApsaraDB for PostgreSQL has the following restrictions.

|Operations|RDS restrictions|
|----------|----------------|
|Modify database parameter settings|Currently it is not supported.|
|Database root permission|RDS does not offer the superuser permission.|
|Database backup|Data backup can only be performed through pg\_dump.|
|Data migration|Data backed up by pg\_dump can only be restored through psql.|
|Build database replication| The system automatically builds the HA mode based on PostgreSQL stream replication.

 The PostgreSQL Standby node is invisible and cannot be accessed directly.

 |
|Restart the RDS instance|The instance must be restarted through the RDS console or OPEN API.|
|Network setting|If the [access mode](../../../../intl.en-US/User Guide/Network management/Set access mode.md#) of the instance is safe connection mode, enabling net.ipv4.tcp\_timestamps in SNAT mode is not allowed.|

