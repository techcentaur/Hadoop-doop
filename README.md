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
