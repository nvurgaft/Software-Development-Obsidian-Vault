Data types are a way to limit the kind of data that can be stored in a table. For many applications, however, the constraint they provide is too coarse. For example, a column containing a product price should probably only accept positive values. But there is no standard data type that accepts only positive numbers. Another issue is that you might want to constrain column data with respect to other columns or rows. For example, in a table containing product information, there should be only one row for each product number.

To that end, SQL allows you to define constraints on columns and tables. Constraints give you as much control over the data in your tables as you wish. If a user attempts to store data in a column that would violate a constraint, an error is raised. This applies even if the value came from the default value definition.

From https://www.postgresql.org/docs/current/ddl-constraints.html

### Check

The `CHECK` constraint allows you to test the validity of a column value against a statement.

```postgresql
CREATE TABLE products (
    product_no integer,
    name text,
    price numeric CONSTRAINT positive_price CHECK (price > 0)
);
```

`positive_price` is the constraint name.

Because product prices can not be negative, this `CONSTRAINT .. CHECK` tests if the price is a positive numeric value

You can also define a `CHECK` outside the column.

```postgresql
CREATE TABLE products (
    product_no integer,
    name text,
    price numeric,
    CHECK (price > 0),
    discounted_price numeric,
    CHECK (discounted_price > 0),
    CHECK (price > discounted_price)
);
```

Can also be written more concisely as 

```postgresql
CREATE TABLE products (
    product_no integer,
    name text,
    price numeric,
    discounted_price numeric,
    CHECK (discounted_price > 0 AND price > discounted_price)
);
```

### Not Null

You can specify a column to never contain a null value. 
Primary and Foreign keys as `NOT NULL` by default

```postgresql
CREATE TABLE products (
    product_no integer NOT NULL,
    name text NOT NULL,
    price numeric
);
```

You can also name a not null constraint 

```postgresql
CREATE TABLE products (
    product_no integer NOT NULL,
    name text CONSTRAINT non_nullable_name NOT NULL,
    price numeric
);
```

### Unique

You can specify a column to only contain unique values.
Primary key columns are unique by default.

```postgresql
CREATE TABLE products (
    product_no integer UNIQUE,
    name text,
    price numeric
);
```

### Default

Default is a constraint used to insert a default value inside a column if no value was specified inside the `INSERT`.

```postgresql
CREATE TABLE Orders (  
    order_id integer PRIMARY KEY,  
    order_number int NOT NULL,  
    order_date date DEFAULT CURRENT_DATE()  
);
```

If now `order_date` is provided, the row will contain the current date returned from `CURRENT_DATE()`.
This is another way to constrain a non null column.
### Primary Key

The [[Primary key]] constraint defines a column or a group of columns to act as a unique identifier inside the table.

```postgresql
CREATE TABLE products (
    product_no integer PRIMARY KEY,
    name text,
    price numeric
);
```

Defining `product_no integer PRIMARY KEY` is equivalent to `product_no integer UNIQUE NOT NULL`.

You can define a group of columns to act as a primary key

```postgresql
CREATE TABLE host (
	ip ip_adder,
	port integer,
	service_name text
	PRIMARY KEY (ip, port, service_name)
)
```

### Foreign Key

The [[Foreign key]] constraint defined a column or a groups of columns that act as an identifiers for rows in another table.

```postgresql
CREATE TABLE products (
    product_no integer PRIMARY KEY,
    name text,
    price numeric
);

-- The product_no FK in orders refers to product_no in the products table
CREATE TABLE orders (
    order_id integer PRIMARY KEY,
    product_no integer **REFERENCES products (product_no)**,
    quantity integer
);
```

You can define a composite foreign key.

```postgresql
CREATE TABLE t1 (
  a integer PRIMARY KEY,
  b integer,
  c integer,
  FOREIGN KEY (b, c) REFERENCES other_table (c1, c2)
);
```