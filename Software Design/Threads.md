Threads are the most basic unit of executing code in parallel with other code (concurrency). Threads also the developer to run multiple multiple code routines at the same time, instead of one after the other (sequential).
Because threads can access common objects and resources at the same time, [[Common issues found in concurrent code|a need arises to synchronize certain segments of code to avoid subtle bugs an issues that may disrupt the correct execution of code]].

In Java a Thread is a class that provides utilization of the underlying OS threads. 
Once a thread has started (using the `start()` method) and finished, it can not run again and must be discarded (garbage collected).

The Thread API expects a class object implementing the `runnable` interface to execute. Internally it will run the Runnable's `run()` method.  

### Starting a Thread 

As an inline `Runnable`

```java
Thread t = new Thread(new Runnable() {
	// ...
});
t.start();
```

As a separate class implementing the interface

```java 
class Task implements Runnable{ ...}

Thread t = new Thread(new Task);
t.start();
```

Or by extending the Thread class

```java 
class Task extends Thread { ...}

Task t = new Task();
t.start();
```


Stopping the Thread

To join the thread (wait until thread completes), use the `join` method. This will pause the thread executing `t`.

```java
t.join();
```


### States

A thread can be in only one of the following states.

- **New:** The thread is in a new state if you create an instance of the Thread class but before the invocation of the `start()` method.
- **Runnable:** The thread is ready to run, but it's not running.
- **Blocked:** The thread is waiting for a monitor lock.
- **Waiting:** The thread is waiting indefinitely for another thread to perform a particular action.
- **Timed Waiting:** The thread is waiting for another thread to perform a specific action for up to a specified waiting time.
- **Terminated:** A thread that has exited is in this state.