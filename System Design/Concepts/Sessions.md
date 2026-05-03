A session is a sequence of interactions between a client (like a web browser) and a server. It allows the server to remember information about the client across multiple requests and interactions.

Sessions are a mechanism for stateful interactions between a client and a server. It exists to supplement [[Stateless protocol|stateless protocols]].

#### How does it work

When a user logs in a system, the server creates a session object, the server generates a session ID which it then sends to the client (usually via a cookie or a token).
On every request the client sends the session ID and the server identifies the user and looks up the session data using this ID.

#### Storage

Accessing Session data is crucial for maintaining session and state. This data can be stored in various places

1. In memory - Doesn't scale well, when the server goes down the session data is deleted.
2. Database - The session data persists, it's slower but data is recoverable
3. Cache - Data can be durable, faster retrieval, even between multiple instances (better more microservices).

### Sticky Sessions

In scaled systems session data can live in one server but not in the other. 
A specific client's requests will always route to the same server instance
This creates coupling between a client and a server instance.
This happens if you [[Load Balancer|balance workload]] using IP Hash.
It very simple to implement and maintain but ..

1. Doesn't scale well (new server instance don't receive user workload).
2. Causes fault tolerance issues (what if that specific server instance fails ?)
3. Work balance doesn't scale well.

### Shared Storage

Store session data in a shared cache memory (such as Redis), the session data is accessible to all servers.
When a session dies, invalidate and remove the session data from the cache.

### Token

Another approach is tokens (JWT), store all session data in a token that is shared between the client and server.
Servers don't need to synchronize the session data between them because it is shared with the client and the client sends the token on every request.