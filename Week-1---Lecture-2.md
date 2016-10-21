#Cloudera VM

We take the sample data in the Relational **MySQL Tables** and use **Sqoop 1** to import them into HDFS, and then with some configuration we will query this data using **Impala**.

**Hive** executes queries using MapReduce Jobs and is slower, while **Impala** does this directly. **Hue** Provides the web base interface to many services on Cloudera.