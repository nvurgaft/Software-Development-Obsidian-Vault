A field or column in a [[Table]] that contains a unique value for the row. These values are important constraints used to define relationships between tables. Primary keys are used to identify rows from other tables using [[Foreign key|foreign keys]]. Primary keys must be unique and not null.

Customer numbers or student Id's are common used as primary keys because they are unique.

Examples:

```sql 
CREATE TABLE Accounts (
	id SERIAL PRIMARY KEY,
	name TEXT,
	created_at TIMESTAMP,
	...
);
```

Another option is to declare the PK using the constraint syntax

```sql
CREATE TABLE Accounts (
	id SERIAL,
	name TEXT,
	created_at TIMESTAMP,
	...
	PRIMARY KEY(id)
);
```