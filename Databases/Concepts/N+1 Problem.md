The N+1 Problem is a common performance problem encountered in systems using ORM's that run multiple queries instead of one efficient query.

The N+1 problem occurs when an application executes one query to fetch a list of entities and then executes an additional query for each entity to fetch related data, resulting in N+1 queries total.

**Example:**

We have an application that has a news section that contains posts made by users.
Each user can post many posts, and each post has one author (user).

In a naïve approach, to get the authors and posts you will have to perform 1+N `SELECT` operations, which, for a huge corpus of posts would sum to many select queries (each one port a post made by an author) and the entire operation will be slow and taxing on the database.

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

While a clever developer can observe this phenomenon and avoid it, an ORM may run the 1 select for all the authors and then try to run the other N select for posts per each of the N authors.

We should strive to avoid this behavior  

 1. This loads the database with many `SELECT` operations and hits performance in both database and the server side. `N+1` means the ORM will make `N+1` round trips to the database.
 2. It takes a longer time to finish than just one correct query.
 3. It doesn't scale well if N is millions of records.

### How to avoid N+1

Use Joins to get all the data you need 

```postgresql
select u.id, p.*
from Users as u join Posts as p 
	on u.id = p.userI
```

If you know the id's in advance (lets say, you paginate or batch)

```postgresql
select u.id, p.*
from Users as u join Posts as p 
	on u.id = p.userId
where u.id = 1 or u.id = 2 or ..... or u.id = N
```

Or use the `IN` keyword

```postgresql
select *
from Posts
where id in (0, 1, 2, 17, 18, 42);
```

JPA and Hibernate ORM have a built in feature to handle N+1 called `JOIN FETCH`

```java
@Query("SELECT u FROM User u JOIN FETCH u.posts")  
List<User> findAllWithPosts();
```

Also in JPA and Hibernate you can set the fetch mode to `EAGER` to get the data beforehand, which will eliminate the need to run the N queries on the cost that the data will be fetched early, even if not needed.

```java
@OneToMany(fetch = FetchType.EAGER)
private List<Post> posts;
```

Other Solutions

1. Batching operations will reduce the total amount of queries.
2. Redesign your API and Client code to run the additional queries on demand (don't just show all user posts on the same page, give the user a link to a separate page with his posts, the client will specifically request the page from the server to get these Posts).