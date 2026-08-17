Indexes  (Indices or Indexes in plural) are data structures and database objects used to improve the performance of lookups on [[Table|Tables]] for specific or ranges of records.

Indices internally use various search algorithm, usually [B-Trees](https://en.wikipedia.org/wiki/B-tree) (A self balancing tree), [Hash-Tables](https://en.wikipedia.org/wiki/Hash_table) and more. specific vendors may include their own algorithm implementations and index types.

For instance, a table with millions of records may be unsorted and a lookup for a specific key or column value will have $O(n)$ time complexity to find.
Indexing a table with a B-Tree algorithm will reduce look up time to $O(logn)$.
Indexing with a Hash-Table will reduce lookup to $O(1)$.

Different algorithms are better for certain cases and data types than others. It's the developer's responsibility to pick and choose the right index.

Each relational database will have it's own set of index algorithm implementations.

### Indices

Create an index on the `id` column without specifying the index type 
```postgresql
CREATE INDEX hosts_id_index ON hosts (id);
```

Specifying the `HASH` type index
```postgresql
-- Hash index in Postgresql
CREATE INDEX customer_id_hash ON customers USING HASH (customer_id);
```

### Compound (multi-column) indices

An index can made using multiple columns, I such cases the combined column values must be unique.

Say we have a table

```sql
create or replace table versions (
	major int not null,
	minor int not null,
	name text,
	released date
);
```

We can deduce that a version is unique if the combined values of `major` and `minor` are unique and must not repeat.

So when querying like

```postgresql
select *
from versions
where major = 1 and minor = 0;
```

An Index creation query will look like so

```postgresql
CREATE INDEX combined_version_index on versions (major, minor);
```

When using a compound index, make sure you use an index type that supports it.