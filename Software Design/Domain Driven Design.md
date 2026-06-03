**Domain-Driven Design (DDD)** is a software design approach that focuses on modeling software around the business domain rather than technical concerns.

- Start by understanding the business problem and terminology.
- Developers and domain experts collaborate to create a shared language called a [[Ubiquitous Language]].
- The system is organized around **Domains** (business areas) and **Subdomains**.
- Each subdomain has a **Bounded Context**, where terms and rules have a specific meaning.
- Core business concepts are represented as:
    - **Entities**: Objects with identity (e.g., User, Order).
    - **Value Objects**: Immutable objects defined by their values (e.g., Address, Money).
    - **Aggregates**: Groups of related objects treated as a consistency boundary.
    - **Repositories**: Abstractions for loading and saving aggregates.
    - **Domain Services**: Business logic that doesn't naturally belong to an entity.
- Business rules live in the domain model, not in controllers or databases.
- DDD encourages separating business logic from infrastructure concerns.
- It is especially useful for large, complex business applications where domain complexity is the main challenge.