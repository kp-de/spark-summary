## Deployment Nodes  

### Cluster Mode  
  * Driver on a worker node on the cluster  
  * Cluster Manager manages spark processes  
  
  Pros:  
    * Faster communication between driver and executors  
    * More resources available for driver (assuming nodes of cluster have resources)  
    
  Cons:  
    * Node failure kills application, if node with driver crashes  
      
### Client Mode  
  * Driver on the client machine  
  * Client responsible for Spark processes & state management  
  * Executors on cluster  
  
  Pros:  
    * Node failures do not fail app  
    
  Cons:    
    * Slower communication between driver and executor  
    * fewer resources for driver  
  
### Local   
  * Everything on client machine  
  
  
