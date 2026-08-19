A field or column in a [[Table]] that contains a unique value for that row and identifies it. These values are important [[Constraints]] used to define relationships between tables. Primary keys are used to identify rows of current table from other tables using [[Foreign key|foreign keys]]. 

Primary keys must be unique and not null, SQL databases enforce these constraints.

Customer numbers or student Id's are commonly used as primary keys because they are unique.

Examples:

```sql 
CREATE TABLE Accounts (
	id SERIAL PRIMARY KEY,
	name TEXT,
	created_at TIMESTAMP,
	...
);
```

Another option is to declare the PK using the [[Constraints|constraint syntax]]

```sql
CREATE TABLE Accounts (
	id SERIAL,
	name TEXT,
	created_at TIMESTAMP,
	...
	PRIMARY KEY(id)
);
```

Primary keys can also be compounded from multiple column

```sql
CREATE TABLE GlobalAccounts (
	id SERIAL,
	state_id INT,
	name TEXT,
	created_at TIMESTAMP,
	...
	PRIMARY KEY(id, state_id)
);
```