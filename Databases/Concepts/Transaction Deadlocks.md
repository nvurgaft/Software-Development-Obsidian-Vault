A deadlock happens when two or more [[Transaction|transactions]] are waiting for each other to release locks on resources, resulting in a circular dependency where none of the transactions can proceed.

> [!Luckily, Postgresql will log when it detects a deadlock]
> ERROR: deadlock detected

### Example

Lets say we have 2 transactions, each wants to update some values on the same table.

```plsql
-- Transaction A
begin;

update records
set data = data + 1
where id = 1
returning *;

update records
set data = data + 2
where id = 2
returning *;

commit;
```

And ...

```plsql
-- Transaction B
begin;

update records
set data = data + 2
where id = 2
returning *;

update records
set data = data + 1
where id = 1
returning *;

commit;
```

After transaction A finishes the first `update`, it needs to update the row with id = 2, but that row is locked by transaction B.
Vice-versa, transaction B will wait after it's first `update` for a lock release by transaction A.
After some wait, the transaction will timeout and postgresql will log something like

> ERROR: deadlock detected  
> DETAIL: Process 70725 waits for ShareLock on transaction 891717; blocked by process 70713.  
> Process 70713 waits for ShareLock on transaction 891718; blocked by process 70725.  
> HINT: See server log for query details.  
> CONTEXT: while updating tuple (0,1) in relation "records"

### Strategies

When a deadlock occurs, you can do one of two things

1. Wait indefinitely (not really acceptable !)
2. Abort one (or both) the transactions.

Deadlocks are solved at the code level, here are some approaches to consider when dealing with deadlocks.

1. Rewrite your transaction code to not access the same tables (this is a major re-design challenge)
2. Make sure only one transaction writes data while other transactions possibly running transaction only read data (similar to how a read-write lock works, also a major design challenge).
3. Rearrange code execution order, example give below

You can take transaction B from the example above and rearrange the `update`s order

```plsql
-- Transaction B
begin;

update records
set data = data + 1
where id = 1
returning *;

update records
set data = data + 2
where id = 2
returning *;

commit;
```

This will get rid of the deadlock, but for more complex code this approach will have to undergo extensive re-design and re-testing to keep the code correct.