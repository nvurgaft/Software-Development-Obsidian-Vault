A load balancer is a component that sits in front of another network component or service and distributes load across the multiple instances so that no specific instance will get overwhelmed and fail.
It provides better performance, allows for better scaling of service instances, fault tolerance and higher availability.

### What does it do

1. Distributes traffic across multiple servers.
2. It detects unhealthy servers using health checks or other criteria.
3. It stops sending traffic to unhealthy or downed instances and rebalances the incoming traffic among the remaining servers.
4. It can also handle routing rules and enforce [[Rate Limiting]].

### Types of Load Balancers

#### Layer 4 (Transport Layer)

Works on the TCP/UDP level, reroutes traffic based on IP address and port.
It's very fast because the traffic contents are not opened or inspected, all the work remains on the transport layer.

#### Layer & (Application Layer)

Works on the HTTP/S level.
In this level you can inspect the request contents (URL paths, headers, cookies). 
You can perform URL based rerouting.
Slower than Layer 4 Load Balancers at the cost of more application related features.

Before
```
						 +---------------------+
						 |       Service       |
						 +---------------------+
									|
						 +---------------------+
						 |       Client        |
						 +---------------------+
```

After
```
+---------------------+  +---------------------+  +---------------------+
|     Service         |  |      Service A      |  |      Service A      |
|     Instance 1      |  |      Instance 2     |  |      Instance 3     |
+---------------------+  +---------------------+  +---------------------+
			|						|						|
			+-----------------------+-----------------------+
									|
						 +---------------------+
						 |    Load Balancer    |
						 +---------------------+
									|
						 +---------------------+
						 |       Client        |
						 +---------------------+
```

### Common load balancing algorithms

#### Round Robin

Requests are distributed evenly, but resulting workload can be uneven between different requests and some instances may overload.
#### Least Connections

Sends traffic to the server with the fewest active connections, better for uneven workloads but not optimal.
#### IP Hash

Same client IP redirects to the same server. Useful for session consistency. Workload may be uneven.

#### Weighted balancing

Some servers get more traffic (based on capacity)

### Common Issues

#### Session Persistence

Sometimes a server will hold session data for a specific user. In that case we need to redirect all user requests to that specific server. This hampers load balancing by coupling the user with a specific instance. 
**Solution**: Sticky Sessions or external session storage (such as Redis)

### Common implementations

Hosted
1. [nginx](https://nginx.org/en/)
2. [HAProxy](https://www.haproxy.org/)

Cloud-managed
1. AWS Elastic Load Balancer
2. Google Cloud Load Balancing