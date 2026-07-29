BASE is a database model that is popular in [[NoSQL (Not Only SQL)|NoSQL]] database systems. It describes a database system that emphasizes availability at the cost of immediate consistency. In particular, these databases are:

- **Basically Available** – the database ensures that all data is available by ensuring that it’s stored across multiple nodes. This means that even if some nodes are unavailable, it’s much more likely that all of the data can still be accessed, but at the cost that it takes a non-zero amount of time for the data to spread across the nodes
- **Soft-state** – because the same data is stored across multiple nodes, and because this data may take time to get to every node, this means that the database can’t strongly enforce data integrity. Instead, it’s assumed that the client application will be doing this
- **Eventually consistent** – because the data is stored across multiple nodes, there is no guarantee that reading from one node will immediately reflect writes to another node. These reads will be consistent in time but not immediately

BASE systems are considered to be AP (Availability + Partition tolerance) on the [[CAP Theorem]] scale.

Examples of such systems include, but are not limited to [MongoDB](https://www.baeldung.com/java-mongodb), [Redis](https://www.baeldung.com/spring-data-redis-tutorial), and [Cassandra](https://www.baeldung.com/cassandra-with-java).