# k8s-101
> A quick look at Kubernetes

## K8s objects

| Name | Shortname | Scope | Concept Category | Explain |
| --- | --- | --- | --- | --- |
| Node | `no` | physical cluster | | A node may be a virtual or physical machine, depending on the cluster. |
| PersistentVolume | `pv` | physical cluster | | - |
| Namespace | `ns` | cluster |  | A namespace virtual clusters that backed by the same physical cluster |
| PersistentVolumeClaim | `pvc` | cluster | | - |
| StorageClass | `sc` | cluster | | - |
| Pod | `po` | ns | | The smallest and simplest unit in the Kubernetes object model that you create or deploy. |
| ReplicaSet | `rs` | ns | | Maintain a stable set of replica Pods running at any given time. |
| ReplicationController | `rc` | ns | | may deprecated |
| Service | `svc` | ns | | An abstract way to expose an application running on a set of Pods as a network service. |
| Job | `job` | ns | | Creates one or more Pods and ensures that a specified number of them successfully terminate. |
| Ingress | `ing` | ns | | Ingress may provide load balancing, SSL termination and name-based virtual hosting. |
| Deployment | `deploy` | ns | | Provides declarative updates for Pods and ReplicaSets. |
| DaemonSet | `ds` | ns | | |
| ServiceAccount | `sa` | ns | Security | |
| Role | | ns | Security | |
| RoleBinding | | ns | Security | |
| ClusterRole | | cluster | Security | |
| ClusterRoleBinding | | cluster | Security | |
