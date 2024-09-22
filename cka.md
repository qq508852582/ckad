
### Q1
设置配置环境：
``` [candidate@node-1] $ kubectl config use-context k8s ```

- Context

为部署流水线创建一个新的 ClusterRole 并将其绑定到范围为特定的 namespace 的特定 ServiceAccount。
#### Task
- 创建一个名为 deployment-clusterrole 且仅允许创建以下资源类型的新 ClusterRole：
  - Deployment
  - StatefulSet
  - DaemonSet
- 在现有的 namespace app-team1 中创建一个名为 cicd-token 的新 ServiceAccount。
- 限于 namespace app-team1 中，将新的 ClusterRole deployment-clusterrole 绑定到新的 ServiceAccount cicd-token。
