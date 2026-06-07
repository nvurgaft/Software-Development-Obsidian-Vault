Every Java process the JVM executes it allocated a space in memory for objects to live in. The running Java process runs and during runtime creates objects, these objects live on the Heap, when an objects is not longer needed by the process, it is marked for deletion (Sweep and Mark) and is removed by the JVM garbage collector.
This space can be later used to allocated other objects.

Allocating an object into the heap is as simple as 

```java
MyObject obj = new MyObject(); 
```

A space in the heap will be allocated for `obj`. 
When the reference is no longer used or accessible, it will be remove in the next garbage collection cycle

```java
private void doSomething() {
	MyObject obj = new MyObject(); 
	// obj is now used
	obj.runTask();
}

public static void main(String[] args) {
	
	doSomething();
	// by this point doSomething() as already finished and the object reference is not longer accessible, it will be garbage collected soon
}
```

### Structure

The JVM heap is divided into several main areas

* Eden Space
	Newly created objects arrive here, most objects die young and die in this area. GC cycles are very frequent here.
* s0 and s1 (Survivor space)
	Objects surviving enough gc cycles in Eden space reach S0 and S1.
* Tenured and Old generation space
	Objects surviving s0 and s1 reach tenured and old space. These objects are long lived and Garbage collection cycles are far less frequent here.
* PermGen
	PermGen (Permanent Generation) is a memory area in the Java Virtual Machine (JVM) that stores metadata about classes and methods. **It was removed in Java 8 and replaced by Metaspace, which allows for dynamic memory allocation.**
* Metaspace
	Metaspace replaces the older PermGen space starting from Java 8. It allocates memory from the native system memory and can grow dynamically as needed.