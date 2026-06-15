SSL termination means that HTTPS encryption is decrypted at a specific component before the request reaches the application.

Instead of every service handling TLS/SSL certificates, a dedicated component (load balancer, reverse proxy, API gateway, ingress controller) handles the encryption.

### Common flows

#### Termination at entry

Instead of encrypting the communications between the client (browser) and the backend (a server instance or a service), a gateway, a reverse proxy or a load balancer is placed between the two and that component terminates the SSL, then the communication continues unencrypted to the backend and to any other components in the architecture.

Common reverse proxies or load balancers that provide SSL termination are 

1. [ngingx](https://nginx.org/en/)
2. [kong](https://developer.konghq.com/gateway/)
3. [Spring Cloud Gateway](https://spring.io/projects/spring-cloud-gateway)

#### Zero-Trust

Some systems require to be very secure and hardened in a way that plain termination at entry may not be enough, such [[Zero Trust|Zero Trust environments]] will most likely use [[mTLS]] to ensure encrypted communications between services.