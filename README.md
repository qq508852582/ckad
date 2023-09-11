# CKAD

### Q1
- kubectl config use-context k8s
- 创建一个名为 ppi 并执行一个运行以下单一容器的 Pod 的 CronJob：

   ```yaml
      - name: pi
        image: perl:5
        command: ["perl", "-Mbignum=bpi", "-wle", "print bpi(2000)"]
    ```

    配置 CronJob 为：
    - 每隔 5 分钟执行一次
    - 保留 2 个已完成的 Job
    - 保留 4 个失败的 Job
    - 永不重启 Pod
    - 在 8 秒后终止 Pod
- 为测试目的，从 CronJob ppi 中手动创建并执行一个名为 ppi-test 的 Job. (Job的完成或是爱并不不重要)

### Q2
- kubectl config use-context k8s
- 您需要创建一个将在预定时间运行的 Pod。
- 在清单文件 /ckad/CKAD00016/periodic.yaml 中定义此 Pod
- 在一个 busybox:stable 容器中运行命令 date ，该命令必须每分钟运行一次，并且必须在 10 秒内完成运行，或者被 Kubernetes 终止运行。
 注意：CronJob 名称和容器名称都必须为 hello
- 在上述清单文件中创建此资源，并验证此 Job 至少成功执行一次。

### Q3
- 一个 Dockerfile 已经存在于 /ckad/DF/Dockerfile
- 使用已存在的 Dockerfile，构建一个名为 centos 和标签为 8.2 的容器镜像。
您可以安装和使用您选择的工具。
- 使用您选择的工具，以 OCI 格式导出构建的容器镜像，并将其存储在 /ckad/DF/centos-8.2.tar

### Q4
- kubectl config use-context k8s
- 您需要创建一个请求一定量的 CPU 和内存的 Pod。
- 在现有的 namespace pod-resources 中创建一个名为 nginx-resources 的 Pod。用 nginx:1.16 的镜像来指定一个容器.
  为其容器指定 40m 的 CPU 和 50Mi 的内存的资源请求.

### Q5
- kubectl config use-context k8s
- haddock namespace 中名为 nosql 的 Deployment 的 Pod 因其容器已用完资源而无法启动。
- 请更新 nosql Deployment，使 Pod：
    - 为其容器请求 15Mi 的内存
    - 将内存限制为 haddock namespace 设置的最大内存容量的一半。
- 您可以在 /ckad/chief-cardinal/nosql.yaml 找到 nosql Deployment 的配置清单。

### Q6
- kubectl config use-context k8s
- 您需要在运行最新版本 Kubernetes 的 cluster 上部署一个为旧版本 Kubernetes 开发的应用程序。
- 修复清单文件 /ckad/credible-mite/www.yaml 中的任何 API 弃用问题，以便可以将应用程序部署在 k8s cluster 上。
    - 该应用程序是为 Kubernetes v1.15 开发的。
    - k8s cluster 运行着 Kubernetes v1.26
- 请在 garfish namespace 中部署更新后的清单文件/ckad/credible-mite/www.yaml 中指定的应用程序。

### Q7
- kubectl config use-context k8s
- 为了测试新的应用程序发布，您需要准备一个金丝雀部署。
- namespace goshawk 中名为 chipmunk-service 的 Service 指向名为 current-chipmunk-deployment 的 Deployment 创建的 5 个 Pod。
- 你可以在/ckad/goshawk/中找到 current-chipmunk-deployment 的清单文件。
- 在同一 namespace 中创建一个相同的 Deployment，名为 canary-chipmunk-deployment
- 修改 Deployment，以便：
    - 在 namespace goshawk 中运行的 Pod 的最大数量为 10 个
    - chipmunk.service 流量的 40%流向 Pod canary-chipmunk-deployment

### Q8
- kubectl config use-context k8s
- 修改运行在 namespace quetzal 名为 broker-deployment 的现有 Deployment，使其容器
     - 以用户 30000 运行
     - 禁止特权提升。
- 您可以在/ckad/daring-moccasin/broker-deployment.yaml 找到 broker-deployment 的清单文件。

### Q9 
- kubectl config use-context k8s
- 您需要新建一个用于运行 NGINX 的 Deployment。
- 在现有的 namespace ckad00014 中创建一个运行 6 个 Pod 副本，名为 api 的 Deployment。用 nginx:1.16 的镜像来指定一个容器。
- 将名为 NGINX_PORT 且值为 8000 的环境变量添加到容器中，然后公开端口 80

