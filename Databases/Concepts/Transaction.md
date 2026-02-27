An SQL transaction is a sequence of one or more [[DML (Data Manipulation Language)|SQL operations]] (such as `INSERT`, `UPDATE`, `DELETE`) executed as a single unit of work (Atomicity). 
Transactions ensure that either all operations succeed and the database is affected or no changed are applied, maintaining data integrity.
Transactions are a necessary requirement of [[ACID]] compliance.

Common uses for Transactions are

* Banking systems
* E-Commerce sites
* [[OLTP (Online Transaction processing)]] systems

In SQL systems, you start a transaction using `BEGIN TRASACTION` or `BEGIN`, do your work and then either `COMMIT` or `ROLLBACK` your work.

Savepoints allow to to take a snapshot of your work up to a certain point, and when a `ROLLBACK` occurs, your work will roll back to the last savepoint.
#### Examples

```postgresql
-- simple trasaction
BEGIN;
UPDATE accounts SET balance = balance - 100.00
    WHERE name = 'Alice';
-- etc etc
COMMIT;
```

```postgresql
-- complex trasaction with savepoints and rollabcks 
BEGIN;
UPDATE accounts SET balance = balance - 100.00
    WHERE name = 'Alice';
SAVEPOINT my_savepoint;
UPDATE accounts SET balance = balance + 100.00
    WHERE name = 'Bob';
-- oops ... forget that and use Wally's account
ROLLBACK TO my_savepoint;
UPDATE accounts SET balance = balance + 100.00
    WHERE name = 'Wally';
COMMIT;
```