In database theory, the **CAP theorem**, also named **Brewer's theorem** after computer scientist Eric Brewer, states that any distributed data store can provide at most [two of the following three](https://en.wikipedia.org/wiki/Inconsistent_triad "Inconsistent triad") guarantees

**Consistency**

Every read receives the most recent write or an error. Consistency means that all clients see the same data at the same time, no matter which node they connect to. For this to happen, whenever data is written to one node, it must be instantly forwarded or [replicated](https://en.wikipedia.org/wiki/Replication_\(computing\)) to all the other nodes in the system before the write is deemed ‘successful’. Consistency as defined in the CAP theorem is quite different from the consistency guaranteed in [ACID](https://en.wikipedia.org/wiki/ACID "ACID") [database transactions](https://en.wikipedia.org/wiki/Database_transaction "Database transaction").

Weak consistency means that some data may be missing or not fresh.  However, eventually, the data will be consistent.

**Availability**

Every request received by a non-failing node in the system must result in a response, without the guarantee that it contains the most recent version of the data. This is the definition of availability in CAP theorem as defined by Gilbert and Lynch. Availability as defined in CAP theorem is different from [high availability](https://en.wikipedia.org/wiki/High_availability "High availability") in software architecture.

**Partition tolerance**

The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes.
Partitioning is a requirement for horizontal scaling.

When a network partition failure happens, it must be decided whether to do one of the following:

- cancel the operation and thus decrease the availability but ensure consistency
- proceed with the operation and thus provide availability but risk inconsistency. This does not necessarily mean that system is highly available to its users.

Thus, if there is a network partition, one has to choose between consistency or availability.

During times of normal operations, a data store covers all three.

Source: https://en.wikipedia.org/wiki/CAP_theorem