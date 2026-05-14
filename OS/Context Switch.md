A context switch is the process of changing the execution context for a working processor. If multiple long (enough) running processes contend to run on a single processor, the OS will not allow each of them to run from start to finish in one go, one after the other, instead it will break their execution into chunks and will run these execution chunks in an interleaved manner. Simulating processes running in parallel (albeit no, execution time save is gained unless these processes are offloaded into separate threads).

Instead or running A, B and C, in a serial manner
```
A A A B B B C C C
```

They will be executed as
```
A A B B A C C B C
```

or
```
A B B A A C C B
```

Switching contexts takes time and throughput, for the benefit responsiveness and fairness when scheduling execution of programs. 