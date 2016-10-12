## Hadoop Stack Basics

Apache Hadoop is Open Source software framework for storage and large-scale processing of data-sets. 
(Apache License)

Hadoop moves computation to data instead of the other way round. 

**Scalability** is at the core of it.<br/>
**Reliability** (hardware failures are handled automatically).

## The Apache Framework

**4 basic components:**

1. **Hadoop Common**: Libraries and utilities needed by other Hadoop Components <br/>
2. **HDFS**: high bandwidth distributed storage <br/>
3. **Hadoop Yarn**: Manages computer resources and uses them to schedule users and applications <br/>
4. **Hadoop MapReduce**: Programming model that scales data across different processes <br/>
All the modules are designed with the scalability and reliability in mind.<br/>

**Other components:**

* **Pig**: Scripting <br/>
* **HBase**: Non relational database <br/>
* **Oozie**: Workflow manager <br/>
* **Hive**: SQL Query <br/>
* **Sqoop**: Data Exchange <br/>

## Hadoop Distributed File System (HDFS)
High bandwidth distributed file system **written in Java** for the Hadoop Framework. It can stores file of sizes GB, TB, PB.

Each machine in the cluster has a **single name-node** and a **group of data-nodes** that form the HDFS. With each name-node, there is also a **secondary name-node**. This is **not** a backup or failsafe for the name-node. What it does is it regularly creates snapshots of the primary name-node, directory information etc and allows the primary name-node to work faster.

### Secondary Name Node: 
The namenode stores the HDFS filesystem information in a file named fsimage. Updates to the file system (add/remove blocks) are not updating the fsimage file, but instead are logged into a file, so the I/O is fast append only streaming as opposed to random file writes. When restaring, the namenode reads the fsimage and then applies all the changes from the log file to bring the filesystem state up to date in memory. This process takes time.

The secondarynamenode job is not to be a secondary to the name node, but only to periodically read the filesystem changes log and apply them into the fsimage file, thus bringing it up to date. This allows the namenode to start up faster next time.

Reference: [Name node Vs Secondary name node](http://stackoverflow.com/questions/19970461/name-node-vs-secondary-name-node)
More Information: [Secondary Namenode - What it really do?](http://blog.madhukaraphatak.com/secondary-namenode---what-it-really-do/)


## The Hadoop "Zoo"

## Hadoop Ecosystem Major Components