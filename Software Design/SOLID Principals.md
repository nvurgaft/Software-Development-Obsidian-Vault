 SOLID is an acronym that represents five key design concepts in object-oriented programming that help making code more understandable, flexible, and maintainable. 
 They include:
 
 1. Single Responsibility Principle 
 2. Open-Closed Principle
 3. Liskov Substitution Principle
 4. Interface Segregation Principle 
 5. Dependency Inversion Principle.
 
## The Five SOLID Principles

**Single Responsibility Principle (SRP)** - A class should have only one reason to change, meaning it should only have one responsibility.

Example:

```java
/**
	This class only does one thing and can be used by outside objects
*/
class CoinFlipper {
	public Result flipCoin() {
		...
	}
}
```

**Open-Closed Principle (OCP)** - Software entities should be open for extension but closed for modification.

Example:

```java
final class LegacyClient {
	// an old, yet working code that shouldn't be modified
	// final is optional, but a final class can not be extended. 
}

class NewClient {
	private LegacyClient legacyClient;
	// this class acts as an adapter/wrapper to the old legacy client class
	// and provides additional modern features of it's own
}
```

**Liskov Substitution Principle (LSP)** - Objects of a superclass should be replaceable with objects of a subclass without affecting the program's correctness.

Example:

```java
AbstractClass aco = new ConcreteClassOne();
AbstractClass act = new ConcreteClassTwo();
```


**Interface Segregation Principle (ISP)** - Clients should not be forced to depend on interfaces they do not use.

Example:

```java
public interface HttpClient { ... }
public interface SftpClient { ... }

public class ElasticClient implements 
	HttpClient,
	SftpClient // <- remove this as Elastic is HTTP only
	{ 
	...
}
```

**Dependency Inversion Principle (DIP)** - High-level modules should not depend on low-level modules; both should depend on abstractions.
This is to reduce tight coupling between classes.

Instead of injecting a concrete implementation ...

```java
class ClassB { 
// fields, constructor and methods 
} 

class ClassA { 
	
	private ClassB objectB; 
	
	public ClassA(ClassB objectB) { 
		this.objectB = objectB; 
	} 
	// invoke objectB methods 
}
```

Inject the interface

```java
class ClassB { 
	// fields, constructor and methods 
} 

class InterfaceB { 
	// fields, constructor and methods 
} 

class ClassA { 
	
	private ClassB objectB; 
	
	public ClassA(InterfaceB objectB) { 
		this.objectB = objectB; 
	} 
	// invoke objectB methods 
}
```

Now you can provide any implementation of `InterfaceB` at runtime.