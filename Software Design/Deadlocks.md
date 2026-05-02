A deadlock is a situation when 2 or more threads hold a lock and wait for each other to to finish a unit of work so they could release their own lock. When each thread forever waits for the other to finish, this results in a deadlock.

Deadlocks also exists in database environments in the form of [[Transaction Deadlocks]].

```java
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class DeadlockExample {
    private final Lock lock1 = new ReentrantLock();
    private final Lock lock2 = new ReentrantLock();

    public void methodA() {
        lock1.lock();
        try {
            Thread.sleep(100); // Simulate some work
            lock2.lock();
            try {
                // Critical section
            } finally {
                lock2.unlock();
            }
        } catch (InterruptedException e) {
        } finally {
            lock1.unlock();
        }
    }

    public void methodB() {
        lock2.lock();
        try {
            Thread.sleep(100); // Simulate some work
            lock1.lock();
            try {
                // Critical section
            } finally {
                lock1.unlock();
            }
        } catch (InterruptedException e) {
        } finally {
            lock2.unlock();
        }
    }

    public static void main(String[] args) {
        DeadlockExample example = new DeadlockExample();
        Thread t1 = new Thread(example::methodA);
        Thread t2 = new Thread(example::methodB);
        t1.start();
        t2.start();
    }
}
```

You can avoid some Deadlocks by using conditional locking, usually when a lock is set, the lock will block a thread from executing until the other thread releases the lock.

Java provides us with the [Lock](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/locks/Lock.html) interface and implementations.
Using `tryLock` we can do something else instead of locking.
Using `tryLock(n, TimeUnit)` we can try to lock and

1. Either wait up to `n` time units for the lock and return true.
2. Timeout and return false.

```java
if (lock.tryLock(2, TimeUnit.SECONDS)) {  
	try {  
		// critical section  
	} finally {  
		lock.unlock();  
	}  
} else {  
	// handle potential deadlock  
}
```