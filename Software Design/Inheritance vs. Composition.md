Inheritance and composition are two ways to structure relationships between classes, but they model very different ideas.

**Inheritance (“is-a” relationship)**  
With inheritance, a class derives from another class and automatically gets its behavior and properties. For example, a `Dog` class inheriting from `Animal` means a dog is an animal. This promotes reuse, but it creates tight coupling, changes in the parent class can affect the subclasses. It can also lead to rigid hierarchies that are hard to evolve (the classic “fragile base class” problem).

```java
class Manager extends Employee { ... }
```

A manager **is a** type of an employee that works inside an organization

**Composition (“has-a” relationship)**  
Composition builds classes by combining smaller, independent components. For example, a `Car` has an `Engine`, but a Car is not is an Engine. Instead of inheriting behavior, you delegate it to contained objects. This leads to looser coupling, better flexibility, and easier testing, since components can be swapped or modified independently.

```java
class Manager extends Employee {
	
	private List<Employee> workers;
}
```

In the above example, the manager **has** employees working under him.

**Key differences in design:**

- Inheritance is static (decided at compile time); composition is more dynamic (you can change behavior by swapping components).
- Inheritance encourages reuse through hierarchy; composition encourages reuse through collaboration.
- Inheritance can become brittle in large systems; composition tends to scale better and supports modular design.

**Rule of thumb:**  
Prefer composition over inheritance unless there’s a clear, stable “is-a” relationship.