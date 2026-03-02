A Kubernetes cluster consists of a control plane and one or more worker nodes.

### Control Plane Components

API Server, the core component server that exposes the Kubernetes HTTP API.

* [[etcd]], consistent and highly-available key value store for all API server data.
* Scheduler, looks for Pods not yet bound to a node, and assigns each Pod to a suitable node.
* Controller Manager, runs [controllers](https://kubernetes.io/docs/concepts/architecture/controller/) to implement Kubernetes API behavior.
* Cloud Controller Manager (optional), Integrates with underlying cloud provider(s).