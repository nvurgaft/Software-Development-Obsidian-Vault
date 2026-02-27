Indexes  (Indices in plural) are data structures and database objects used to improve the performance of lookups on [[Table|Tables]] for specific or ranges of records.

Indices internally use various search algorithm, usually [B-Trees](https://en.wikipedia.org/wiki/B-tree) (A self balancing tree), [Hash-Tables](https://en.wikipedia.org/wiki/Hash_table) and more. specific vendors may include their own algorithm implementations and index types.

For instance, a table with millions of records may be unsorted and a lookup for a specific key or column value will have $O(n)$ time complexity to find.
Indexing a table with a B-Tree algorithm will reduce look up time to $O(logn)$.
Indexing with a Hash-Table will reduce lookup to $O(1)$.

Different algorithms are better for certain cases and data types than others.

Each relational database will have it's own set of index algorithm implementations.

#### Example:
```postgresql
-- Hash index in Postgresql
CREATE INDEX customer_id_hash ON customers USING HASH (customer_id);
```