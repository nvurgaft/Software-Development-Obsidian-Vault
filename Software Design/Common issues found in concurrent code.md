Concurrent code fails in ways that are often subtle and hard to reproduce. The most common bugs tend to fall into a few patterns:

#### Race conditions 
Two or more threads access shared state without proper synchronization, and at least one modifies it. The outcome depends on timing, so you get inconsistent behavior. 

**Example**: 
Incrementing a counter without a lock or atomic operation.
2 threads read the same numeric value at the same time, increment the value and set it. What is happening is by the end of the 2 operations, the value has only increased by 1. 

#### Deadlocks  
[[Deadlocks]] occur when two threads each hold a [[Lock]] and wait for the other to release theirs. Neither can proceed, so the system freezes. This often happens when locks are acquired in different orders across the codebase.

#### Live locks  
Threads aren’t blocked, but they keep reacting to each other and retrying without making progress. CPU is active, but useful work never completes.

#### Starvation  
A thread never gets access to the resources it needs (CPU, locks, etc.) because others monopolize them. This can happen with unfair locking or thread scheduling.

#### Atomicity violations  
A sequence of operations that should be indivisible is interrupted. Even if individual operations are thread-safe, the _combination_ may not be. 

**Example**: 

check-then-act 
``` java 
if (!exists) { 
	create(); // after this operation exists will be set to true 
}
```

``` java
/**
2 threads will check whether x equals to 0, because x++ is not atomic, a non-zero chance exists that one thread will read x as 0 while the other thread will be busy incrementing the x value.
*/
if (x == 0) {
	x++;
}

// to correct this issue, use an atomic integer
AtomicInteger ax = new AtomicInteger(0);
// ....
// later
ax.compareAndSet(0, 1);
```

#### Visibility issues (memory consistency bugs)
One thread updates a variable, but another thread doesn’t see the change due to caching or compiler/CPU reordering. Without proper memory barriers (e.g., `volatile`, synchronized blocks), threads may read stale values.

#### Order violations  
Code assumes a certain execution order between threads, but the scheduler interleaves them differently. For example, using a variable before another thread has initialized it.

**Improper use of synchronization primitives**

- Forgetting to release locks (especially in exception paths)
- Double locking or unlocking
- Using the wrong primitive (e.g., mutex instead of read-write lock)

**Ensuring unlocking example**:

Using try/catch/finally is a good control flow mechanism to ensure lock release.

```java
lock.lock();
try {
	// do work !
} catch (Exception ex) {
	// do something with the exception
} finally {
	// always use the finally block to release the lock as it is ensured 
	// that it will always run even on exception or return.
	lock.unlock();
}
```


**Thread leaks / resource exhaustion**  
Creating threads without proper lifecycle management can exhaust system resources over time.

**False sharing**  
Threads modify different variables that happen to share the same CPU cache line, causing performance degradation due to cache invalidation (not a correctness bug, but a nasty performance issue).

---

**How to mitigate these issues**

- Prefer immutable data and stateless design where possible
- Use higher-level concurrency constructs (thread pools, concurrent collections)
- Keep critical sections small and consistent in lock ordering
- Use atomic classes and proper synchronization
- Add timeouts and monitoring to detect deadlocks or stalls
- Test with stress, fuzzing, and tools designed for concurrency bugs

In practice, the hardest part is that many of these bugs don’t show up in testing—they appear under real load or rare timing conditions, which is why disciplined design matters so much.