OLTP refers to database systems designed to process and manage large number of short, atomic, concurrent transactions ([[ACID]]).
OLTP systems process real time transactional data that have to be correct, consistent, concurrent, durable and with as low latency as possible, while ensuring no errors, data corruption and data inconsistencies. 

#### Common uses for OLTP systems are:

* System with API's facing the end-user.
* Banking and payment processors.
* E-Commerce checkouts.
* Order management.
* Inventory tracking.

#### Characteristics 

* [[Transaction]] oriented. 
* [[ACID]] compliance.
* Low latency (queries can complete in milliseconds, tables are indexed). 
* Queries that run and fetch simple data fast
```sql
INSERT INTO transaction_log VALUES (?, ?, ?);

UPDATE trasaction_log SET status = 'DONE' WHERE status = 'PENDING' and user_id = ?;

SELECT * 
FROM trasaction_log 
WHERE customer_id = ?;
```

#### OLTP emphasizes:

* Correctness under concurrency.
* Transactional integrity 
* Minimal redundancy.
* Strict constraint enforcement.

#### Databases:

* Postgresql
* MySQL
* Oracle
