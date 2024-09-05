#### Spark architecture
Driver process/program
Executer
Application master
Cluster manage: yarn, Kubernetes, spark standalone
#### Execution modes in Yarn
###### client mode
Driver runs in client machine/process and the application master is only used for requesting resources from Yarn (Cluster manager)
![[client_mode.png]]
###### cluster mode
Spark driver runs inside an application master process which is managed by yarn and client goes away after initiating the application.
![[cluster_mode.png]]
###### Local![[local_mode.png]]
![]() 

 
What happens to a spark program if one of the nodes fails  

Spark dataframe partition: dataframe is split and stored in different executers in cluster nodes as partitions. we can split df into partition based on a column using `partitionBy("country")`
#### Spark Architecture 
![]() 
Spark Ecosystem 
![]() ![[ecosystem.png]]

When spark reads a file from HDFS, the number of partitions of an rdd depends on the number of blocks the file is split into.
![[shuffle.png]]


- Actions examples: count, write etc 
- Narrow transformation: filter, concat etc. 
- Wide transformations: join, group by etc.
![[executors.png]]



