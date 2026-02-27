A way for a database cluster to replicate the data into segments that are stored in multiple instances. 

A shard will also have a backup.

Examples: 

A MongoDB cluster will have a Replica Set of multiple primary shards, with up to multiple secondary shards. In the case of a primary shard failure, secondary shards that will elect a new primary.

A Cassandra cluster will setup a Node cluster that anyone of these nodes can act as the primary node, to handle data replication, Cassandra undergoes "Eventual Consistency" which means new or updated data will propagate throughout the cluster and will reach consistency as fast as it is allowed. 

**Pros**: Helps prevent data loss when instances are down, just get a copy of the record from another instance in the cluster.

**Cons**: Complex joins, what if we need to join data from instance 1 on data from instance 2 ? We can mitigate this by utilizing smart database design, minimize join queries and use more queries that look up single value (key/value).

