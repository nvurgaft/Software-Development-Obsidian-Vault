Databases are software that facilitate persistence of data on disk in such ways that allow for efficient and fast storage and retrieval of structured or unstructured data.

Databases are crucial for any software that need to maintain a layer of fast and efficient persistence, as other, more basic storage methods such as writing to cleartext files or shared memory may not meet performance requirements.

Databases typically work with multi-tenancy application and require to support isolation between transaction.

Databases also require the provisioning of user accounts and roles to limit access and actions by certain users and user groups.

In classic SQL, data is stored in tables, a table can have one or multiple columns of various data types, a record in table then can be mapped to an object instance in runtime. 

In production environments, databases can contains hundreds or even thousands of tables (with various other database objects) with some tables can contains millions of records. 

Databases usually implement specialized data structures called [[Index (RDBMS)|Indexes]] that facilitate faster data lookup and retrieval (in a similar way an OS will index some parts of it's filesystem to help users locate files and directories in less time and effort).
### SQL Databases

Some databases are created to store tabular data, such records are stored inside [[Table|tables]], a database may typically have multiple tables, such tables will often have data with some [[Relationships|Relationship]] to other data inside other tables. Such databases allow to query and merge related data before retrieval. Traditionally SQL databases also provide [[ACID]] compliance and [[Transaction]] support, making them ideal for specific fields such as Banking, E-Commerce, Inventory management and storage of monetary transactions. 

### NoSQL Databases

In some occasions, SQL databases do not neatly fit the storage and retrieval requirements of certain applications, in such cases more specialized database are implemented. Usually these databases do not provide tabular data storage and forgo [[ACID]] compliance, rigid [[Transaction|transactions]] and other traditional database features to provide more specialized features that lack or do not exist in SQL databases.
[[NoSQL (Not Only SQL)]] databases usually excel in analytics processing, handling and processing huge amounts of unstructured data, vector data and more.

