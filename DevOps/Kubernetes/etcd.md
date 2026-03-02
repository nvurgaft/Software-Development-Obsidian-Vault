etcd is a consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.

etcd stores states for running [[Pod|Pods]], Nodes, [[Deployment|Deployments]], Services, ConfigMaps, Secrets, Roles, Leases, Cluster configuration

When you run 

```sh
kubectl get pods
```

You are reading the pods records from etcd.