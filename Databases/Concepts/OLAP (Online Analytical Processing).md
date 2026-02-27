Is a process or a technology that allows users to store big amounts of data from multiple data sources and quickly analyze and retrieve this data using [multi-dimensional analytical (MDA)](https://en.wikipedia.org/wiki/Multidimensional_analysis) queries.

You do not do OLAP in the services and applications facing the end-user as it will overkill the processing unit with heavy queries and big data.
Instead Use [[ETL (Extract, Transform, Load)]]/[[ELT (Extract, Load, Transform)]] from an [[OLTP (Online Transaction processing)]] service to transfer the data into an OLAP service.

#### Common uses for OLAP systems are:

* Internal systems and mechanism.
* Reports (sales, revenue, infrastructures, etc.. ).
* User behavior analysis.
* Fraud detection.
* Management dashboards.

#### Characteristics 

* Heavy queries of big data. 
* Large scans of data and aggregations.
* High latency (queries can read large datasets). 
* Denormalized data.
* Queries that can take from seconds to minutes to return processed data.
```sql
SELECT customer_id, count(*)
FROM purcheses
GROUP BY customer_id
HAVING total_price >= 100
```

#### OLAP emphasizes:

* Some correctness under concurrency.
* No need for strictness of database transactions.
* Some redundancy, data is denormalized.
* No strict constraint enforcement. Data may not even be tabular.

#### Databases:
 
* Elasticsearch
* Redshift
* Google Bigquery
