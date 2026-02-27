Relationships are a way of describing how two [[Table|Tables]] are related or joined to each other.
Tables don't need to be related to each other.

There are 4 main types of relationships

## One to Many

One X has many Y's

Very common

Example: A teacher has many subjects, a system user can have many roles for that system.

## One to One

One X has one Y

Not very common

Example: A person has 1 spouse

## Many to Many

Many X's has many Y's

Not ideal but common

Example: A students can have many subjects, a subject can have many students, an employee can be assigned to many departments, a single department can have many employees.

We can store this type of relational data effectively using a joining table

Student <--- Student Subject ---> Subject

## Self relationship

A table that joins to itself

Example: An employee in an employee table can be a manager and manager another employee