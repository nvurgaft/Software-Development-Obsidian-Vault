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

### Insert or Update (Upsert)

The `MERGE` operation allows for [[Idempotancy|idempotent]] operation on your tables, by making an update on a match and an insert on no match found.

```postgresql
MERGE INTO Student AS s
USING (VALUES
    (1717, 'Param Mohan', 1023456545, CAST('2002-05-15' AS DATE), CAST('2021-01-15' AS DATE), CAST('2025-06-15' AS DATE), 3.50),
    (1722, 'Alice Parker', 1098765432, CAST('2003-02-20' AS DATE), CAST('2022-01-15' AS DATE), NULL, NULL)
) AS v(id, name, national_id, birth_date, enrollment_date, graduation_date, gpa)
ON s.id = v.id
WHEN MATCHED THEN 
    UPDATE SET 
        name = v.name,
        national_id = v.national_id,
        birth_date = v.birth_date,
        enrollment_date = v.enrollment_date,
        graduation_date = v.graduation_date,
        gpa = v.gpa
WHEN NOT MATCHED THEN 
    INSERT (id, name, national_id, birth_date, enrollment_date, graduation_date, gpa)
    VALUES (v.id, v.name, v.national_id, v.birth_date, v.enrollment_date, v.graduation_date, v.gpa);
```

Query taken from https://www.baeldung.com/sql/postgresql-upsert-merge-insert
