The **JIT (Just-In-Time) compiler** is a component of the **Java Virtual Machine (JVM)** that improves performance by converting Java bytecode into native machine code while the application is running.

The Java JIT compiler observes which parts of your program are used most often and dynamically compiles them from bytecode into highly optimized native machine code to improve runtime performance.
### Why does Java need a JIT compiler?

When you compile Java code:

```java
public int add(int a, int b) {
    return a + b;
}
```

the Java compiler (`javac`) produces **bytecode**, not machine code:

```text
add:
  iload_1
  iload_2
  iadd
  ireturn
```

The JVM can execute bytecode using an **interpreter**, but interpretation is slower because each instruction must be decoded every time it runs.

### How JIT works

1. The JVM starts by interpreting bytecode.
2. It monitors which methods are executed frequently ("hot" methods).
3. When a method becomes hot, the JIT compiler compiles it into native machine code.
4. Future calls execute the native code directly, avoiding interpretation.

```text
Java Source
      ↓
    javac
      ↓
   Bytecode
      ↓
 JVM Interpreter
      ↓
 Hot Method Detected
      ↓
 JIT Compilation
      ↓
 Native Machine Code
```

### Optimizations performed by the JIT

The JIT can perform optimizations such as:

- **Method inlining**

Instead of 
```java
result = calculator.add(a, b);
```

The JIT may replace the method call with the method's actual code.
```java
result = a + b;
```

This removed the need to create an unnecessary stack frame

- **Dead code elimination**  
    Removes code that can never runs or affects the result.
- **Loop optimization**  
    Improves performance of frequently executed loops.
- **Escape analysis**  
    Determines whether an object can remain on the heap or be garbage collected.
### Tiered Compilation

Modern JVMs use **tiered compilation**:

- **C1 Compiler (Client Compiler)**: compiles quickly with basic optimizations.
- **C2 Compiler (Server Compiler)**: compiles more slowly but applies aggressive optimizations.

A method may first be compiled by C1 and later recompiled by C2 if it remains heavily used.
### Example

```java
for (int i = 0; i < 1_000_000; i++) {
    sum += i;
}
```

Initially, the loop runs interpreted. After enough iterations, the JIT compiles the loop into optimized machine code, making subsequent executions much faster.

### Benefits

- Platform independence (bytecode runs anywhere a JVM exists).
- Performance close to native languages like C++ for many workloads.
- Runtime optimizations based on actual execution patterns.