Use specialized data structures as a caching layer between you application logic and the persistence layer. Caching allows us to reduce database hits and get data faster using in memory or durable cache for the cost of complexity and the possibility of receiving stale cached values.
Cache mechanisms map keys to stored values for storage and retrieval. 

#### Workflow
1. Try to access a stored value for a specific key
2. Instead of reaching straight to the database, query the cache
3. If there's a cache hit, retrieve the value from the cache.
4. If there's a cache miss, ask the database for a value, return the value to the end user, take the value and cache it for future requests.

Caches are usually implemented using hash maps for $O(1)$ read and write complexity. Using other data structures to keep consistency and implement eviction policies.

**Pros**
* Reduce database hits, resulting in less throughput on the service.
* Faster retrieval of data, has your value stored in memory instead of reading stored data in disk.
* Allows up to specify capacity and eviction policies.

**Cons**
* Additional layer of complexity.
* Additional cost of memory usage.
* Additional cost of synchronizing duplicate data.
* Can we afford end users receiving stale data ?
* How do we invalidate the data ? We let the cache or the database decide ?

## Eviction Policies

In real life situations we cannot allow our cache to grow without limit, we want to specify eviction rules for old or unused key-value pairs, if some database values are more frequently accessed than others, we would like them cached and retained more then others.

#### LRU (Least Recently Used)
Define a cache size and when new key-value pairs are added, if the size limit is reached, the least recently used key-value will be evicted.
Implemented using a hash map for easy key value access, and maps the values to a bounded linked list in the back, when a new value is added to the head, the least recently used value is removed from the tail.
If a value is re-used, move it to the head.

#### LFU (Least Frequently Used)

Keeps track of how much a value is accessed, and when a new value is entered the least accessed value is removed.
Implementations use value counters to keep track of the frequency.  

#### FIFO (First In First Out)
Similar to the LRU only that we keep a bounded Queue instead of a List, accessed values are not moved to the head.   