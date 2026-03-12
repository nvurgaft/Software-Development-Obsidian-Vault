A system call is a way for a program to request a service from the operating system's kernel, such as safely accessing hardware, managing processes, or handling files.

In fact, every Linux command runs at least some system calls used to access some sort of system resource, such as network, filesystem, memory and CPU.

It is possible to see which system calls are made using the [[strace|strace]] command.

Some common system calls are `open()`, `write()` and `close()`.

The Linux system calls can be divided into five categories:

1. Process management system calls
2. File management system calls
3. Device management system calls
4. Network management system calls
5. System information system calls