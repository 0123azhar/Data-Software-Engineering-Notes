
![[cluster.png]]
Hadoop, Spark, Yarn running on the same cluster will be configured such that each frameworks services runs in different nodes so that they do not compete for resources. 
- Ex: Spark driver should not run on the hdfs name node 
- Yarn resource manager should have a dedicated node 
- Above statements are generally true but not compulsory. 

1. Hadoop - ecosystem with 3 core/basic components - hdfs, map reduce, yarn 
2. Spark - data processing engine 
3. Hive - data warehouse 
4. HDFS - Hadoop distributed file system. files are stored in small chunks of 128MB called "data blocks" which are than replicated. 
5. Ranger - Access control and manage security policies of many components of hadoop ecosystem like hdfs, hive, kafka etc. 
6. Yarn - cluster manager 
7. Delta lake - storage layer on top of hdfs that brings ACID capabilities  
8. Oozie - Scheduling and orchestration tool for spark and map reduce jobs in hadoop ecosystem.  
9. Sqoop - to load and traditional RDBMS to HDFS/hive. Mostly replaced by Spark 
10. Zookeeper - Managing the joining and leaving of nodes, Centralised management and dissemination of configuration information in cluster. Developer almost never interacts with Zookeeper


In production Hadoop clusters, the distribution of services across nodes is carefully planned to optimize performance, resource utilization, and fault tolerance. Here’s a typical layout of how services like HDFS, YARN, Hive, and Spark are distributed across different types of nodes in production:

### 1. **Master Nodes (or Control Nodes)**:
   These nodes manage the overall operations and coordination of the cluster. They generally host the control plane services.

   - **HDFS NameNode**: Responsible for metadata management of the HDFS. Usually, there is one active NameNode, and in a highly available (HA) setup, a standby NameNode is also deployed for failover.
   - **YARN ResourceManager**: Schedules jobs, allocates resources across the cluster, and manages applications running on worker nodes.
   - **Hive Metastore**: Stores metadata about Hive tables (schemas, partitions, locations, etc.). The Hive Metastore typically runs on a separate server but can be hosted on the master node as well.
   - **HiveServer2**: Handles query requests from clients and provides a front-end for Hive queries. In large clusters, HiveServer2 can be deployed on dedicated nodes to handle a higher load.
   - **Secondary NameNode**: Performs checkpoints for the NameNode to prevent the loss of HDFS metadata. It’s generally placed on a different node than the primary NameNode.
   - **Spark History Server (optional)**: Provides a UI to inspect the history of completed Spark applications.

   #### Number of Master Nodes:
   - Typically, there are **2–3 master nodes** to ensure high availability for services like the NameNode, ResourceManager, and Hive Metastore.

### 2. **Worker Nodes (or Slave Nodes)**:
   These nodes do the actual processing and storage of data.

   - **HDFS DataNode**: Stores the actual data blocks. Worker nodes are primarily responsible for data storage in HDFS.
   - **YARN NodeManager**: Responsible for launching and monitoring containers (where tasks run). It communicates with the ResourceManager.
   - **Spark Executors**: These run on worker nodes to process data in parallel when you submit a Spark job. Executors handle the actual execution of tasks.
   - **MapReduce Tasks**: If running MapReduce jobs, these will execute on worker nodes.
   
   #### Number of Worker Nodes:
   - In production, there can be anywhere from **dozens to hundreds of worker nodes**, depending on the size of the cluster and data processing needs. More worker nodes are required to handle a higher volume of data and parallel processing.

### 3. **Edge Nodes (or Gateway Nodes)**:
   Edge nodes serve as entry points for users to interact with the cluster. These nodes are typically not involved in actual data storage or processing but serve as gateways for job submission.

   - **Client Tools**: These nodes host clients for services like Spark, Hive, HDFS, etc. Users submit jobs and queries through these tools.
   - **Spark Driver**: The driver for Spark jobs may run on the edge node or an application master node in the cluster.
   - **Hive Client**: Users submit Hive queries from the edge node, and the execution happens on the worker nodes.

   #### Number of Edge Nodes:
   - Edge nodes are often **1–3** per production cluster. In some setups, they are replicated for high availability.

### 4. **Dedicated Nodes (Optional)**:
   In large clusters, some services are moved to dedicated nodes to balance the load, improve performance, and ensure scalability.

   - **Hive Metastore and HiveServer2**: These may run on dedicated nodes, especially in environments with heavy Hive usage.
   - **Zookeeper**: Used for cluster coordination, especially in HA setups. Zookeeper nodes are usually dedicated and run on separate servers (typically 3 or 5 nodes for fault tolerance).
   - **Spark Thrift Server**: For handling JDBC/ODBC requests to Spark SQL, this can also run on dedicated nodes in production environments.

### Typical Distribution of Services Across Node Types:

| **Service**          | **Master Node** | **Worker Node** | **Edge Node** | **Dedicated Node** |
|----------------------|-----------------|-----------------|---------------|--------------------|
| HDFS NameNode        | ✓               |                 |               |                    |
| HDFS DataNode        |                 | ✓               |               |                    |
| YARN ResourceManager | ✓               |                 |               |                    |
| YARN NodeManager     |                 | ✓               |               |                    |
| Hive Metastore       | ✓               |                 |               | ✓                  |
| HiveServer2          | ✓               |                 |               | ✓                  |
| Spark Executors      |                 | ✓               |               |                    |
| Spark Driver         |                 |                 | ✓             |                    |
| Secondary NameNode   | ✓               |                 |               |                    |
| Zookeeper            |                 |                 |               | ✓                  |

### Production Considerations:
1. **High Availability (HA)**: 
   - **HDFS**: Active and standby NameNodes ensure failover and availability. Zookeeper is used for leader election in HA setups.
   - **YARN**: The ResourceManager can also be set up in an HA mode.
   
2. **Separation of Concerns**: In larger clusters, master services (like the NameNode, ResourceManager, and Hive Metastore) may be separated to avoid overloading any single node.
   
3. **Load Balancing**: Worker nodes are designed to scale horizontally. More nodes can be added as the data and processing load increases.

4. **Security**: Edge nodes often have additional security measures to ensure that only authorized users can submit jobs or access data in the cluster.

By separating services across these different types of nodes, production Hadoop clusters can be scalable, fault-tolerant, and efficient, enabling the handling of massive datasets with high availability and performance.