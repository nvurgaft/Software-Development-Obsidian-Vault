Because running a single query over a database takes 1 round trip, in the case where we need to insert a great deal of data we can avoid making a lot of round trips to the database by utilizing batching.

Another issue that may arise is a need to update or delete a huge dataset (millions or billions or records), running a query on such a huge dataset may take an extremely long time and the session may timeout your query.
So breaking such a task into smaller sub-tasks will avoid timeouts and unnecessary rollbacks

### INSERT

We can use the `INSERT` command to insert multiple rows with one query using the `INSERT INTO ... VALUES ...` syntax

```postgresql
insert into cities(id, name) values
	(1, 'New York'),
	(2, 'Tokyo'),
	(3, 'Jerusalem'),
	(4, 'Rio de Jeneiro');
```

If we, for example, have millions or billions of entries to append to the table we may implement batching on the server side

```java
int step_size = 1_000;
List<Record> records = ... // this is a very long list

for (long i=0; i<1_000_000; i = i + step_size ) {

	List<Record> subset = dataset.subList(i, i + step_size);
	String query = new StringBuilder()
		.append("insert into cities(id, name) values ");
	
	for (Record record : subset) {
		// create a query object and append the records from the subset
		query.append("(")
			.append(record.getId())
			.append(", ")
			.append(record.getName())
			.append(")");
		// ...
	}
	// send the query to the database
}
```

This approach will greatly reduce the times needed to reach the database. 
### DELETE

The syntax for running `delete`s in multiple batches 

```sql
DECLARE @BatchSize INT = 1000
DECLARE @RowsAffected INT = 1

WHILE (@RowsAffected > 0)
BEGIN    
	DELETE TOP (@BatchSize) 
	FROM table_name    
	WHERE condition
    
    SET @RowsAffected = @@ROWCOUNTEND
END
```

Rerunning this query will delete another `@BatchSize` of records from the Table.