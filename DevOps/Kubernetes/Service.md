Expose an application running in your cluster behind a single outward-facing endpoint, even when the workload is split across multiple backends.

### Service Components

* Kubelet, ensures that [[Pod|Pods]] are running, including their containers.
* Kube Proxy. maintains network rules on nodes to implement [[Service|Services]].
* Container runtime, software responsible for running [[containers]].