# High-availability service {#concept_tph_vbv_tdb .concept}

The high-availability service consists of several modules including the Detection, Repair, and Notification modules. In combination, these modules guarantee the availability of the data link services and process any internal database exception.

In addition, RDS can improve the performance of its high-availability service by migrating to a region that supports multiple zones and by adopting the appropriate high-availability policies.

## Detection {#section_ngf_xbv_tdb .section}

The Detection module checks whether the master and slave nodes of the DB Engine offer their services normally. The HA \(High Available\) node uses heartbeat information, acquired at an interval of 8 to 10 seconds, to check the health status of the master node. This information, combined with the health status of the slave node and heartbeat information from other HA nodes, allows the Detection module to eliminate any risk of misjudgment caused by exceptions such as network jitter and allows that the exception switchover can be completed within 30 seconds.

## Repair {#section_ogf_xbv_tdb .section}

The Repair module maintains the replication relationship between the master and slave nodes of the DB Engine. It can also repair any errors that may occur on either node.

For example:

-   Automatic restoration of master/slave replication in case of disconnection
-   Automatic repair of table-level damage to the master or slave nodes
-   On-site saving and automatic repair if the master or slave nodes crash

## Notice {#section_qgf_xbv_tdb .section}

The Notice module informs the SLB or Proxy of status changes to the master and slave nodes to guarantee that you can continue to access the correct node.

For example, the Detection module discovers that the master node has an exception and instructs the Repair module to fix it. If the Repair module fails to resolve the problem, it directs the Notification module to initiate traffic switching. The Notification module then forwards the switching request to the SLB or Proxy, which begins to redirect all traffic to the slave node. Simultaneously, the Repair module creates a new slave node on another physical server and synchronizes this change back to the Detection module. The Detection module then incorporates this new information and starts to recheck the health status of the instance.

## Multi-zone {#section_rgf_xbv_tdb .section}

Multi-zone refers to the physical area that is formed by combining multiple individual zones within the same region. Multi-zone RDS instances can withstand higher level disasters than single-zone instances. For example, a single-zone RDS instance can withstand server and rack failures, while a multi-zone RDS instance can survive a situation such as failure of an entire data center.

Currently no extra charge for multi-zone RDS instances is generated. Users in a region where multi-zone is enabled can purchase multi-zone RDS instances directly or convert single-zone RDS instances into multi-zone RDS instances by using inter-zone migration.

**Note:** Multiple zones may have a certain amount of network latency. As a result, when a multi-zone RDS instance uses a semi-synchronous data replication solution, its response time to any individual update may be longer than that of a single-zone instance. In this case, the best way to improve overall throughput is to increase concurrency.

