Materialized views are [[Views]] whose data is stored physically on the disk.

The use of materialized views are performance specific, store results from heavy queries so as to not repeat them often. They're a tradeoff between run time and storage space.

Syntax

```postgresql 
CREATE MATERIALIZED VIEW view_name AS query
```

Example:

```postgresql
CREATE MATERIALIZED VIEW total_sales AS
SELECT account_id, SUM(total)
FROM Sales
GROUP BY account_id
HAVING SUM(total) > 1000000;
```

Refresh the data in the materialized view using the `REFRESH` command

```postgresql
REFRESH MATERIALIZED VIEW total_sales;
```

Or refresh concurrently (must have a unique index)

```postgresql
REFRESH MATERIALIZED VIEW CONCURRENTLY total_sales;
```