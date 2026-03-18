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

Example:

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

Examples: 

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

### Common use cases for Views

#### API & Abstraction Layer

Views can act as simplified, stable interfaces for the application

```postgresql
create view active_users as
select *
from users
where status = 'ACTIVE';
```
#### Business Logic encapsulation

Views can be used to encapsulate business logic by embedding rules into them

```postgresql
create view high_value_orders as
select *
from orders
when total > 1000;
```
#### Aggregation and Reporting

Views can be used to define reporting queries

```postgresql
create view monthly_sales as
select 
	date_trunc('month', order_Date) as month,
	sum(amount) as total_sales
from orders
group by 1;
```
#### Multi-Tenant Filtering

Views can support and enforce [[Multi-Tenancy|tenant isolation]].

```postgresql
create view tenant_orders as
select *
from orders
where tenant_id = current_setting('app.tenant_id);
```
#### Simplifying complex joins from multiple tables

Instead of joining results of complex `select`s, hide the result behind a `view` and join them. This approach also allows to simplify data retrieval from multiple tables.

```postgresql
create view customer_profile as  
select  
	c.id,  
	c.name,  
	o.last_order,  
	p.plan_name  
from customers c  
join orders o on c.id = o.customer_id  
join plans p on p.id = c.plan_id;
```
#### Security and data access control 

Use views to restrict tables or columns you do not with other users to access, restrict access to a specific table, but do allow users to access a view that provides a safer interface.

```postgresql
-- view only reveals the 'id' and 'username' columns
CREATE VIEW public_users AS
SELECT id, username
FROM users;
```

#### Backwards compatibility

A view can mimic the behavior of an old table structure while not limiting any future refactoring of existing tables.

```postgresql
create view old_users as
select
  split_part(full_name,' ',1) as first_name,
  split_part(full_name,' ',2) as last_name
from users;
```