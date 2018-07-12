# Comparison between ApsaraDB for RDS and local databases {#concept_u4w_sy5_tdb .concept}

## Performance comparison {#section_ukk_wy5_tdb .section}

|Item|ApsaraDB for RDS|Database services built on purchased servers|
|----|----------------|--------------------------------------------|
|Service availability|99.95%|You are required to implement your own data protection, master-slave replication, and RAID.|
|Data reliability|99.9999%|You are required to implement your own data protection, master-slave replication, and RAID.|
|System security|Anti-DDoS, malicious traffic cleaning, timely repair of various database security vulnerabilities|You are required to do deployment at high costs and repair database security vulnerabilities independently.|
|Database backup|Automatic backup|Independent backups are possible, but you have to find storage space for backup and regularly validate whether the backup data can be recovered.|
|Software and hardware investment|Pay as you go, with no software and hardware investment|Database servers are rather costly and the license fees for SQL Server have to be paid.|
|System hosting|No hosting fee|A single 2U server costs more than RMB 5,000 RMB/year \(more than 10,000 RMB/year for master and slave servers, if needed\).|
|Maintenance cost|Maintenance not needed|Professional DBAs have to be hired, resulting in high labor cost.|
|Deployment and resizing|Instant activation, fast deployment, auto resizing, activation on demand|Hardware procurement, data center hosting, and host deployment, among other tasks, are required and can be time consuming.|
|Resource utilization rate|Charged based on actual usage, resulting in 100% utilization.|Resource utilization is low if peak traffic is considered.|

## Price comparison {#section_kkj_t1v_tdb .section}

|Item|ApsaraDB for RDS|Database services built on purchased servers|
|----|----------------|--------------------------------------------|
|Costs of hardware, spare parts and accessories|Take the following instance type as an example: An instance with memory of 1,200 MB and storage space of 50 GB \(IOPS is up to 600\) costs 2,040 RMB/year.| -   A minimum of 2 servers are required for the database cluster, and a single server whose IOPS is up to 600 costs approximately 6,000 RMB.
-   An intranet switch is used to connect the front-end Web server \(an inexpensive 1U non-NMS switch costs about 1,000 RMB\). Later hardware damages and replacements take at least 30% of the cost.
-   Hardware cost: \(6,000 × 2 + 1,000\) × 130% = 16,900 RMB

Annual hardware cost: 16,900 RMB/3= 5,633 RMB \(the cost of hardware is calculated over a 3-year depreciation period\)


 |
|Data center hosting fee|It is service provider’s responsibilities, and no hosting fee is required.|The hosting fee for a 1U cabinet is 3,000 RMB/year, and the hosting fee for two 1U servers and a 1U intranet switch is charged.  Data center hosting fees: 3,000 x 3 = 9,000 RMB|
|Bandwidth fee|Communication between ECS and ApsaraDB for RDS in the same region is available through the intranet at no cost.  However, communication between ECS and ApsaraDB for RDS across different regions is available over the Internet at a certain cost for Internet traffic. For more information, see [Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds#pricing).|Available only in the intranet at no cost for Internet traffic.|
|Cost of database maintenance engineers|There is no labor cost, because database maintenance is taken care of by a service provider.|The monthly salary for an entry-level DBA engineer is at least 5,000 RMB/month. If 30% workload for a full-time engineer is needed for the current project: Labor cost: 5,000 × 12× 30% = 18,000 RMB|
|Total annual cost|2,040 RMB/year|32,633 RMB/year|

