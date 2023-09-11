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
