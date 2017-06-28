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
* *Schedulers* - nodes that manage how the resources are shared among the jobs and jobs are timed
* *Name Nodes* - nodes that maintain *where* a node exists and how to address it

