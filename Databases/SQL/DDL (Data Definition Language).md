The set of queries that define and modify the structure of database objects. It allows you to define Table constraints and the [[Relationships]] between them. 

It affects Tables, Indices, Views, Schemas, Constraints, Sequences, etc..

Common commands are
* CREATE
* ALTER
* DROP
* TRUNCATE
* RENAME

Examples:

```sql
CREATE TABLE Users (
	id serial,
	name text,
	email text,
	PRIMARY KEY(id)
);

ALTER TABLE Users
ADD COLUMN created_by TIMESTAMP WITH TIME ZONE;

TRUNCATE TABLE Users;

DROP TABLE Users
```
