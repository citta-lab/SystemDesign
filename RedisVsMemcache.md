
# Which one to Pick ?
## Use Redis 
- when we need persistence data store 
- when we have complex data types like strings, hash, set, sorted list, bitmaps 
- when we need to use CLUSTER mode
- when we need to RANK in-memory dataset
- when we need failover scenario ( automatic failover to secondary node )
- when we need data replication for READ INTENSIVE applications 
- when we need more storage size ( i.e 512 MB )
- when we need control over LRU eviction 

## Use Memcache 
- when we need simple data store 
- when we need to support large application with multiple cores/threads 
- when we need to SCALE OUT/IN based on the demand 
- when data persistence is not a must ( may loose data if crashed )
- When we need to cache Objects ( no other data types are supported )
