The [[Pod]] is the smallest deployable unit in Kubernetes.

A pod is a higher abstraction unit than a Container, a Pod may manage multiple containers as a single unit.
When running multiple containers as they are, each container is it's own process, running separately as different hosts. Contained processes can communicate by exposing their working process ports.
When running multiple containers inside a pod, they share a single unique IP address, and containers running inside the Pod use localhost to connect to each other on different ports. 

Containers inside a Pod share

1. Network namespace - All containers inside a pod communicate over localhost.
2. Interprocess namespace - All containers share IPC namespace.
3. Hostname - All containers share the same hostname.

Pods can Be created, updated and deleted. 

A pod is a native Kubernetes Object, to create one, a requirement YAML must be defined.

### Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: web-server-pod
  labels:
    app: web-server
    environment: production
  annotations:
    description: This pod runs the web server
spec:
  containers:
  - name: web-server
    image: nginx:latest
    ports:
    - containerPort: 80
```

## Lifecycle

The Pod moves between 4 states

#### Pending

The pending states is the initial state, the Pod is in the pending state when a [[Pod]] / [[Deployment]] / [[Job|Jobs]] is applied 
```sh
kubectl apply -f pod.yaml
```
Kubernetes is setting up the Pod in this state, it
* pulls images
* sets up volumes and networking
* creates containers

#### Running

Once all containers have successfully created, and at least one container is running, other containers may be running, starting or restarting

The `running` state is no indication that the application itself is properly running and healthy, that's what the readiness and liveness probes are for.

#### Completion (Succeeded / Failed)

This state occurs when all container finish. 

If all containers exited with status `0` then the Completion succeeded.
This is a common state for Jobs, [[CronJob|CronJobs]] and batch workloads.

If at least 1 container exited with status `1` then the Completion failed.

#### Terminated (Deletion / scaling down)

This state is entered when a Pod is deleted or a deployment is scaled down.

```sh
kubectl delete pod my-pod
```


## Pod phase

A Pod's `status` field is a PodStatus object, which has a `phase` field.

| State       | Description                                                                                                                                                                                                                                                        |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Pending`   | The Pod has been accepted by the Kubernetes cluster, but one or more of the containers has not been set up and made ready to run. This includes time a Pod spends waiting to be scheduled as well as the time spent downloading container images over the network. |
| `Running`   | The Pod has been bound to a node, and all of the containers have been created. At least one container is still running, or is in the process of starting or restarting.                                                                                            |
| `Succeeded` | All containers in the Pod have terminated in success, and will not be restarted.                                                                                                                                                                                   |
| `Failed`    | All containers in the Pod have terminated, and at least one container has terminated in failure. That is, the container either exited with non-zero status or was terminated by the system, and is not set for automatic restarting.                               |
| `Unknown`   | For some reason the state of the Pod could not be obtained. This phase typically occurs due to an error in communicating with the node where the Pod should be running.                                                                                            |
