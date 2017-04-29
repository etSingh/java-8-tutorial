### Intro to spark

+ Expressive - API modelled on scala Immutable collections, easy to reason about in a Distributed Setting
+ Performant - Way faster than Hadoop
+ Good for Data Science - Enables iteration without any boilerplate as in Hadoop

### Data-Parallel to Distributed Data-Parallel

```scala
 val res = jar.map(jellyBean => doSomething(jellyBean))
 ```
 
 #### Shared Memory Data Parallelism
 + Split the data
 + Workers/threads independently operate on the data shards in parallel
 + Combine when done (if necessary)
 
 *Scala's Parallel Collections is a collections abstraction over shared memory data-parallel execution*
 
 
 #### Distributed Data Parallelism
 + Split the data *over several nodes*
 + ~~Workers/threads~~ Nodes independently operate on the data shards in parallel
 + Combine when done (if necessary)
 *Now we have to worry about network latency between the nodes, however, we can still keep the collection abstraction over distributed nodes*
 
 ## RDD - Resilient Distributed Datasets - Apache Spark's Distributed Data parallel model
 
 #### High Level Overview of Spark functionality
 Given a large dataset, like wikipedia (48 GB) that cant fit into the memory of a single machine
 + Chunk up the data using a partitioning mechanism
 + Distribute it over a set of nodes
 + From there, think of your data as a single collection even though it is hosted on distributed machines 
 
 ```scala
 val wiki: RDD[wikiArticle]: ...
 wiki.map( article => article.text.toLowerCase)
 ```
 ___
 
 
 ### Latency
 
 Additional complexity introduced in distributed computation -
 + Node Churning (Partial failure) - Nodes involved in computation can go down
 + Latency - Specially operations involving network latency (Cannot be masked completely, has an impact on the programming model)
 
 Spark handles the above two issues very well
 
 Reading 1 MB sequentially from memory - 20 micro seconds
 Reading 1 MB sequentially from disk - 20 milli seconds
 *100 times difference in time taken*
 
 Broadly
 + Memory opertions - Fastest
 + Disk operations - slow
 + Network operations - slowest
 Network operations are a million times slower than memory operations for more perspective, check (Humanized Latency Numbers)[https://gist.github.com/hellerbarde/2843375]
 
 
 
