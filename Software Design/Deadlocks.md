A deadlock is a situation when 2 or more threads hold a lock and wait for each other to to finish a unit of work release theirs. Each thread is waiting for the other and this results in endless wait.


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