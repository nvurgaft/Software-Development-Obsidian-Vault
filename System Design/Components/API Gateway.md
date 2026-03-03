An API Gateway is a server that sits between [[client|clients]] and your backend services and acts as a single entry point into your system.

Instead of clients talking directly to multiple microservices, they talk to the API Gateway — and the gateway routes the request to the correct service.

A different Gateway can be used for client type, a Gateway for a web client and a separate gateway from a mobile client.

### Trade offs

**Pros**
1. Centralized Security.
2. Better observability.
3. Centralized traffic control.
4. Allows response aggregation.

**Cons**
1. Performance bottleneck and a single point of failure (unless replicated).
2. Adds a network hop which adds to latency.
3. Adds complexity to the architecture, the gateway is another actor with critical application logic.

### Responsibilities

#### Routing

A client may send a request to the backend, the request is intercepted by the API Gateway and the request is being routed to the appropriate service. Many services may receive the request from the client and the matter is completely invisible to the end-user.

A call to `/api/users` may reach the users service (authentication and authorization), but a call to `/api/orders` will reach the orders service.

#### Authentication and Authorization

Instead of each service handling authentication, the Gateway centralizes it.

#### Caching

[[Caching]] can be used on the API Gateway is a centralized to reduce hops and ease service access.

#### Rate Limiting

Because all client requests go trough the Gateway, it perfect central point to rate limit requests to the system and block suspicious traffic. Give less rate limitation to premium users. 

#### Load Balancing

Load balance requests among services.

#### Transform requests and responses

Modify content types, convert data formats. 

#### Logging and Monitoring

The gateway is a central place useful to gather user metrics, tracing and to audit log.

### Response Aggregation

When the client sends a request to the gateway, the gateway can instead send multiple, parallel requests to multiple services, wait for their arrival, merge them and return the merged response to the client.
As for the client sees things he only send a single request and got a single response, he is completely unaware that multiple services have been queried at the same time. He is completely decoupled from what happens in the backend.

For example, a client can send a request to `/api/order_summary`, the request will reach the Gateway. Then the gateway will send requests, in parallel to 
1. `\api\orders` in orders service
2. `\api\users` in users service
3. `\api\products` in products service
4. `\api\payment` in payment service

Get all responses, aggregate them into a overall response

```json
{
	status: "success",
	message: "",
	errors: [],
	data: {
		order: {
			orderId: 1234567
			... etc
		},
		user: {
			userId: 2
			... etc
		},
		products: [{
			productId: 1000
			... etc
		},{
			productId: 1001
			... etc
		}],
		payment: {
			paymentId: 90
			... etc
		}
	}
}
```

**Pros**

1. Simplifies client code and requesting logic
2. Decoupling by the gateway, the gateway can change target services without affecting client code.
3. Decoupling, the client side doesn't know it speaks with a gateway instead of a service.

**Cons**

1. Complexity is only moved from the client to the gateway
2. Aggregation is added complexity, validation and error handling is required. 
