Java garbage collection (GC) is an automatic memory management process in the Java platform, JavaScript engines and other runtimes, that frees up memory by removing objects that are no longer in use. It helps developers avoid manual memory handling (like in C/C++) and prevents issues such as memory leaks and dangling pointers.

Garbage collection is an essential part of the proper run of the process. Because the programmer doesn't get to have an interface with which he can deallocate object memory (`delete` in C++ or `free` in C) he is entirely committed to the proper run and execution of the GC.

No GC mean the heap will eventually explode and the process will crash.

Garbage collectors work using the Mark and Sweep (and Compact) method.
1. Traverse the [[Java Heap|heap]] and mark unreferenced/unused object references.
2. Sweep and remove the unused objects
3. Compact the remaining objects to allow the runtime more contiguous space to easily allocate more objects. 