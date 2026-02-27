A database contains one or more named schemas, which in turn contain tables. Schemas also contain other kinds of named objects, including data types, functions, and operators. Within one schema, two objects of the same type cannot have the same name. Furthermore, tables, sequences, indexes, views, materialized views, and foreign tables share the same namespace, so that, for example, an index and a table must have different names if they are in the same schema. The same object name can be used in different schemas without conflict; for example, both `schema1` and `myschema` can contain tables named `mytable`. Unlike databases, schemas are not rigidly separated: a user can access objects in any of the schemas in the database they are connected to, if they have privileges to do so.

There are several reasons why one might want to use schemas:

- To allow many users to use one database without interfering with each other.
- To organize database objects into logical groups to make them more manageable.
- Third-party applications can be put into separate schemas so they do not collide with the names of other objects.

Schemas are analogous to directories at the operating system level, except that schemas cannot be nested.

Schemas are used to implement multi-tenancy at the schema level.
#### Examples

```postgresql
-- creates a schema
CREATE SCHEMA myschema;
```

```postgresql
-- creates a new table under the schema 
CREATE TABLE myschema.mytable (
 ...
);
```

```postgresql
-- drops a schema if it's empty
DROP SCHEMA myschema;
```

```postgresql
-- drops a schema with all the objects inside 
DROP SCHEMA myschema CASCADE;
```

Source: https://www.postgresql.org/docs/current/ddl-schemas.html