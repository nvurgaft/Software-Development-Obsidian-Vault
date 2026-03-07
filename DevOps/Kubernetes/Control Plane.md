A Kubernetes cluster consists of a control plane and one or more worker nodes.
### Control Plane Components

1. **API Server** - The core component server that exposes the Kubernetes HTTP API to external clients such as `kubectl`, CI/CD tools and other applications. It is a central place that is  responsible for authentication, request validation and admission controllers. It is the only component that talks with [[etcd]].

2. **etcd** - The etcd database, consistent and highly-available key value store for all API server data. This is where the state of the cluster is stored, Kubernetes is practically blind if etcd goes down.

3. Scheduler - looks for Pods not yet bound to a node, and assigns each Pod to a suitable node.

4. Controller Manager -It  runs [controllers](https://kubernetes.io/docs/concepts/architecture/controller/) to implement Kubernetes API behavior. It runs [[Deployment]], [[Node]], [[ReplicaSet]], [[Jobs|Job]], [[Service]], Endpoint, ServiceAccount controllers.

5. Cloud Controller Manager (optional), Integrates with underlying cloud provider(s). It creates load balancers, manages cloud routes, handles node lifecycles and integrates volumes.

```
                Kubernetes Cluster
                       │
        ┌──────────────┴──────────────┐
        │                             │
   Control Plane                  Worker Nodes
 (cluster management)         (application workloads)
```
