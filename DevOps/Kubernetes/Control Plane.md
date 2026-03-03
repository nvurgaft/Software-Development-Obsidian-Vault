A Kubernetes cluster consists of a control plane and one or more worker nodes.

### Control Plane Components

API Server, the core component server that exposes the Kubernetes HTTP API. `kubectl`, CI/CD tools and UI's talk with this API.
It is responsibly for authentication, request validation and admission controllers.
It is the only component that talks with etcd.

[[etcd]] database, consistent and highly-available key value store for all API server data.

Scheduler, looks for Pods not yet bound to a node, and assigns each Pod to a suitable node.

Controller Manager, runs [controllers](https://kubernetes.io/docs/concepts/architecture/controller/) to implement Kubernetes API behavior. 
It runs deployment, Node, ReplicaSet, Job, Service, Endpoint, ServiceAccount controllers.

Cloud Controller Manager (optional), Integrates with underlying cloud provider(s).
It creates load balancers, manages cloud routes, handles node lifecycles and integrates volumes.
