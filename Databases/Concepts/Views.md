A View is a stored SQL `SELECT` query that acts as a virtual [[Table]], a View has a name and is queried just like a Table, but instead to defer to the View query.

Views are used as a store common, complex queries that can be queried from multiple places. It allows the user to create non-repeating logic, write less queries and add readability. 

### Simple Views

Simple view are views that reference only one table and can be called to have it's underlaying table modified.

In PG, simple views fulfill the following conditions:
- The view must have exactly one entry in its FROM list, which must be a table or another updatable view.
- The view definition must not contain WITH, DISTINCT, GROUP BY, HAVING, LIMIT, or OFFSET clauses at the top level.
- The view definition must not contain set operations (UNION, INTERSECT or EXCEPT) at the top level.
- All columns in the view's select list must be simple references to columns of the underlying relation. They cannot be expressions, literals or functions. System columns cannot be referenced, either.
- No column of the underlying relation can appear more than once in the view's select list.
- The view must not have the security_barrier property.

E.g.

```postgresql
UPDATE pending_customers_view
SET customer_state = 'DONE'
WHEN customer_state = 'PENDING'
```

### Updatable Views

Simple views are automatically updatable: the system will allow `INSERT`, `UPDATE`, `DELETE`, and `MERGE` statements to be used on the view in the same way as on a regular table. A view is automatically updatable if it satisfies all of the following conditions:

- The view must have exactly one entry in its `FROM` list, which must be a table or another updatable view.
- The view definition must not contain `WITH`, `DISTINCT`, `GROUP BY`, `HAVING`, `LIMIT`, or `OFFSET` clauses at the top level.
- The view definition must not contain set operations (`UNION`, `INTERSECT` or `EXCEPT`) at the top level.
- The view's select list must not contain any aggregates, window functions or set-returning functions.

Updatable Views can then be further modified using [[Triggers]].

Syntax:

```sql
CREATE VIEW view_name AS ...query...
```

```sql
CREATE OR REPLACE VIEW view_name AS query
```

Example: 

Create a View:
```sql
CREATE VIEW blocked_users AS
SELECT id, name, email, last_login
FROM users
WHERE blocked = true;
```

Then query from it:
```sql
SELECT * FROM blocked_users;
```