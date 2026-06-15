**Domain-Driven Design (DDD)** is a software design approach that focuses on modeling software around the business domain rather than technical concerns.

- Start by understanding the business problem and domains
- Developers and domain experts (developers, stakeholder, project managers, etc..) collaborate to create a shared language called a [[Ubiquitous Language]].
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

Domains are separated into microservices, each service controls it's own domain, with his it's own database that contains the relevant data.

Common domain separation are 

- User Management
- Event Management
- Payments
- User notifications
- Reporting
- Observability

Every service should:

- Have a single business responsibility
- Own its data
- Be deployable independently
- Minimize dependencies on other services

Ways of minimizing dependency between services can be varied

1. Have a clear separation of concerns between services, do not allow duplication of data of logic between services
2. Ubiquitous API, instead of having services know about other services and how to communicate with them, have them all talk to a central message broker.
3. Separate CI/CD deployment procedure for each service.

When separating domains avoid splitting

- By CRUD entities only
- By database tables
- By technical layers (UI, DAO, Service)
- Too early before understanding the business