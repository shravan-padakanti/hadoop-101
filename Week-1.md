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

Each machine in the cluster has a **single active name-node** which stores the HDFS meta-data and a **group of data-nodes** which store the actual data. With each name-node, there is also a **secondary name-node** which regularly creates snapshots of the primary name-node, directory information etc and allows the primary name-node to work faster. Together these nodes across the cluster form the HDFS.

### Secondary Name Node: 
The name-node stores the HDFS filesystem information and meta-data in a file named **fsimage**. Updates to the file system (add/remove blocks) are not updating the fsimage file, but instead are logged into a separate "edit-log" file, so the I/O is fast append only streaming as opposed to random file writes. When restaring, the namenode reads the fsimage and then applies all the changes from the log file to bring the filesystem state up to date in memory. This process takes time.

The secondarynamenode job is not to be a secondary to the name node, but only to periodically read the filesystem changes log and apply them into the fsimage file, thus bringing it up to date. This allows the namenode to start up faster next time.

Reference: [Name node Vs Secondary name node](http://stackoverflow.com/questions/19970461/name-node-vs-secondary-name-node) <br/>
More Information: [Secondary Namenode - What it really do?](http://blog.madhukaraphatak.com/secondary-namenode---what-it-really-do/)

## Engines used in Hadoop

### Hadoop MapReduce engine
At the core of every hadoop based system there is some version of a MapReduce engine. (There are some other engines developed, but still use MapReduce at its core, eg. YARN). A **job** is a execution of full-program (from mapping to reducing) across a set of data. A **task** is execution of either the map or the reduce function on a slice of data. The Hadoop Map Reduce Engine consists of a **job-tracker** which keeps a track of the jobs submitted by managing resources (task trackers) and task life cycles.

![](https://github.com/rohitvg/CourseraHadoop/blob/master/resources/images/MapReduceEngineOverview.png)

### Hadoop Nextgen MapReduce engine (YARN)
YARN stands for "Yet Another Resource Negotiator" is a cluster-manager. It was introduced to generalize HDFS to work with different technologies and not just Map Reduce. Thus, it is not just constrained or limited to only Map and Reduce processes but also supports other processes like Graph Processing, Machine Learning, etc, while still being fully compatible with MapReduce. It also separates resource management and the processes components and allows better cluster utilization. 

![](https://github.com/rohitvg/CourseraHadoop/blob/master/resources/images/yarn.png)

## The Hadoop "Zoo"

## Hadoop Ecosystem Major Components