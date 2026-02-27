In SQL a table is a database object that holds collection of records used to store and persist data.
The data is split between columns, each column has a type and constraints associated with it.

Tables are created using the `CREATE TABLE` command.

Example:
```sql
CREATE TABLE colors (
	id SERIAL PRIMARY KEY,
	name VARCHAR(20)
);
```

The example above create a simple table with 2 columns, the `id` column is used to identify the record and the `name` column is used to store the color name.

After inserting some data the table may look something like this:

| id (PK) | name  |
| ------- | ----- |
| 1       | red   |
| 2       | green |
| 3       | blue  |
The `SERIAL` type tell the database to always insert incrementing integer values (type `INT`) as ID's so we don't have to.
The `PRIMARY KEY` is a constraint that ensures not `NULL` data will be inserted and that the data is `UNIQUE`.
`VARCHAR(20)` is a string/text type that accepts a string of letter up to 20 characters in length.