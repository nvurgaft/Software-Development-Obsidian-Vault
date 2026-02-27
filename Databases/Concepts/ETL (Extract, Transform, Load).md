ETL is a process of Extracting data from a data source such as a Database, file (XML, JSON, CSV, etc..), Transforming that data into a different format, which can alter be easily queried and worked on, and then load the data to other persistence system such as another Database or a Data lake/warehouse.

## Extract

The step of extracting data from the data source.
An important part of this process is data validation and correctness, data must be validated to be eligible for further process and loading. 
Invalid data must be filtered out and reported.
The data must also be be in the correct form for future processing. 

Examples given:

```sql
select * from stock_transactions_2022;
```

```Java
Path path = Paths.get("src/to/file.csv");
List<String> read = Files.readAllLines(path);
```
## Transform

This step transforms the data into a format that can be loaded into the target data system.

Data cleansing ensures that only the required data is passed. Textual data with a specific encoding will have to change into another encoding.

Other examples of transforming may be:

* Type changing, `1` or `0` may be mapped into `true` or `false`.
* Data may be joined and grouped for easy future querying.
* Adding aggregations.
* Pivoting table data. Either changing or adding new pivoted tables.
* Splitting a column into multiple columns.
* Adding columns with data calculated from other columns.
* Preparing data for future [[Auditing]].
* Preparing data for future analytics.
* Adding surrogate keys.
* Sorting the data.
* Deduplication.
* Adding any additional required metadata.

## Load

Load an persist the data inside the target system.

How to load all this data ? Bulk loading or single row by row queries ? Multiple fast and efficient Transactions or 1 big Query !?

What loading strategies and API's the target system provides us ?

Examples:

```sql
insert into Stock_Transactions_Aggregate(transaction_id, customer_id, date, balance)
values (1, 1, '2022-1-1', 100), (2, 1, '2022-1-2', 120), ...
```

```java
byte[] content = "A long string or buffered data".getBytes(); 
Files.write(Paths.get("/src/to/file"), strToBytes);
```