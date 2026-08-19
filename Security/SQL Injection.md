SQL injection is a code injection attack where an attacker inserts malicious SQL into an input field so the database runs unintended commands. It can let attackers steal sensitive data, modify or delete data, take administrative control, or make the database unavailable.

### Case Study

Lets say a client wants to run the following query

```sql
SELECT * 
FROM users 
WHERE name = userName
```

In our code we may write the following statement as so

```javascript
let statement = "SELECT * FROM users WHERE name = '" + userName + "'";
```

And expect the user to provide a valid value for the `userName`.

However a malicious user may try foul play and provide the `userName` with a value that breaks the query's intended behavior.

```sql
' OR '1'='1
```

The database will append this input to the query and will execute 

```sql
SELECT * 
FROM users 
WHERE name = '' OR 1=1
```

**Explanation**: no name in the table may be empty but `OR 1=1` will always return true for each record. Which makes this query functionally identical to

```sql
SELECT *
FROM Users
```

This will return all user data, **this is a security breach !!**

### Solutions 

1. Do not allow users to enter raw values into queries. Either validate and sanitize the values beforehand or hard code values and queries in the backend.
2. Use parameterized statements such as [PreparedStatements](https://docs.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html) with value placeholders that help avoid having your query manipulated, and allow the framework to enter only valid typed values and no syntax.
3. Use a backend mechanisms to build your queries in a safe way, such as a tested Query Builder or an ORM.
4. Instead of running SQL queries from the backend, encapsulate query login inside stored procedures in the database and call these procedures from the backend.