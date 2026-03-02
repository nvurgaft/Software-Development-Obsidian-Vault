The pod is the smallest deployable unit in Kubernetes.

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

