Change Data Capture is about identifying can capturing data changes made inside a database using operations such as `INSERT`, `UPDATE` or `DELETE` and delivering those changes downstream as events in real time, Usually to a message broker.

#### Use cases:

* Real time stream processing.
* Synchronizing data across multiple services.
* Data replication and backup.
* Auditing.
* Automating cache invalidation.
* An alternative to [[ELT (Extract, Load, Transform)]] that runs when data is changed.

### Trigger Based CDC

In [[Triggers]] based CDC, custom triggers attached to tables run specific logic when data is being inserted or updated.
#### Example

```postgresql
-- Create the trigger  
CREATE OR REPLACE FUNCTION customers_trigger_function()  
RETURNS TRIGGER AS $$  
BEGIN  
	INSERT INTO data_change_log (table_name, operation, timestamp, data)  
	VALUES ('customers', TG_OP, NOW(), NEW);  
  
	RETURN NEW;  
END;  
$$ LANGUAGE plpgsql;  
  
-- Attach the trigger function to the table  
CREATE TRIGGER customers_trigger  
AFTER INSERT OR UPDATE OR DELETE  
ON customers  
FOR EACH ROW  
EXECUTE FUNCTION customers_trigger_function();
```

This approach creates the overhead of a function being called the adds an `INSERT` operation after an `INSERT` or an `UPDATE` were made on the `customers` table.

This approach avoids polling.

### Timestamp Based CDC

Periodically query the database for modified records. Utilize data columns to figure out which rows were inserted or modified for the queried time window.

This approach forgoes the use of Triggers and instead need to call a function that gathers the required data for that specific time window.

This is a polling approach, the target tables may not even change during the time window. 

### Log Based CDC

Read data straight from the database transaction log, or the [Write-Ahead Log](https://www.postgresql.org/docs/current/wal.html).
This approach removes the need to call functions that run additional queries but adds the complexity of having to parse database logs.


