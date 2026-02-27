Sometimes data must be traced and audited. When data is created and changed we need to keep track on who created or modified specific tables or rows.

We add fields/columns to our [[Table]] that will help up audit it.

Fields such as 

* `created_at`
* `created_by`
* `updated_at`
* `updated_by`

We can also create tables that keep an audit log. For example if we have a Students table, we may also create a `Students_Audit` table.

In an audit table we will store copies of the modified data with information on who modified the data and when. A copy of the data before and after can also be saved. Note that this will take a lot of space and this process can be migrated to a different database using [[CDC (Change Data Capture)]].

A new Audit Id primary key will make sure each row is unique.