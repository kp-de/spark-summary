## Spark Architecture Summary

Driver   
  * One Per Application  
     
Executor  
  * One JVM  
  * Works for one Application  
  * One App can have many executors  
  * 0 to many executors possible on any machine in the cluster  
  
Planning Phase  
  * Compilation from DF/ SQL to RDD transformations  
  * Compilation from RDD transformations into a DAG  
  * Creation of logical plan: DAG + transformation sequence  
  * Creation of physical plan: optimized sequence of steps for cluster nodes  
  
Job  
  * Has 1 or more stages  
  
Stage  
  * All computations between two shuffles  
  
Task  
  * Run by one executor  
  * processing one partition  
  * each Task takes up one Thread, and is assumed to be assigned to one core
  * Multiple tasks can run concurrently within an Executor (multiple threads)
  
We should always look to minimize number of stages in our jobs because each new stage means shuffle  

Shuffle: Data Exchange between two executors  

Narrow Transformations : partitions do not need to know about each other, e.g. map, flaatmap, filter, projection  

Wide Transformations: All partitions need to be considered, resulting in shuffles. e.g. group by, joining, sorting, RDD/ DF structure changes. 
 
 
