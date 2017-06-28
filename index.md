# The Big Data Menagerie

## Mental Model
It helps to think of the the ecosystem as:
* Lightweight, disposable containers
* working on top of 'ephemeral' virtual machines
* that live on physical infrastructure

## Things that a Big Data ecosystem would need 
A basic setup would need one or more:
* *Workers* - nodes that actually execute the processing task
* *Managers* - nodes that track the jobs
* *Schedulers* - nodes that provide coordination services and may additionally manage how the resources are shared among the jobs
* *Name Nodes* - nodes that maintain *where* a node exists and how to address it

### *additionally*
* *Storage* - to persist the data (S3, local, HDFS, RDBMS, NoSQL etc.)
* *Data Import* - to acquire data into the ecosystem (from other RDBMS, data streams, etc.)
* *Data Query* - ability to run SQL like analysis on the data once it's in the Big Data ecosystem
* *