
# Title : Key Value Store

Example: Dynamo
Example Database: DynamoDB

## Main Goal
- High Availability over Consistency i.e no leader/master node
- Eventual Consistency instead of 100% consistency 
- Highly Scalable 

## Trade Off
- Data Consistency as it will be eventual consistency 

## Design 
### 1. Data Partioning 
- Using Consistency Hashing : All data nodes are connected in a ring and each nodes are responsible for storing data within certain range. ex: 0-25, 25-50, etc. 
- MD5 : data keys are hashed using MD5 in "consistency hashing" to determine the range it belongs to.
- To avoid "hotspot", "data overload", "relication load" with consistency hashing we can use "Virtual Nodes" which are distributed across the ring. 
- Now ranges will have multiple vnodes spread acorss the ring.


### 2. Data Replication 






## Reference
[dynamo-cassandra](https://sujithjay.com/data-systems/dynamo-cassandra/)