1.	Explain in detail about HDFS :

HDFS is the primary distributed storage used by Hadoop applications. A HDFS cluster primarily consists of a NameNode that manages the file system metadata and DataNodes that store the actual data. The HDFS Architecture Guide describes HDFS in detail. This user guide primarily deals with the interaction of users and administrators with HDFS clusters. The HDFS architecture diagram depicts basic interactions among NameNode, the DataNodes, and the clients. Clients contact NameNode for file metadata or file modifications and perform actual file I/O directly with the DataNodes.

The following are some of the salient features that could be of interest to many users.

•	Hadoop, including HDFS, is well suited for distributed storage and distributed processing using commodity hardware. It is fault tolerant, scalable, and extremely simple to expand. MapReduce, well known for its simplicity and applicability for large set of distributed applications, is an integral part of Hadoop.
•	HDFS is highly configurable with a default configuration well suited for many installations. Most of the time, configuration needs to be tuned only for very large clusters.
•	Hadoop is written in Java and is supported on all major platforms.
•	Hadoop supports shell-like commands to interact with HDFS directly.
•	The NameNode and Datanodes have built in web servers that makes it easy to check current status of the cluster.







2.	Explain in detail about Hadoop Cluster :

The three types of node groups in a Hadoop deployment are master nodes, worker nodes, and client nodes. Master nodes oversee the following key operations that comprise Hadoop: storing data in the Hadoop Distributed File System (HDFS) and running parallel computations on that data using MapReduce. The NameNode coordinates the data storage function (with the HDFS), while the JobTracker oversees and coordinates the parallel processing of data using MapReduce.

Worker nodes make up the majority of virtual machines and perform the job of storing the data and running computations. Each worker node runs both a DataNode and TaskTracker service that communicates with, and receives instructions from their master nodes. The TaskTracker service is subordinate to the JobTracker, and the DataNode service is subordinate to the NameNode.

Client nodes have Hadoop installed with all the cluster settings, but are neither master nor worker nodes. Instead, the client node loads data into the cluster, submits MapReduce jobs describing how that data should be processed, and then retrieves or views the results of the job when processing is finished.















3.	Explain about HDFS Blocks : 

Hadoop distributed file system also stores the data in terms of blocks. However the block size in HDFS is very large. The default size of HDFS block is 64MB. The files are split into 64MB blocks and then stored into the Hadoop filesystem. The Hadoop application is responsible for distributing the data blocks across multiple nodes.

The main reason for having the HDFS blocks in large size is to reduce the cost of seek time. In general, the seek time is 10ms and disk transfer rate is 100MB/s. To make the seek time 1% of the disk transfer rate, the block size should be 100MB. The default size HDFS block is 64MB. 

•	Advantages of HDFS Block

The benefits with HDFS block are: 

o	The blocks are of fixed size, so it is very easy to calculate the number of blocks that can be stored on a disk.
o	HDFS block concept simplifies the storage of the datanodes. The datanodes doesn’t need to concern about the blocks metadata data like file permissions etc. The namenode maintains the metadata of all the blocks.
o	If the size of the file is less than the HDFS block size, then the file does not occupy the complete block storage.
o	As the file is chunked into blocks, it is easy to store a file that is larger than the disk size as the data blocks are distributed and stored on multiple nodes in a Hadoop cluster.
o	Blocks are easy to replicate between the datanodes and thus provide fault tolerance and high availability. Hadoop framework replicates each block across multiple nodes (default replication factor is 3). In case of any node failure or block corruption, the same block can be read from another node.

