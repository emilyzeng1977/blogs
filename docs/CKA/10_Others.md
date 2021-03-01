## Others
http://www.mydlq.club/article/78/
https://www.zze.xyz/archives/linux-update-kernel.html

https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/

### 01 clusterRole
https://kubernetes.io/docs/reference/access-authn-authz/rbac/  

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
## 09 Task
https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/  
```markdown
Find a template from the above link and change the related fields
```
## 10 Tast
```markdown
[root@master3 vagrant]# kubectl get nodes | grep -i ready | wc -l
2
[root@master3 vagrant]# kubectl get nodes | grep -i NotReady | wc -l
1
echo 1 > 制定文件
```
## 12 Persistent volume
https://kubernetes.io/zh/docs/tasks/configure-pod-container/configure-persistent-volume-storage/  
请先学习这个例子

## 13 Persistent volume Claim
https://kubernetes.io/zh/docs/tasks/configure-pod-container/configure-persistent-volume-storage/  
