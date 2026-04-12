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

### Savepoint

The `SAVEPOINT` command established a point in your transaction you can rollback into. The `SAVEPOINT` command is used in tandem with the `ROLLBACK` command, make sure to specify the savepoint name.

Savepoints can only be created and used inside transactions.

**Example**

```postgresql
BEGIN;
    INSERT INTO table1 VALUES (1);
    SAVEPOINT my_savepoint;
    INSERT INTO table1 VALUES (2);
    ROLLBACK TO SAVEPOINT my_savepoint;
    INSERT INTO table1 VALUES (3);
COMMIT;
```

You can destroy savepoints using the `RELEASE SAVEPOINT <name>` command.

```postgresql
BEGIN;
    INSERT INTO table1 VALUES (1);
    SAVEPOINT my_savepoint;
    INSERT INTO table1 VALUES (2);
    ROLLBACK TO SAVEPOINT my_savepoint;
    INSERT INTO table1 VALUES (3);
    RELEASE SAVEPOINT my_savepoint; -- < here it is
COMMIT;
```