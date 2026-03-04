A service mesh is a dedicated infrastructure layer that manages service-to-service communication in a microservices architecture.

Instead of putting networking logic (retries, timeouts, TLS, monitoring, etc.) inside your application code, a service mesh moves it into the infrastructure layer.

#### It provides 

1. Secure communication (TLS)
2. Retry logic
3. Load balancing
4. Handle timeouts
5. Circuit breaking
6. Observability (metrics, logs, traces)

It helps your application services handle unreliable network.
It keeps your application code clean of this infrastructure logic, thus removing the need to duplicate this logic across your services.

#### Use cases

* Multi team, multi service environments needing secure, consistent communication.
* Applications with high compliance requirements (Zero Trust)
* Gradual deployment of new features with canary or A/B strategies
* Requirement for unified monitoring and logging across services.

#### When is it not needed 

* May be total overkill for small or simple architectures. The added complexity may not worth it.


The Service Mesh has 2 components, The **Data Plane** and the **Control Plane**.
### Data Plane

The data plane is composed of lightweight service proxies called _sidecars_ and deployed alongside the service instances. These proxies handle real time network communication between the different services and parts of your architecture.

The data plane provide service discovery, load balancing, TLS, health checks and traffic routing between the services.

### Control Plane

The control plane manages the configuration and behavior of the data.

It provides policy management, security configurations, certificate distribution and observability.

#### Overview

```
+---------------------+  +---------------------+  +---------------------+
|     Service A       |  |      Service B      |  |      Service B      |
|  -----------------  |  |  -----------------  |  |  -----------------  |
|  | Sidecar Proxy |<------>| Sidecar Proxy |<------>| Sidecar Proxy |  |
|  -----------------  |  |  -----------------  |  |  -----------------  |
+---------------------+  +---------------------+  +---------------------+
			|						|						|
			+-----------------------+-----------------------+
									|
						 +---------------------+
						 |  Control Plane      |
						 +---------------------+
```

The service mesh architecture is implemented by software products such as [Istio](https://en.wikipedia.org/w/index.php?title=Istio&action=edit&redlink=1 "Istio (page does not exist)"), [Cilium](https://en.wikipedia.org/wiki/Cilium_\(computing\) "Cilium (computing)"), [Linkerd](https://en.wikipedia.org/wiki/Linkerd "Linkerd"), [Consul](https://en.wikipedia.org/wiki/Consul_\(software\) "Consul (software)"), AWS App Mesh, [Kuma](https://en.wikipedia.org/wiki/Kong_Inc. "Kong Inc."), Traefik Mesh, and Greymatter.io. Many service meshes use the [Envoy](https://en.wikipedia.org/wiki/Envoy_\(software\) "Envoy (software)") proxy on the data plane.