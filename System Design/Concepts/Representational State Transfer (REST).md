Representational State Transfer (REST) is an architectural style for designing networked applications, primarily used for web services. It emphasizes [[Stateless protocol|stateless]] communication between clients and servers, where each request from a client contains all the information needed to process it, and resources are identified by unique URIs.

A REST API is an Application Programming Interface that adheres to the specifications and constraints of REST.

### Uniform interface

All API requests for the same resource should look the same, no matter where the request comes from. The REST API should ensure that the same piece of data, such as the name or email address of a user, belongs to only one uniform resource identifier (URI). Resources shouldn’t be too large but should contain every piece of information that the client might need.

### Client-server decoupling

In REST API design, client and server applications must be completely independent of each other. The only information that the client application should know is the URI of the requested resource; it can't interact with the server application in any other ways. Similarly, a server application shouldn't modify the client application other than passing it to the requested data via HTTP.

### Statelessness

REST APIs are stateless, meaning that each request needs to include all the information necessary for processing it. In other words, REST APIs do not require any server-side sessions. Server applications aren’t allowed to store any data related to a client request.

### Cacheability

When possible, resources should be [[Caching|cacheable]] on the client or server side. Server responses also need to contain information about whether caching is allowed for the delivered resource. The goal is to improve performance on the client side, while increasing scalability on the server side.

### Layered system architecture

In REST APIs, the calls and responses go through different layers. As a rule of thumb, don’t assume that the client, and server applications connect directly to each other. There may be a number of different intermediaries in the communication loop. REST APIs need to be designed so that neither the client nor the server can tell whether it communicates with the end application or an intermediary.

Source: https://www.ibm.com/think/topics/rest-apis