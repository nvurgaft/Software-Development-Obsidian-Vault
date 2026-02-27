A ACID is an acronym of Atomicity, Consistency, Isolation and Durability, these are a set of properties that a database transaction has to guarantee against data errors, failures, logical and technical errors and other conditions that can corrupt a database or cause unwanted issues.

### Atomicity

Transactions usually consist of multiple queries that run sequentially, Atomicity guarantees that the entire Transaction runs as a single atomic unit of work. The transaction either succeeds and changes the state of a [[Table]] or a database or fail and rollback to it's initial state.

SQL commands such as `.commit` and `.rollback` help ensure Atomicity 
### Consistency

Consistency ensures that a transaction bring the database from one consistent state to another, preserving existing invariants. 
This means data cannot be saved in a way that break rules and constraints.
e.g. if a column cannot have a negative `int` value, saving a -1 value will fail the transaction.
This helps ensure the database doesn't enter a corrupted state.

### Isolation

[[Transaction|Transactions]] usually run concurrently, Isolation ensures that concurrent transactions run and affect the database as though they ran one after the other. 
They also cannot affect each other.
To do that, databases implement inner concurrency control (optimistic/pessimistic locks, record version control, etc...)

### Durability

Durability ensures that once a transaction committed a state change to the database, that state remains even on immediate power failure or a restart. This property is critical against irreversible database corruption.