Commands used to controller transaction lifecycle.

It affects Transaction boundaries, consistency and recovery from errors. TCL works with [[DML (Data Manipulation Language)]] queries. 

Transaction are used to ensure [[ACID]] compliance.

Common commands are
* BEGIN / START TRANSACTION
* COMMIT
* ROLLBACK
* SAVEPOINT
* SET TRANSACTION

Examples:
```sql
BEGIN;

UPDATE Accounts SET balance = balance - 100 WHERE id = 10;
UPDATE Accounts SET balance = balance + 100 WHERE id = 20;

COMMIT;
```