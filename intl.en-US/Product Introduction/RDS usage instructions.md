# RDS usage instructions {#concept_pvm_hd2_vdb .concept}

-   Instructions for RDS instance upgrade

    There is a transient disconnection of up to 30 seconds during RDS instance upgrade. To avoid service unavailability caused by interruptions, you must make preparations in advance and set auto-reconnection for the program and to RDS.

-   Risks of intranet/Internet switchover

    During the switchover between the intranet and Internet, RDS may be disconnected with the server and the RDS IP address may change. After the switchover, update the connection address in the program in a timely manner.

-   Rollback risks

    Currently, RDS only supports data rollback for the entire instance but not for a single table or database. It is important to make backups of crucial data before rollback to prevent data loss. If you need to roll back only partial tables or partial data, we recommend that you recover the data by creating a temporary instance or a clone instance. After a temporary instance or a clone instance is created successfully, the required data is directed returned to the production database. For more information, see [Recover data to the master instance through a temporary instance](../../../../intl.en-US/User Guide/Backup and recovery/Recover SQL Server/PPAS/PostgreSQL data/Recover data to the master instance through a temporary instance.md#).

-   Instructions on RDS locking policies

    Currently, RDS only supports data rollback for the entire instance, not for a single table or database. It is important to make backups of crucial data before rollback to prevent data loss. We recommend that you create a temporary instance for data recovery if you only want to roll back part of the tables or part of the data. You must import the required data back to the production databases from the temporary instance. For more information, see [Recover data to the master instance through a temporary instance](../../../../intl.en-US/User Guide/Backup and recovery/Recover SQL Server/PPAS/PostgreSQL data/Recover data to the master instance through a temporary instance.md#).

-   Instructions on RDS failover

    RDS adopts a master-slave mode to guarantee high availability. When the master node fails, RDS fails services over to the slave node within 30 seconds. During the failover, there may be an inaccessible period of \(less than or equal to\) 30 seconds. You must set auto-reconnection for your program to RDS to avoid service unavailability.

-   Instructions on data synchronization mode for MySQL instances

    -   For MySQL 5.1, data synchronization between the master and slave nodes is in asynchronous mode. This mode guarantees high performance of instances, but it may lead to probabilistic data inconsistency between the master and slave nodes.

    -   For MySQL 5.5, data synchronization between the master and slave nodes is in semi-synchronous mode. This mode compromises write performance to some extent, but it can greatly reduce the probability of data inconsistency between the master and slave databases. If you have a high requirement on data reliability \(for example, financial systems\), we recommend that you purchase instances of MySQL 5.5 or later versions.

    -   For MySQL 5.6, data synchronization between the master and slave nodes uses GTID \(a new feature in MySQL 5.6\). This feature guarantees both the performance and data consistency.

-   Notes of attentions for using RDS

    After purchasing an RDS instance, you do not need to conduct basic O&M \(such as high availability guarantee, backup, and security patches\) for databases. Pay attention to the following matters:

    -   Check whether the CPU, IOPS, space, and the number of connections of your RDS instance are adequate. If not, you must optimize or upgrade your instance.
    -   Check whether your RDS instance has performance problems, for example, whether there is a large number of slow SQL queries, whether the SQL statements need optimization, and whether there are extra or missing indexes.
    -   Check whether your RDS instance has any web SQL injection warnings. If so, your databases may be vulnerable to web SQL injections. In this case, modify the application to prevent web SQL injection attacks.

