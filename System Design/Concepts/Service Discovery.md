In a microservices environment, services need to talk to one another, to be able to do so, each service would need to know the remote address and working ports of any other service. 
Manually configuring remote service addresses and ports onto service configuration makes services that much more coupled together. Higher coupling will result in systems that are harder to maintain and scale.

Dynamically determining the different addresses of all services that need to talk to one another is not trivial task, especially when different containers/instances of services a constantly being created and destroyed.

### Service Registry

A service discovery pattern enables locating microservices within the network. It uses a service registry (a centralized server) to keep a global record of all microservices’ network locations.

All microservices must register and disclose their locations to the central service registry at set intervals. Clients (service consumers) can retrieve the locations of each microservice by connecting to the service registry, after which they can directly call the various services to complete a task.

There are two main implementations of service discovery: client-side discovery and server-side discovery.
### Client-side Discovery

1. A client-side service consumer tries to locate a specific service provider by searching the service registry.
2. The service consumer selects a suitable, available service instance with the help of a load balancer.
3. The service consumer makes a request.

Once a service instance initiates, it needs to register at the service registry, and unregister itself when destroyed.

Since the consumer of a given service is aware of all service instances available, the pattern can make intelligent decisions to implement load balancing.

### Server-side Discovery

1. The client-side service consumer does not know about the service registry. Instead, it makes requests through a router.
2. The router looks for an available, suitable service instance in the service registry and reroutes the request.

In this pattern, clients do not do service discovery or load balancing. Instead, the [[API Gateway]] works to select a suitable endpoint for a given client-side request.

## Implementing Service Discovery

There are several different ways to implement service discovery

#### DNS Based Discovery


#### Sidecar w/ key-value store


#### Library based service discovery




Source: https://www.solo.io/topics/microservices/microservices-service-discovery