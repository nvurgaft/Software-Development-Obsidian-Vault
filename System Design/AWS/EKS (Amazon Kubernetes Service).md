Amazon Elastic Kubernetes Service (Amazon EKS) is a fully managed AWS service that simplifies containerized applications’ deployment, scaling, and operation. 

It automates Kubernetes management tasks, ensuring high availability and security without requiring users to manage the underlying infrastructure.

It is comparable to [[ECS (Amazon Container Service)]], with the key difference EKS utilized Kubernetes for deployment tasks.

Amazon EKS follows the standard Kubernetes architecture with:

- **Control Plane –** Managed by AWS, responsible for scheduling workloads, maintaining cluster state, and handling API requests. It runs across multiple availability zones to ensure high availability.

- **Worker Nodes –** EC2 instances or AWS Fargate containers that run application workloads. These nodes communicate with the control plane to execute Kubernetes commands.