The N+1 Problem is a common performance problem encountered in systems using ORM's that run multiple queries instead of one efficient query.

The N+1 problem occurs when an application executes one query to fetch a list of entities and then executes an additional query for each entity to fetch related data, resulting in N+1 queries total.

Example:

```java

// the .findAll will execute a SELECT
List<User> users = usersRepository.findAll();
// iterate through the users
for (User user : users) {
	// and each .getPosts with also run a select using the user's id.
	user.getPosts().size()
}
```

On the database side, these queries will run one after the other

```sql
SELECT * FROM Users;
SELECT * FROM Posts WHERE userId = 1;
SELECT * FROM Posts WHERE userId = 2;
SELECT * FROM Posts WHERE userId = 3;
...
SELECT * FROM Posts WHERE userId = N;
```

This is **REALLY BAD** because 

 1. This loads the database with many `SELECT` operations and hits performance in both database and the server side.
 2. It takes a longer time to finish than just one correct query.
 3. It doesn't scale well if N is millions of records.

### How to solve this ?

Use Joins

```postgresql
select u.*, p.*
from Users as u join Posts as p on u.id = p.userId
while u.id = 1 or u.id = 2 or ..... or u.id = N
```

JPA and Hibernate ORM have a built in feature to handle N+1 called `JOIN FETCH`

```java
@Query("SELECT u FROM User u JOIN FETCH u.posts")  
List<User> findAllWithPosts();
```

Also in JPA and Hibernate you can set the fetch mode to EAGER to get the data beforehand, which will eliminate the need to run the N queries on the cost that the data will be fetched early, even if not needed.

```java
@OneToMany(fetch = FetchType.EAGER)
private List<Post> posts;
```

Other Solutions

1. Batching operations will reduce the total amount of queries.
2. Redesign your API and Client code to request the additional queries on demand (don't just show all user posts on the same page, give the user a link to a separate page with the his posts, the client will specifically request the server to get these Posts).