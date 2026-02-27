In SQL a foreign key is a column or a group of columns that relates to a [[Primary key]] in another [[Table]], and uniquely identifies that row. 
Foreign keys are used to link (join) related dat from two, or more, tables.

Example:
```sql
CREATE TABLE customers (
	id INT PRIMARY KEY,
	name VARCAHR(255) NOT NULL,
	PRIMARY KEY(id)
);

CREATE TABLE contacts (
	id INT,
	customer_id INT,
	name VARCHAR(255) NOT NULL,
	phone VARCHAR(15),
	email VARCHAR(120),
	PRIMARY KEY(id),
	CONSTRAINT fk_customer
		FOREIGN KEY(customer_id)
			REFERENCES customers(id)
);
```

Because foreign keys reference primary key values in another table, it is not possible to to have foreign key values that don't exist in the referenced table. Therefor, to keep data integrity, when rows with primary key values are deletes, so must that operation cascade to the referencing table.

Cases for update or delete are also supported using the `ON DELETE` and `ON UPDATE` constraints.

```sql
  
CREATE TABLE contacts( 
	id INT, 
	customer_id INT, 
	contact_name VARCHAR(255) NOT NULL, 
	phone VARCHAR(15), 
	email VARCHAR(120), 
	PRIMARY KEY(id), 
	CONSTRAINT fk_customer 
		FOREIGN KEY(customer_id) 
			REFERENCES customers(customer_id) 
			ON DELETE CASCADE);
```

Usually primary and foreign keys are not updated, but records are commonly deleted.

Supported operations are: 
* `CASCADE` automatically deletes all the referencing table when the referenced rows in the other table are deleted.
* `SET NULL` sets the foreign key values to null
* `SET DEFAULT` sets the default key on the foreign key value.