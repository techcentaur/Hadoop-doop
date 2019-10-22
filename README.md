# Hadoop-Distributed-File-System (HDFS)

Here I will summarize the paper of HDFS, because it's really cool, and pin down the steps that I used to set it up on my system.

### [Architecture Guide](https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html)

# 1. Introduction
- HDFS, is a distributed file system, and it runs on commondity hardware.
- Highly fault-tolerant and designed to be deployed on low-cost hardware | High throughput access to data -> suitable for large datasets.
- Relaxes POSIX requirements for fast streaming access.

# 2. Assumptions and Goals
- Hardware failure: Assumed to occure often -> fault detection, quick and automatic recovery are essential.
- Streaming data access: For data access -> high throughout > low latency.
- Large data sets: Should work for high aggregate data BW and highly scalable to support large files.
- Simple coherency model: Write-once-read-many enables high throughout and reduced data cohereny issues | once created file needn't changed.
- Moving Computation: Computation efficient if executed near data location -> less network congestion and high throughput.
- Portability: across platforms would remove platform dependency issues.

# 3. NameNode and DataNode

> HDFS has a master/slave architecture.

HDFS Cluster Entities: piece of softwares, typically GNU/Linux OS
	- Single NameNode: a master server:
		- Arbitrator and repository for all HDFS metadata.
		- User data doesn't flow through here.
		- Manages a file system namespace and regulates access to files by clients
		- Executes file operations like opening, closing, and renaming files and directories.
		- Determines the mapping of blocks to DataNodes.
	- Multiple DataNodes: slave servers (usually per node)
		- Manage storage attached to system where they run
		- A file is split in one or more blocks, and these blocks are stored at DataNodes.
		- DataNodes also perform block creation, deletion, and replication upon instructions from NameNode.
		- Responsible for serving read and write requests from the file system's client.

Notes:
	- Multiple instances of DataNode can run on one machine, but rarely the case in real deployment.


# 4. File System Namespace


# 5. Data Replication