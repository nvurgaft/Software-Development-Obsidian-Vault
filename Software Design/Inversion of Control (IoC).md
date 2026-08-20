Inversion of Control (IoC) is a software design principle that shifts the control of program execution from the code written by the developer to an external framework. 
This approach contrasts with traditional programming, where the developer's code directly calls libraries to perform tasks.

**Example:**

A developer may start writing a program from the `main` entry point and write up any required logic from there on

```java
class Main {
	public static void main(String[] args) {
		try {
			Calculator calc = new Calculator();
			calc.init();
			calc.start();
		} catch (Throwable t) {
			// handle and log something
		} finally {
			calc.stop();
		}
	}
}
```

Finding his program very much complex and high maintenance, the developer may unload his code into a framework.

```java
class Main {
	public static void main(String[] args) {
		Framework fw = new Framework().start(new Calculator());
	}
}
```

The framework may already implement error handling and a lifecycle loop so the developer wouldn't have to. 
But now the `main` method doesn't directly execute the developer's program, rather it initiates the framework that it itself run the program.

## Benefits

The benefits of IoC is inherent in what the framework adds to the development effort, frameworks add additional features that also improve developer experience.

1. [[Dependency Injection]] support.
2. Security features.
3. Dependency management. 
4. Opinionated (or not) architecture support.
5. Domain specific design patterns implementations (less boilerplate code).
6. Support for existing CI/CD tools.

And more..