A Deployment manages a set of Pods to run an application workload, usually one that doesn't maintain state.

If [[Pod|Pods]] are the basic units in Kubernetes, a deployment is an abstraction layer over Pods. 

Key features

1. A deployment can schedule multiple pods, a pod cannot scale itself.
2. A deployment represents a single purpose with a group of Pods.
3. To access a deployment with 1 or more pods, you need a Kubernetes service endpoint mapped to the deployment using labels and selectors.

Use cases

1. Create a deployment to rollout a [[ReplicaSet]]
2. Declare the new state of the Pods
3. Rollback to an earlier deployment revision
4. Scale up deployments to handle more load
5. Pause the rollout of a deployment
6. Clean up old ReplicaSets you no longer need

### Example

```YAML
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```