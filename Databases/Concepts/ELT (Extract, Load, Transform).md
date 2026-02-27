ELT is an alternative approach to the [[ETL (Extract, Transform, Load)]] used with data lakes implementations. In contrast to ETL, ELT models extract the data from the data source and then load them as is into the target system.
Any needed transformation is made on demand when the specific data is queried. 

That means, that any data cleansing, validation, deduplication and other pipeline processes are done on request basis.

ELT provides a tradeoff compared to ETL. Loading is faster, but querying the data, especially when a transform is needed, requires more processing power.