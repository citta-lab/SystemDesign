
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
- when we need to support large application with multiple cores/threads ( Memcached outperforms Redis for storing data of 100k or above )
- when we need to SCALE OUT/IN based on the demand 
- when data persistence is not a must ( may loose data if crashed )
- When we need to cache Objects ( no other data types are supported )

# Memcache vs Redis 
|       | Memcache | Redis |
| ----------- | ----------- |----------- |
| Core      | Multi Core  | Single Core  |
| Key/Value pair size      | 1MB  | 512MB  |
| Replication      | No  | Yes  |
| Pub/Sub Support      | No  | Yes  |
| Auto Failover | No | Yes |


# Use Cases 
## Redis 
- Caching ( Database query results caching, persistent session caching, web page caching, and caching of frequently used objects such as images, files etc )
- Chat / Messaging ( pub/sub model )
- Session Store ( manage session data such as user profiles, credentials, session state, and user-specific personalization )
- Media Streaming ( store users metadata about users' profiles and viewing histories, authentication information/tokens for millions of users, and manifest files to enable CDNs to stream videos to millions of mobile and desktop users at a time )
- Leader Board (Redis Sorted Set data structure, which provides uniqueness of elements while maintaining the list sorted by users' scores )

## Memcache 
- Caching ( same as redis cache )
- Session Store (manage session data such as user profiles, credentials, and session state.) 
