Rate limiting is a technique to control and limit the amount of running operations or processing requests to a specific period of time. 
This technique is used to prevent abuse and to ensure fair use of resource and API's. Rate limiting is used to protect systems against denial-of-service attack by limiting excessive traffic.

### How Rate Limiting Works

Rate limiting typically involves tracking the number of requests from a specific IP address or user account over a defined period. If the limit is exceeded, the server may respond with an error code, such as `429: Too Many Requests`, or temporarily block further requests.

### Common Techniques

- **IP-Based Rate Limiting**: Limits requests based on the source IP address.
- **User-Based Rate Limiting**: Restricts requests based on user accounts, useful for preventing credential stuffing attacks.
- **Application-Based Rate Limiting**: Controls access based on the type of application making the request. 
- **Application Domain Rate Limiting**: Apply rate limiting based on specific rules inside your application. For example, provide higher request limit to a premium users and lower limit to a free user. 

### Common Algorithms

#### Fixed window

Track the number of requests all users make in a given time window, and don't let any user exceed this limit.
Use a key/value store implementation (e.g. HashMap, Redis) to count the amount (value) of requests coming from an IP (key), if the number reaches the configured limit, return an error message to the use.
At the end of the time window, empty the Map.

##### Pros

Easy to implement

##### Cons

Case 1: Easy to exploit, a burst of requests, higher than the limit, at the end of the window can occurs if the time window has ended and the key/value store has emptied.
Case 2: For very large windows, if the use made a lot of requests at the start of the window, he will  will have to wait a very long time to be able to make the N+1th request.
Case 

#### Sliding logs

Similar to Fixed Window, however the time window is saved per user/IP.

#### Sliding Window

Same as above, but make the time window expire after a set time has passed from an early request, updating the time window's start time.


### Implementation

Rate limiting can be implemented at various levels, including:

- **Network Level**: Controls overall traffic to a network resource.
- **Application Level**: Built into web servers or applications to manage user sessions and requests. Distributed components such as [[Reverse Proxy|Reverse Proxies]], [[API Gateway|API Gateways]] and [[Service Mesh|Service Meshes]] can provide rate limiting functionality out of the box.
- **Data Centers**: Used to allocate resources according to service agreements, ensuring fair usage among tenants.

By employing rate limiting, organizations can enhance security, maintain performance, and ensure that their services remain available to legitimate users.