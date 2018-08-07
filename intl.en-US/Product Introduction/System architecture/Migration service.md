# Migration service {#concept_crr_3dv_tdb .concept}

The migration service can migrate data from a local database to ApsaraDB, or migrate an ApsaraDB instance to another. ApsaraDB includes a Data Transfer Service \(DTS\) tool to facilitate quick database migration.

DTS is a cloud data transfer service for efficient instance migration from local databases to the cloud, and between RDS instances. For more information, see [DTS product overview](https://www.alibabacloud.com/help/doc-detail/26592.htm).

DTS provides three migration modes, that is, structure migration, full migration, and incremental migration:

-   Structure migration: DTS migrates the structure definitions of migration objects to the target instance. Currently, tables, views, triggers, stored procedures, and stored functions can be migrated in this mode.

-   Full migration: DTS migrates all existing data of migration objects in source databases to the target instance.

-   Incremental migration: DTS synchronizes data changes made in the migration process to the target instance.


