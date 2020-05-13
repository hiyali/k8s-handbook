# k8s-101
> Quick deep dive in kubernetes.

## K8s objects

| Name | Shortname | Explain |
| --- | --- | --- |
| Pod | po | The smallest and simplest unit in the Kubernetes object model that you create or deploy. |
| Nodes | no | A node may be a virtual or physical machine, depending on the cluster. |
| ReplicaSet | rs | Maintain a stable set of replica Pods running at any given time. |
| ReplicationController | rc | may deprecated |
| Service | svc | An abstract way to expose an application running on a set of Pods as a network service. |
| Job | job | Creates one or more Pods and ensures that a specified number of them successfully terminate. |
| Ingress | ing | Ingress may provide load balancing, SSL termination and name-based virtual hosting. |
| Deployment | deploy | Provides declarative updates for Pods and ReplicaSets. |
