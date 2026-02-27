Triggers are database objects that are attached to tables and run functions when certain operations on those tables are made.

Triggers can run a function before (`BEFORE`) or after (`AFTER`) the database record is inserted, updated or deleted. Another options is `INSTEAD OF` to trigger actions on [[Views]].

The trigger can be configured to fire the trigger function either for each row modified (`FOR EACH ROW`) or for each statement (`FOR EACH STATEMENT` is the default in PG).

A `conditon` can also be applied to determine whether the trigger function should be applied.

Triggers are also commonly used for [[CDC (Change Data Capture)]] and [[Auditing]] operations.

#### Examples:

```postgresql
-- execute check_account_update() for each updated row in the accounts 
-- table
CREATE TRIGGER check_update
BEFORE UPDATE ON accounts
FOR EACH ROW
EXECUTE FUNCTION check_account_update();
```

```postgresql
-- execute check_account_update() when the balance column in updated in 
-- the accounts table
CREATE OR REPLACE TRIGGER check_update
BEFORE UPDATE OF balance ON accounts
FOR EACH ROW
EXECUTE FUNCTION check_account_update();
```

```postgresql
-- run the function view_insert_row() for each row
CREATE TRIGGER view_insert
INSTEAD OF INSERT ON my_view
FOR EACH ROW
EXECUTE FUNCTION view_insert_row();
```