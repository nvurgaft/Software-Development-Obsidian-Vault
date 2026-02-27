An operation is idempotent if performing it multiple times has the same effect as performing it only once.

Meaning if a client performed an action multiple times or send a request multiple times, the system would behave as though the action or request happened once.

Idempotency is important when making sure an operation needs to run once and only once. For example poor network conditions may prompt a client to resend a request after a timeout was reached, even though the original request reached the server and changed it's state. 
If the operation is not idempotent the operation will run twice and change the server state twice.

Common cases are 

* Double charges
* Duplicate orders

In the HTTP specifications, the `PUT` verb describe an idempotent operation.

### How to implement Idempotency

For requests that add new database entries or resources attach a request key. In case of a `POST` command, no new entry will be added if the request key was already processed.

In databases use a merging operation (`MERGE`). Command such as `CREATE IF NOT EXIST ...` are idempotent.