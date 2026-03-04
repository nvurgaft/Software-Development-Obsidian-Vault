A reverse proxy is a server that sites in front of backend servers or services and forwards [[Client]] requests to them on behalf of the application.

> [!NOTE]
> The Reverse Proxy sits on the server's end.

Clients think they’re talking directly to your application, but they’re actually talking to the reverse proxy.

An [[API Gateway]] can be considered a superset of a reverse proxy, a gateway will also include advanced features such as orchestration/aggregation features, rate limiting, protocol translation and more.

### What reverse proxies do

1. **SSL Encryption** - The reverse proxy can offload the work of encrypting and decrypting data from the server.
2. **Security** - The reverse proxy hides the real IP addresses of the server/s rendering it invisible to DDoS attacks. Albeit, the proxy is the point that needs to be hardened.
3. **Caching** - [[Caching]] can be used on the API Gateway is a centralized to reduce hops and ease service access.
4. **Rate Limiting** - Because all client requests pass trough the Gateway, it perfect central point to rate limit requests to the system and block suspicious traffic. Give less rate limitation to premium users. 
5. **Load Balancing** - Load balances traffic and requests among services.
6. **Logging and Monitoring** - The gateway is a central place useful to gather user metrics, tracing and [[Auditing|auditing]].

Some popular Server software that can also act as reverse proxies are [nginx](https://nginx.org/en/) and the [Apache httpd server  ](https://httpd.apache.org/).