### Q10
- kubectl config use-context k8s
- 在名为 honeybee-deployment 的 Deployment 和 namespace gorilla 中的一个 Pod 正在记录错误.
- 查看日志以识别错误消息。
- 找出错误，包括 ```User “system:serviceaccount:gorilla:default ”cannot list resource “serviceaccounts” […] in the namespace “gorilla”```
- 更新 Deployment honeybee-deployment 以解决 Pod 日志中的错误。
- 您可以在/ckad/prompt-escargot/honeybee-deployment.yaml 中找到 honeybee-deployment 的清单文件

### Q11
- kubectl config use-context k8s
- 您需要创建一个 Configmap，并在一个 Pod 中使用此 Config Map。
- 在 namespace default 中创建一个名为 some-config 并存储着以下键/值对的 Configmap：```key3: value4```
- 在 namespace default 中创建一个名为 nginx-configmap 的 Pod。用 nginx:stable 的镜像来指定一个容器。
- 用存储在 Configmap some-config 中的数据来填充卷，并将其安装在路径/some/path

### Q12
- kubectl config use-context k8s
- 您需要创建一个 Secret，并在一个 Pod 中使用此 Secret。
- 在 namespace default 中创建一个名为 another-secret 并包含以下单个键/值对的 Secret：```key1: value2```
- 在 namespace default 中创建一个名为 nginx-secret 的 Pod。用 nginx:1.16 的镜像来指定一个容器。
- 添加一个名为 COOL_VARIABLE 的环境变量来使用 secret 键 key1 的值。

### Q13
- kubectl config use-context k8s
- 由于 Liveness Probe 发生了问题，您无法访问一个应用程序。该应用程序可能在任何 namespace 中运行。
- 找出对应的 Pod 并将其名称和 namespace 写入文件 /ckad/CKAD00011/broken.txt 。使用以下格式: ```<namespaceName>/<podName>```
  文件/ckad/CKAD00011/broken.txt 已存在
- 用 kubectl get events 来获取相关错误事件井将其写入文件 /ckad/CKAD00011/error.txt 。请使用输出格式 wide 。
- 文件/ckad/CKAD00011/error.txt 已存在。
- 修复故障的 Pod 的 Liveness Probe 问题。


### Q14
- kubectl config use-context k8s
- 在 default namespace 中，名为 probe-http 的 deployment 在端口 80 上运行着 Web 应用程序。
- 修改 Deployment：
- 指定 readiness probe 路径为 /healthz/return200
- 将 initialDelaySeconds 设置为 15，即在执行第一次探测前应该等待 15 秒
- 将 periodSeconds 设置为 20，即执行探测的时间间隔为 20 秒

### Q15
- kubectl config use-context k8s
- 您需要更新一个应用程序，然后执行该更新的回滚。
- 更新 namespace ckad00015 中的 Deployment webapp 的比例缩放配置，将 maxSurge 设置为 10%，将 maxUnavailable 设置为 4。
- 更新 Deployment webapp 以让容器镜像 lfccncf/nginx 使用版本标签 1.13.7。
- 将 Deployment webapp 回滚至前一版本。

### Q16
- kubectl config use-context k8s
- 您的应用程序需要使用特定的 ServiceAccount
- 更新在 namespace frontend 中的 Deployment，使其使用现有的 ServiceAccount app

### Q17
- kubectl config use-context k8s
- 您需要扩展一个现有的应用程序，并将其公开在基础设施内。
- 首先，更新在 namespace ckad00017 中的 Deployment ckad00017-deployment ：
     - 以使其运行 5 个 Pod 的副本
     - 将以下标签添加到 Pod ```tier: dmz```
- 然后，在 namespace ckad00017 中创建一个名为 rover 的 NodePort Service 以在 TCP 端口 81 上公开 Deployment ckad00017-deployment

### Q18
-  kubectl config use-context nk8s
-  更新在 namespace ckad00018 中的 Pod ckad00018-newpod ，
-  使其使用一个只允许 此 Pod 与 Pod front 和 db 之间收发流量的 Networkpolicy。
-  所有必要的NetworkPolicy 均已被创建.
-  在完成此项目时,请勿创建、修改或删除任何Networkpolicy,您只能使用现有的Networkpolicy.

### Q19
- kubectl config use-context k8s
- 在 namespace ingress-ckad 下，有 deployment service ingress 三个资源已经部署好了，但是他们的配置有问题，导致的 ingress 网络不通。
- 3个资源的配置清单在目录/ckad/CKAD202206 中，请将其修改为正确的，并重新创建。
- 请注意，这道题的 deployment 是正确的，请不要修改 deployment。

### Q20
-  kubectl config use-context nk8s
- 在 namespace ingress-kk 下有一个 ingress ，但是它貌似不能被正常访问，请排除出原因，并修复。
- 请注意，这道题的 deployment 是正确的，请不要修改 deployment。
