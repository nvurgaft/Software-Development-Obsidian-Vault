The set of queries that read and write data (rows) into tables.

Common commands are
* SELECT
* INSERT
* UPDATE
* DELETE
* MERGE

These commands are the CRUD operations for your database.

Examples:

```sql
SELECT 1;

SELECT * FROM Users;

INSERT INTO Users(name, email) 
VALUES ('Nick', 'nick@user.domain');

DELETE FROM Users
WHERE name = 'Nick';

UPDATE Users
SET name = 'Jones'
WHERE id = 42;
```