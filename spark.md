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
