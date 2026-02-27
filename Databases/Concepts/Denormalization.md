[[Normalization|Normalized data]] is stored using normal forms, they use less storage space, require more look up to fetch specific data, easy to update.
We write queries that join [[Table]] data because the data is separated.

Example:

| Reservation ID | Customer ID | Time |
| -------------- | ----------- | ---- |
| 1              | 123         | 6:30 |
| 2              | 451         | 7:00 |
| 3              | 123         | 8:00 |

| Customer ID | Name  | Phone    |
| ----------- | ----- | -------- |
| 123         | Frank | 555-1234 |
| 451         | John  | 555-5233 |
Denormalized data has everything in one table, as if tables were joined together. requires more storage space, easy single lookups, harder to update

Example:

| Reservation ID | Customer ID | Name  | Phone    |
| -------------- | ----------- | ----- | -------- |
| 1              | 123         | Frank | 555-1234 |
| 2              | 451         | John  | 555-5233 |
| 3              | 123         | Frank | 555-1234 |

The benefits to denormalized data is that look ups do not require complex joins. This approach is somewhat useful in distributed database cluster that can hold data in different shards and joining that data could be an expensive operation.