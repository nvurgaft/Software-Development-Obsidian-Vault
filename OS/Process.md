A process is an instance of a program that is executing and using system resources allocated by the Operating system.
Each process is executed in a separate address space and one process cannot directly access the variables that belong to another process.
If a process wants to "talk" to a different process and access it's resources it has to use some mechanism of inter process communication (IPC).
These include pipes, files, sockets (UDP), shared memory etc.. 