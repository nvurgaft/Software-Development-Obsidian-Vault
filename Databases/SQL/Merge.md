The `merge` query allows you to conditionally insert, update or delete records from one table onto another. `merge` consolidates these multiple operations into one single efficient command.

The `merge` query accepts 
1. Target Table - The table you need modify.
2. Source Table - The table containing the new or updated data.
3. Match Conditions - The rules that determines if records match between tables.

Query syntax
```postgresql
MERGE INTO target_table
USING source_table
ON match_condition
WHEN MATCHED AND condition THEN 
	UPDATE SET column1 = value1, column2 = value2
WHEN MATCHED AND NOT condition THEN 
	DELETE
WHEN NOT MATCHED THEN 
	INSERT (column1, column2) VALUES (value1, value2)
RETURNING merge_action(), target_table.*;
```

The `merge_action()` function tells you exactly what happened to each row

#### Example

```postgresql
MERGE INTO products p
USING product_updates u
ON p.name = u.name
WHEN MATCHED AND u.status = 'discontinued' THEN 
	DELETE
WHEN MATCHED AND u.status = 'active' THEN 
	UPDATE SET price = COALESCE(u.price, p.price), stock = u.stock, status = u.status, last_updated = CURRENT_TIMESTAMP
WHEN NOT MATCHED AND u.status = 'active' THEN 
	INSERT (name, price, stock, status) VALUES (u.name, u.price, u.stock, u.status)
RETURNING merge_action() as action, p.product_id, p.name, p.price, p.stock, p.status, p.last_updated;
```