NoSQL databases are a set of databases that do not fall to the traditional category of relational databases that allow for joins, implement [[ACID]] and allow [[Transaction|Transactions]].

NoSQL also usually forgo the traditional SQL language for a specifically tailored query languages. 

Types of NoSQL databases are

### MongoDB

Mongo has some ACID compliance and allows for transactions (since version 4).
It is a document based database that forgoes tables for collections. A collection is a set of loosely structured documents
Because it has no concept of a table and so no columns, relations and constraints between collections of documents are not possible as in regular RDBMS SQL.
Because of that MongoDB doesn't do `JOIN`s, so data would have to be structured around this limitation (some [[Denormalization]] ?!).

### ElasticSearch

Elasticsearch is a distributed search and analytics engine designed to make searching and aggregating large amounts of data extremely fast.

Elastic is optimized for fast multi document search and indexing. 
Elastic can take multiple query terms from a client and return search results sorted by search scores, which makes it ideal for search engines.

It doesn't do ACID and joins !
It doesn't do transactions !

In Elastic the data is not relational, the schema is made up of indices that contain loosely structured documents.