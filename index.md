# The Big Data Menagerie
The goal here is to break away from the fancy terminology and provide a simple way of thinking about the big data technology set as a whole. Many of the terms or statements will sound 'wrong' but that is by design, we really need to focus on gaining intuition about the field and not get bogged down by getting things done 'correctly'. The correctness can be cultivated when we go deeper into the subject and actually implement things.

## Mental Model
It helps to think of the the ecosystem as a distributed computing environment where:
* Lightweight, disposable containers
* work on top of 'ephemeral' virtual machines
* that live on physical infrastructure

## Things that a Big Data ecosystem would need 
A basic setup would need one or more:
* *Workers* - nodes that actually execute the processing task
* *Managers* - nodes that track the jobs
* *Schedulers* - nodes that provide coordination services and may additionally manage how the resources are shared among the jobs
* *Name Nodes* - nodes that maintain *where* a node exists and how to address it

### *additionally*
* *Storage* - to persist the data (S3, local, HDFS, RDBMS, NoSQL etc.)
	* *Data Store* - this is a special case where we care about the structure of the data - so we ask questions like is it columnar or key value or just a stream or documents etc.
	* Storage and data store components come in two flavors *regular* and *in memory*
* *Data Import* - to acquire data into the ecosystem (from other RDBMS, data streams, etc.)
* *Data Query* - ability to run SQL like analysis on the data once it's in the Big Data ecosystem
* *Algorithms* - a library that gives a default implementation of common Statistical and Machine Learning algorithms - understand that these are implemented in a way that best exploits the distributed nature of the entire setup
* *Extensions* - You have a distributed system that can do many many things and not just map-reduce processing on large volumes of data, so you'd need extensions that provide additional functionality 
* *Libraries* - These provide API access to various components in the ecosystem - APIs may be specific to a particular language or may provide support for multiple languages
* *Messaging* - Parts of the distributed system would pass messages and enable data flow - from one process to another, from one node to another, from one cluster to another. A message queue or a message broker would take care of this task. Popular implementations are ZeroMQ (or 0mq) and RabbitMQ. 

## Stacks
A typical Hadoop stack: *this is a stand in diagram, a better one will appear here*
![Hadoop Stack](images/hadoop_stack.png)

A typical Spark stack: *this is a stand in diagram, a better one will appear here*
![Spark Stack](images/spark.png)

The following were taken from https://hadoopecosystemtable.github.io/ and will be replaced by more informed, intuitive text.

* Storm - Storm is a complex event processor (CEP) and distributed computation framework written predominantly in the Clojure programming language. Is a distributed real-time computation system for processing fast, large streams of data. Storm is an architecture based on master-workers paradigma. So a Storm cluster mainly consists of a master and worker nodes, with coordination done by Zookeeper. 
* Spark - Data analytics cluster computing framework originally developed in the AMPLab at UC Berkeley. Spark fits into the Hadoop open-source community, building on top of the Hadoop Distributed File System (HDFS). However, Spark provides an easier to use alternative to Hadoop MapReduce and offers performance up to 10 times faster than previous generation systems like Hadoop MapReduce for certain applications.
* Flume - Flume is a distributed, reliable, and available service for efficiently collecting, aggregating, and moving large amounts of log data. It has a simple and flexible architecture based on streaming data flows. It is robust and fault tolerant with tunable reliability mechanisms and many failover and recovery mechanisms. It uses a simple extensible data model that allows for online analytic application.
* Sqoop - System for bulk data transfer between HDFS and structured datastores as RDBMS. Like Flume but from HDFS to RDBMS.	
* Pig - An engine for executing data flows in parallel on Hadoop. It includes a language, Pig Latin, for expressing these data flows. Pig Latin includes operators for many of the traditional data operations (join, sort, filter, etc.), as well as the ability for users to develop their own functions for reading, processing, and writing data. Pig runs on Hadoop.
* Hive - *SQL-On-Hadoop*. Data Warehouse infrastructure developed by Facebook. Data summarization, query, and analysis. It’s provides SQL-like language (not SQL92 compliant): HiveQL.
* Mahout - Machine learning library and math library, on top of MapReduce. Written in Java.
* Impala - The Apache-licensed Impala project brings scalable parallel database technology to Hadoop, enabling users to issue low-latency SQL queries to data stored in HDFS and Apache HBase without requiring data movement or transformation. It's a Google Dremel clone (Big Query google).
* HBase - Google BigTable Inspired. Non-relational distributed database. Ramdom, real-time r/w operations in column-oriented very large tables (BDDB: Big Data Data Base). It’s the backing system for MR jobs outputs. It’s the Hadoop database. It’s for backing Hadoop MapReduce jobs with Apache HBase tables.
* YARN - *(not from hadoopecosystemtable)* Provides cluster management features for the Hadoop ecosystem. This is akin to the dll loader mechanism found in Windows.
* Mesos - Mesos is a cluster manager that provides resource sharing and isolation across cluster applications. Mesos is hadoop centred design
* Marathon - Marathon is a Mesos framework for long-running services. Given that you have Mesos running as the kernel for your datacenter, Marathon is the init or upstart daemon.
* Kafka - Distributed publish-subscribe system for processing large amounts of streaming data. Kafka is a Message Queue developed by LinkedIn that persists messages to disk in a very performant manner. 
* ZeroMQ - *(not from hadoopecosystemtable)* ZeroMQ (also spelled ØMQ, 0MQ or ZMQ) is a high-performance asynchronous messaging library, aimed at use in distributed or concurrent applications. It provides a message queue, but unlike message-oriented middleware, a ZeroMQ system can run without a dedicated message broker. The library's API is designed to resemble that of Berkeley sockets.
* RabbitMQ - *(not from hadoopecosystemtable)* RabbitMQ is open source message broker software (sometimes called message-oriented middleware) that implements the Advanced Message Queuing Protocol (AMQP). The RabbitMQ server is written in the Erlang programming language and is built on the Open Telecom Platform framework for clustering and failover. Client libraries to interface with the broker are available for all major programming languages.
* Zookeeper - ZooKeeper is a high-performance coordination service for distributed applications. It exposes common services - such as naming, configuration management, synchronization, and group services - in a simple interface so you don't have to write them from scratch. You can use it off-the-shelf to implement consensus, group management, leader election, and presence protocols. And you can build on it for your own, specific needs. ZooKeeper was developed at Yahoo! Research. Several Hadoop projects are already using ZooKeeper to coordinate the cluster and provide highly-available distributed services. 
* Oozie - Workflow scheduler system for MR jobs using DAGs (Direct Acyclical Graphs). Oozie Coordinator can trigger jobs by time (frequency) and data availability.
