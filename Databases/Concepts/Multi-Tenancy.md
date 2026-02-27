Multi-tenancy in web services is about designing one system that securely serves many customers (tenants) while keeping their data isolated, performance fair, and operations manageable.

A tenant can be an end user, organization, a company or any entity that needs to use the system in separation from other entities.

There are 3 multi-tenancy models in databases

### 1. Shared database, shared schema

All tenants' data is stored in the same table under the same schema and database, tenants are distinguished by their `id`

```postgresql
SELECT * FROM users WHERE user_id = 42;
```

**Pros**:
* Simplest to design and maintain.
* Easy to onboard new tenants.
* Simple queries.

**Cons**:
* Bugs run the risk of data leaks if you miss a tenant id.
* Noisy neighbors.
* Harder compliance and auditing.

### 2. Shared database, separate schema

All tenants share the same database but live in different schemas. Tenants are distinguished by schema prefix in queries. 

```postgresql
SELECT * FROM tenant_101.users;
SELECT * FROM tenant_102.users;
```

**Pros**:
* Better isolation, lower risk of data leaks through queries.
* Easier to backup and restore by tenant.
* Simple queries.

**Cons**:
* Migrations now at the schema levels. 
* Harder to shard data.
* Harder compliance and auditing.

### 3. Separate database

Each tenant has it's own database

```postgresql
SELECT * FROM tenant_db_101.tenant_schema.users;
```

**Pros**:
* Strongest isolation.
* Scaling is per tenant.
* Easy compliance
* Easy to import and export data per customer 

**Cons**:
* Complex to operate and high infrastructure cost
* Harder to analyze data between tenants.

## Cache Isolation

Cached data must also be separated by schema/database, when inserting/updating/deleting data make the right separation is selected.

```js
cacheKey = tenantId + ":user:" + userId
```

## Noisy neighbor problem

Some tenants may run massive workloads that can take away computing resources from other tenants and slow them down.

**Mitigations**

- Per-tenant rate limits
- Per-tenant DB connection pools
- Resource quotas (CPU, memory)
- Workload isolation (queues per tenant)
- Tiered plans (free vs enterprise)