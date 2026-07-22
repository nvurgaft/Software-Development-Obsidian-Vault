Because running a single query over a database takes 1 round trip, in the case where we need to insert a great deal of data we can avoid making a lot of round trips to the database by utilizing batching.

Another issue that may arise is a need to update or delete a huge dataset (millions or billions or records), running a query on such a huge dataset may take an extremely long time and the session may timeout your query.
So breaking such a task into smaller sub-tasks will avoid timeouts and unnecessary rollbacks

### INSERT

We can use the `INSERT` command to insert multiple rows with one query using the `INSERT INTO ... VALUES ...` syntax

```postgresql
insert into cities(id, name) values
	(1, 'New York'),
	(2, 'Tokyo'),
	(3, 'Tashkent'),
	(4, 'Rio de Jeneiro');
```

If we, for example, have millions or billions of entries to append to the table we may implement batching on the server side

```java
int step_size = 1_000;

for (long i=0; i<1_000_000; i = i + step_size ) {

	
}
```
### DELETE

The pattern for running `delete`s in multiple batches 

```sql
DECLARE @BatchSize INT = 1000
DECLARE @RowsAffected INT = 1

WHILE (@RowsAffected > 0)
BEGIN    
	DELETE TOP (@BatchSize) 
	FROM YourTable    
	WHERE YourCondition
    
    SET @RowsAffected = @@ROWCOUNTEND
END
```