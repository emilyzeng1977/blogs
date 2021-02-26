## Others
http://www.mydlq.club/article/78/
https://www.zze.xyz/archives/linux-update-kernel.html

https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/


### 02 Task
#### cordon
https://kubernetes.io/zh/docs/concepts/architecture/nodes/
- 将一个节点标识为不可调度 (STATUS from Ready -> SchedulingDisabled)
- 用uncordon恢复


```markdown
kubectl cordon node's name
```
#### drain
https://kubernetes.io/zh/docs/tasks/administer-cluster/safely-drain-node/
- 将一个节点标识为不可调度 (STATUS from Ready -> SchedulingDisabled) // 和cordon功能相同
- 用uncordon恢复 // 和cordon功能相同
- 从一个节点安全逐出所有的Pods(即运行安全的终止该节点中的所有Pod)
- 通常用于在对节点执行维护之前执行

```markdown
kubectl drain --help
              --ignore-daemonsets=false: Ignore DaemonSet-managed pods.
kubectl drain node's name --ignore-daemonsets --force
```
## 08 Task
Scale the deployment nginx-deployment to 10 pods  
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/ 
测试环境的准备工作 
```markdown
kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml
```
方法1 
```markdown
kubectl get deployment nginx-deployment -o yaml > nginx-deployment.yaml
vi change replicas to 10
kubectl apply -f nginx-deployment.yaml
```
方法2  
```markdown
kubectl edit deployment nginx-deployment
change replicas to 10 and then save
```
方法3 (推荐)  
```markdown
kubectl scale deployment.v1.apps/nginx-deployment --replicas=10
or
kubectl scale deployment nginx-deployment --replicas=10
```
