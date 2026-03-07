In Kubernetes, containers expose their health status to the platform using probes. These probes allow Kubernetes to determine whether an application inside a container is running correctly, ready to serve traffic, or needs to be restarted.

Kubernetes defines three main probe types:

- **Liveness Probe**
- **Readiness Probe**
- **Startup Probe**

To add one or more probes, simply define it in the Pod YAML file

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: etcd-with-grpc
spec:
  containers:
  - name: etcd
    image: registry.k8s.io/etcd:3.5.1-0
    command: [ "/usr/local/bin/etcd", "--data-dir",  "/var/lib/etcd", "--listen-client-urls", "http://0.0.0.0:2379", "--advertise-client-urls", "http://127.0.0.1:2379", "--log-level", "debug"]
    ports:
    - containerPort: 2379
    livenessProbe:
      grpc:
        port: 2379
      initialDelaySeconds: 10
```

# 1. Liveness Probe

A **liveness probe** determines whether a container is **still alive**.

If the liveness probe fails repeatedly, Kubernetes assumes the container is stuck or broken and **restarts it**.

Common example:  
An application may enter a **deadlock** or infinite loop. The process is still running, but it cannot make progress.

# 2. Readiness Probe

A **readiness probe** determines whether a container is **ready to accept traffic**.

If the readiness probe fails:
- The container **is not restarted**
- It is simply **removed from service load balancing**

This allows an application to remain running while **temporarily unavailable**.

# 3. Startup Probe

A **startup probe** handles applications that **take a long time to boot**.
Without this probe, the liveness probe might restart the container before it finishes starting.

Examples:

```yaml
ports:
- name: liveness-port
  containerPort: 8080

livenessProbe:
  httpGet:
    path: /healthz
    port: liveness-port
  failureThreshold: 1
  periodSeconds: 10
  
readinessProbe:  
  httpGet:  
	path: /ready  
	port: liveness-port  
  periodSeconds: 5

startupProbe:
  httpGet:
    path: /healthz
    port: liveness-port
  failureThreshold: 30
  periodSeconds: 10
```


### Probe request types

> [!NOTE]
> All of the following request types exist and valid for all 3 probing types

#### Using gRPC probes 

If your application implements the [gRPC Health Checking Protocol](https://github.com/grpc/grpc/blob/master/doc/health-checking.md), use can tell a probe to query using gRPC

```yaml
    livenessProbe:
      grpc:
        port: 2379
      initialDelaySeconds: 10
```

#### Using HTTP GET probes 

Create an HTTP GET request to query your application

```yaml
    livenessProbe:
      httpGet:
        path: /healthz
        port: 8080
        httpHeaders:
        - name: Custom-Header
          value: Awesome
      initialDelaySeconds: 3
      periodSeconds: 3
```

#### Using TCP probes 

This type of probe uses a TCP socket. The kubelet will attempt to open a socket to your container on the specified port. If it can establish a connection, the container is considered healthy, otherwise it not not.

```yaml
    livenessProbe:
      tcpSocket:
        port: 8080
      initialDelaySeconds: 15
      periodSeconds: 10
```

#### Using exec probes

You can run command to check liveness, this [[cat|command]] will print the contents of a file to stdout and exit with a status code.

```yaml
    livenessProbe:
      exec:
        command:
        - cat
        - /tmp/healthy
      initialDelaySeconds: 5
      periodSeconds: 5
```

Note: The file at `/tmp/healthy` is automatically being created by kubernetes when the container is being started, this file will be created after the container OS was set up, and will be removed after 30 seconds.
Checking the existence of this file will return an exist code that will pass the liveness test.