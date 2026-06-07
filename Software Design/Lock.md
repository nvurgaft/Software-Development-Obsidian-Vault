A lock is a mechanism commonly used in concurrent programming to [[Common issues found in concurrent code|synchronize code access between multiple running threads]].

A lock locks a specific area of code and controls it's access, such area is called a critical section because concurrent access to this area from multiple different threads may produce subtle bugs and race conditions.


```java
public void routine() {

	// multiple threads can access this code and run it at the same time
	doSomething();
	
	// thread A takes a hold of this lock and accesses the try block
	// thread B is blocked.
	lock.lock();
	try {
		// only 1 thread at a time will invoke this call.
		doSomethingSynchronized();
		
	} catch (Exception e) {
		// handle exceptions
	} finally {
		// thread A releases the lock, and thread B can now take the lock
		// and access the try block.  
		lock.unlock();
	}

}
```

Using this try/catch/finally block pattern is highly recommended because locks must always be released for other threads to take control.
A resource controlled from un unreleased critical section may become inaccessible, which may lead to a starvation bug.


A popular lock implementation in Java the [ReentrantLock](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/locks/ReentrantLock.html) 