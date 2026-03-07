Kubernetes runs your workload by placing containers into Pods to run on Nodes. A node may be a virtual or physical machine, depending on the cluster. Each node is managed by the control plane and contains the services necessary to run [[Pod|Pods]].

Typically you have several nodes in a cluster; in a learning or resource-limited environment, you might have only one node.

Run on every node, maintaining running pods and providing the Kubernetes runtime environment:

[kubelet](https://kubernetes.io/docs/concepts/architecture/#kubelet)

Kubelet is the agent running on each node, it ensures that Pods and their containers are running properly and .

[kube-proxy](https://kubernetes.io/docs/concepts/architecture/#kube-proxy) (optional)

Managers discovery and network rules on nodes to implement [Services](https://kubernetes.io/docs/concepts/services-networking/service/).

[Container runtime](https://kubernetes.io/docs/concepts/architecture/#container-runtime)

Software responsible for running containers.

```
                    Control Plane
                 ┌─────────────────┐
                 │  API Server     │
                 │  Scheduler      │
                 │  Controllers    │
                 │  etcd           │
                 └────────┬────────┘
                          │
                          │
               ┌──────────┴──────────┐
               │                     │
           Worker Node           Worker Node
        ┌─────────────────┐   ┌─────────────────┐
        │ kubelet         │   │ kubelet         │
        │ kube-proxy      │   │ kube-proxy      │
        │ containerd      │   │ containerd      │
        │ Pods            │   │ Pods            │
        └─────────────────┘   └─────────────────┘
```