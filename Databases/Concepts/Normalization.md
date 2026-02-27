Normalization is the process of converting a database design into a standard format.
Conversion is done into a "normal form", a standard of designing a database.
The normalization process is applied to [[Table|Tables]] and their columns. 

Why normalize

1. Eliminate inconsistencies
2. Remove duplicate information
3. Improve performance
# Normal Forms

## 1st Normal Form

First stage of normalization process

> [!1NF]
> Each set of columns must uniquely identify a row

A combination of all columns must be unique, if more than one row have the same values then it's not unique.
Either add more column/s to uniquely identify the row or add a [[Primary key]]
### Examples

A Subject table with the following columns

1. Subject name
2. Category
3. Student name

**Is not 1NF**, because a student can take the same subject, under the same category multiple times.
Solution: Add a [[Primary key]]
A University [[Table]] with the following columns

1. Name
2. Address

**Is 1NF**, because although multiple universities can have the same name, they can not have the same address (cannot occupy the same place).
But what if the university name changes ? or moves to another location (improbable but possible), so a [[primary key]] is needed regardless 
### Conclusion

For each table determine of a combination or columns can be used to uniquely identify a record
**If so**, determine the columns that can be used as Primary key
**If not**, create a new column for the primary key.
## 2nd Normal Form

The second stage of the normalization process.

> [!2NF]
> It must fulfill all the requirements on the 1st Normal Form
> AND 
Each non-key attribute (column) must be functionally dependent on the primary key (attribute is determined by the primary key)

And the table uses [[Foreign key]]s, a field that related to the [[Primary key]] in another table.
### Examples

An employees table has the following columns

1. Id - PK (Primary key)
2. First name
3. Last name
4. Department Id - FK (Foreign key)
5. Phone

Another table is for departments

1. Id - PK
2. Name

This fulfills the 2NF requirements, Each employee also has a foreign key (his department Id) that relates to the primary key in the departments table, many employees can be assigned to one Department (One to Many relation). 
## 3rd Normal Form

The third stage of the normalization process.

> [!3NF]
> If must fulfill all the requirements of the 1st and 2nd Normal Forms
> AND
> Have no transitive functional dependencies.

Transitive Functional Dependency:
Every non-key attribute must be dependent on the primary key and the primary key only !!
If there are such dependencies, move them to a separate table.

### Example:

Column A determines column B
Column B determines column C
Therefor A > B > C
So if Column A determines Column C
This dependency should be removed.

If we have the following table

University table

1. Id - PK
2. Name
3. City
4. Street name
5. Street number

Student table

1. Id - PK
2. Name
3. City
4. Street name
5. Street number

It is apparent that some table dependencies are common to both tables and are a unique combination for every record. So we can create an addresses table

1. Id - PK
2. City
3. Street name
4. Street number

And have both table point to address Id as their foreign key.

University table

1. Id - PK
2. Name
3. Address Id - FK

Student table

1. Id - PK
2. Name
3. Address Id - FK

Because many students can have the same address the relation is [[Relationships|One to Many]], for universities it is [[Relationships|One to One]].